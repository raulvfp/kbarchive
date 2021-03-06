---
layout: page
title: "Q88557: INFO: CFrameWnd Objects Can Destroy Themselves"
permalink: /kb/088/Q88557/
---

## Q88557: INFO: CFrameWnd Objects Can Destroy Themselves

{% raw %}

	Article: Q88557
	Product(s): Microsoft C Compiler
	Version(s): 7.0
	Operating System(s): 
	Keyword(s): kbDocView kbMFC KbUIDesign kbVC100 kbVC150 kbVC200 kbVC400 kbGrpDSMFCATL kbArchitecture
	Last Modified: 03-MAY-2001
	
	7.00   | 1.00 1.50 1.51 1.52 | 1.00 2.00 2.10 4.00
	MS-DOS | WINDOWS             | WINDOWS NT
	kbprg
	
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft C/C++, version 7.0 
	   - Microsoft Visual C++ for Windows 
	   - Microsoft Visual C++ 32-bit Edition 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Objects derived from the CFrameWnd class destroy themselves automatically when
	the Window that is associated with the object processes the WM_NCDESTROY
	message. Because objects derived from CFrameWnd classes destroy themselves, it
	is recommended that applications use the "new" operator to create new instances
	of this class on the heap.
	
	MORE INFORMATION
	================
	
	Objects derived from CFrameWnd are designed to "clean up" after themselves. The
	CFrameWnd class overloads the OnNcDestroy() member function that makes a call to
	the PostNcDestroy() member function, which in turn does a "delete this."
	
	CMDIFrameWnd and CMDIChildWnd, which are derived from CFrameWnd, exhibit
	identical behavior.
	
	The OnNcDestroy() function is called when the window receives the WM_NCDESTROY
	message. This is the last message a window receives. As a result, CFrameWnd
	objects should be created on the heap using the "new" operator, and should never
	be explicitly deleted by the application. If the application needs to destroy
	the object, it should use the DestroyWindow() member function, which destroys
	both the window and its CFrameWnd object.
	
	In general, CFrameWnd objects should not be used as local variables in functions
	or as embedded objects in other classes. Doing so may cause the object's
	destructor to be called twice: once when the user closes the window, and once
	when the function containing the local variable goes out of scope or when the
	object containing the embedded CFrameWnd object is deleted. Attempting to delete
	the object more than once may cause an unrecoverable application error (UAE).
	
	You can create a CFrameWnd-derived object on the stack or as a static object if
	the application overrides the PostNcDestroy() function for the derived class.
	PostNcDestroy() is a virtual member function of the CWnd class that is called by
	the OnNcDestroy() function. The overridden PostNcDestroy() function for the
	derived class should do nothing, rather than "delete this." This prevents the
	object from being destroyed twice.
	
	Additional query words: kbinf 7.00 1.00 1.50 2.00 2.10 2.50 2.51 2.52 3.00 3.10 4.00
	
	======================================================================
	Keywords          : kbDocView kbMFC KbUIDesign kbVC100 kbVC150 kbVC200 kbVC400 kbGrpDSMFCATL kbArchitecture 
	Technology        : kbAudDeveloper kbMFC
	Version           : :7.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
