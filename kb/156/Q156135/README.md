---
layout: page
title: "Q156135: FIX: CRecordset::m_lCurrentRecord Gives Inaccurate Values"
permalink: /kb/156/Q156135/
---

## Q156135: FIX: CRecordset::m_lCurrentRecord Gives Inaccurate Values

{% raw %}

	Article: Q156135
	Product(s): Microsoft C Compiler
	Version(s): winnt:
	Operating System(s): 
	Keyword(s): kbDatabase kbMFC kbODBC kbVC kbVC500fix
	Last Modified: 30-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), included with:
	   - *EDITOR Please do not choose this product*Microsoft Visual C++ 32-bit Edition* use 241, 265, 225, versions 4.2, 4.2b 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	CRecordset::m_lCurrentRecord does not correctly decrement when
	CRecordset::MovePrev() is invoked.
	
	CAUSE
	=====
	
	CRecordset::m_lCurrentRecord tracks the absolute position of a record within a
	recordset. It is modified using a value passed to the CRecordset::Move() method.
	The CRecordset::MovePrev() method incorrectly increments the value of
	m_lCurrentRecord instead of decrementing it.
	
	The source for CRecordset::MovePrev(), from Afxdb.inl, line 83-84 is shown
	below:
	
	     _AFXDBCORE_INLINE void CRecordset::MovePrev()
	        { ASSERT(IsOpen()); Move(1, SQL_FETCH_PRIOR); }
	
	The value should be as follows:
	
	     _AFXDBCORE_INLINE void CRecordset::MovePrev()
	        { ASSERT(IsOpen()); Move(-1, SQL_FETCH_PRIOR); }
	
	However, since CRecordset::MovePrev() is not virtual, it is not possible to
	correctly override this method.
	
	WORKAROUND
	==========
	
	The solution is to override the CRecordset::SetRowsetCurrencyStatus() so that it
	properly decrements the m_lCurrentRecord member for a MovePrev() call. This is
	done in the switch statement for wFetchType == SQL_FETCH_PRIOR as shown in the
	sample code below.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been fixed in Visual C++ version 5.0.
	
	MORE INFORMATION
	================
	
	The use of CRecordsetStatus should be restricted to information display, and
	should not be relied on in a robust environment. m_lCurrentRecord is not
	relational, and is not be accurate in a multi-user environment. A better
	approach is to use bookmarks, which are more persistent. See the following
	methods:
	
	     CRecordset::SetBookmark()
	
	     CRecordset::GetBookmark()
	
	Use of some methods may cause the bookmark to be invalidated. To determine when a
	bookmark is persistent and when it is not, see the following method:
	
	    CRecordset::GetBookmarkPersistence()
	
	The workaround presented below, however, ensures that
	CRecordset::m_lCurrentRecord is as accurate as possible.
	
	Sample Code
	-----------
	
	
	     extern void AFXAPI AfxSetCurrentRecord(long* plCurrentRecord,
	                                              long nRows, RETCODE nRetCode);
	
	     extern void AFXAPI AfxSetRecordCount(long* plRecordCount,
	          long lCurrentRecord, long nRows, BOOL bEOFSeen, RETCODE nRetCode);
	
	      void CMyRecSet::SetRowsetCurrencyStatus(RETCODE nRetCode,
	                           UWORD wFetchType, long nRows, DWORD dwRowsFetched)
	      {
	          // dwRowsFetched is not used, avoid warning with dummy call
	          dwRowsFetched = 0;
	
	          int nDirection;
	
	          // Set the fetch direction
	          switch (wFetchType)
	          {
	          case SQL_FETCH_FIRST:
	              nDirection = 1;
	              if (nRetCode == SQL_NO_DATA_FOUND)
	              {
	                  m_lCurrentRecord = AFX_CURRENT_RECORD_UNDEFINED;
	                  m_lRecordCount = 0;
	              }
	              else
	                  m_lCurrentRecord = 0;
	              break;
	
	          case SQL_FETCH_NEXT:
	              nDirection = 1;
	              AfxSetCurrentRecord(&m_lCurrentRecord, nRows, nRetCode);
	              AfxSetRecordCount(&m_lRecordCount, m_lCurrentRecord, 1,
	                  m_bEOFSeen, nRetCode);
	
	              // This is the only way to know you've hit the end (m_bEOFSeen)
	              if (!m_bEOFSeen && nRetCode == SQL_NO_DATA_FOUND
	               && m_lRecordCount == m_lCurrentRecord + 1)
	                  m_bEOFSeen = TRUE;
	              break;
	
	          case SQL_FETCH_LAST:
	              nDirection = -1;
	              if (nRetCode == SQL_NO_DATA_FOUND)
	              {
	                  m_lCurrentRecord = AFX_CURRENT_RECORD_UNDEFINED;
	                  m_lRecordCount = 0;
	              }
	              else if (m_bEOFSeen)
	                  m_lCurrentRecord = m_lRecordCount - 1;
	              else
	                  m_lCurrentRecord = AFX_CURRENT_RECORD_UNDEFINED;
	              break;
	
	          case SQL_FETCH_PRIOR:
	              nDirection = -1;
	              AfxSetCurrentRecord(&m_lCurrentRecord, -1, nRetCode);
	              break;
	
	          case SQL_FETCH_RELATIVE:
	              nDirection = nRows;
	              AfxSetCurrentRecord(&m_lCurrentRecord, nRows, nRetCode);
	              AfxSetRecordCount(&m_lRecordCount, m_lCurrentRecord, 1,
	                  m_bEOFSeen, nRetCode);
	              break;
	
	          case SQL_FETCH_ABSOLUTE:
	              nDirection = nRows;
	              if (nRetCode != SQL_NO_DATA_FOUND)
	              {
	                  if (nRows > 0)
	                      m_lCurrentRecord = nRows - 1;
	                  else if (m_bEOFSeen)
	                      m_lCurrentRecord = m_lRecordCount + nRows;
	                  else
	                      m_lCurrentRecord = AFX_CURRENT_RECORD_UNDEFINED;
	              }
	              else
	                  m_lCurrentRecord = AFX_CURRENT_RECORD_UNDEFINED;
	
	              AfxSetRecordCount(&m_lRecordCount, m_lCurrentRecord, 1,
	                  m_bEOFSeen, nRetCode);
	              break;
	
	          case SQL_FETCH_BOOKMARK:
	              nDirection = 0;
	              m_lCurrentRecord = AFX_CURRENT_RECORD_UNDEFINED;
	              break;
	          }
	
	          // Set the BOF/EOF flags
	          if (nRetCode == SQL_NO_DATA_FOUND)
	          {
	              if (wFetchType == SQL_FETCH_FIRST
	               || wFetchType == SQL_FETCH_LAST
	               || wFetchType == SQL_FETCH_BOOKMARK)
	              {
	                  // If MoveFirst/MoveLast fails, result set is empty
	                  // If SetBookmark fails, currency undefined
	                  m_bEOF = m_bBOF = TRUE;
	              }
	              else
	              {
	                  m_bEOF = nDirection >= 0 ? TRUE : FALSE;
	                  m_bBOF = !m_bEOF;
	              }
	          }
	          else
	          {
	              m_bEOF = m_bBOF = FALSE;
	          }
	      }
	
	Additional query words: kbVC420bug
	
	======================================================================
	Keywords          : kbDatabase kbMFC kbODBC kbVC kbVC500fix 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
