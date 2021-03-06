---
layout: page
title: "Q149407: HOWTO: How to Display a Bitmap in a CStatusBar Pane"
permalink: /kb/149/Q149407/
---

## Q149407: HOWTO: How to Display a Bitmap in a CStatusBar Pane

{% raw %}

	Article: Q149407
	Product(s): Microsoft C Compiler
	Version(s): winnt:1.0,2.0,2.1,2.2,4.0,4.1
	Operating System(s): 
	Keyword(s): kbBitmap kbMFC kbStatBar KbUIDesign kbVC kbGrpDSMFCATL kbMFCCtrlBar
	Last Modified: 30-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++ for Windows, 16-bit edition, versions 1.0, 1.5, 1.51, 1.52 
	   - Microsoft Visual C++, 32-bit Editions, versions 1.0, 2.0, 2.1, 2.2, 4.0, 4.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The standard status bar in an MFC application easily allows the application to
	display its status. Sometimes it is a good idea to display the status using
	bitmaps or other graphic entities. MFC's CStatusBar class directly supports
	displaying text, but not graphics, in its panes. This article shows by example
	how to display a bitmap in a CStatusBar pane.
	
	MORE INFORMATION
	================
	
	It is not very difficult to display a bitmap in a status bar pane. The code at
	the end of this article will let you display a bitmap in pane 1 of the status
	bar. Put the code in a Default AppWizard application, and add a new pane to the
	status bar before the standard panes. Please refer to online documentation for
	CStatusBar for information on how to add a pane to the status bar.
	
	With Visual C++ 4.0 and later, MFC's CStatusBar uses the status window common
	control. In earlier versions, CStatusBar was implemented in MFC. Hence the code
	required for displaying bitmap in a CStatusBar pane is different.
	
	You can add the sample code to an application built with an earlier version of
	Visual C++ (a version previous to 4.0), and then recompile the application using
	Visual C++ 4.0 without modifying the code. If you are using Visual C++ 4.0 or
	later, you need not add code between the
	
	     #if _MFC_VER < 0x400
	     ...
	     #endif
	
	directives.
	
	Step-by-Step Example and Sample Code
	------------------------------------
	
	1. Derive a class from CStatusBar (for example, CMyStatusBar), and use this
	  class instead of CStatusBar in CMainFrame.
	
	2. Add the following member functions to the class definition in the .h file:
	
	     class CMyStatusBar : public CStatusBar
	     {
	     ...
	     #if _MFC_VER < 0x400
	         virtual void DoPaint(CDC* pDC);
	     #endif
	
	     #if _MFC_VER >= 0x400
	         virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
	     #endif
	     ...
	     }
	
	3. Add the following code for the functions in the .cpp file:
	
	     #if _MFC_VER < 0x400
	     void CMyStatusBar::DoPaint(CDC* pDC)
	     {
	         CRect rect;
	         GetItemRect(1, &rect);  // get pane rect
	         pDC->ExcludeClipRect(&rect);  // exclude pane rect from paint
	         CStatusBar::DoPaint(pDC);  // paint remainder of status bar
	
	         CRgn paneRgn;
	         paneRgn.CreateRectRgnIndirect(rect);
	         pDC->SelectClipRgn(&paneRgn); // set clip region to pane rect
	
	         CBitmap* pBitmap = /* pointer to current CBitmap */;
	         CDC srcDC; // select current bitmap into a compatible CDC
	         srcDC.CreateCompatibleDC(NULL);
	         CBitmap* pOldBitmap = srcDC.SelectObject(pBitmap);
	         pDC->BitBlt(rect.left, rect.top, rect.Width(), rect.Height(),
	                   &srcDC, 0, 0, SRCCOPY); // BitBlt to pane rect
	         srcDC.SelectObject(pOldBitmap);
	     }
	     #endif
	
	     #if _MFC_VER >= 0x400
	     void CMyStatusBar::DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct)
	     {
	         switch(lpDrawItemStruct->itemID)
	         {
	         case 1:
	             // Attach to a CDC object
	             CDC dc;
	             dc.Attach(lpDrawItemStruct->hDC);
	
	             // Get the pane rectangle and calculate text coordinates
	             CRect rect(&lpDrawItemStruct->rcItem);
	
	             CBitmap* pBitmap = /* pointer to current CBitmap */;
	             CDC srcDC; // select current bitmap into a compatible CDC
	             srcDC.CreateCompatibleDC(NULL);
	             CBitmap* pOldBitmap = srcDC.SelectObject(pBitmap);
	             dc.BitBlt(rect.left, rect.top, rect.Width(), rect.Height(),
	                       &srcDC, 0, 0, SRCCOPY); // BitBlt to pane rect
	             srcDC.SelectObject(pOldBitmap);
	
	             // Detach from the CDC object, otherwise the hDC will be
	             // destroyed when the CDC object goes out of scope
	             dc.Detach();
	
	             return;
	         }
	
	         CStatusBar::DrawItem(lpDrawItemStruct);
	     }
	     #endif
	
	4. Add the following code to CMainFrame::OnCreate().
	
	     int CMainFrame::OnCreate(LPCREATESTRUCT lpCreateStruct)
	     {
	     ...
	         if (!m_wndStatusBar.Create(this) ||
	             !m_wndStatusBar.SetIndicators(indicators,
	               sizeof(indicators)/sizeof(UINT)))
	
	             TRACE0("Failed to create status bar\n");
	             return -1;      // fail to create
	         }
	
	     // Add the following code
	     #if _MFC_VER >= 0x400
	         UINT nID, nStyle;
	         int cxWidth;
	
	         m_wndStatusBar.GetPaneInfo(1, nID, nStyle, cxWidth);
	         m_wndStatusBar.SetPaneInfo(1, nID, nStyle | SBT_OWNERDRAW,
	             cxWidth);
	     #endif
	     ...
	     }
	
	REFERENCES
	==========
	
	Visual C++ Books Online and the Windows SDK docuemntation.
	
	Additional query words: kbinf 1.00 1.50 1.51 1.52 2.00 2.10 2.20 2.50 2.51 2.52 3.00 3.10 3.20 4.00 4.10
	
	======================================================================
	Keywords          : kbBitmap kbMFC kbStatBar KbUIDesign kbVC kbGrpDSMFCATL kbMFCCtrlBar 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:1.0,2.0,2.1,2.2,4.0,4.1
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
