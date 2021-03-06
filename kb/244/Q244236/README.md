---
layout: page
title: "Q244236: HOWTO: Use the System Color on ScrollBars Under Windows NT"
permalink: /kb/244/Q244236/
---

## Q244236: HOWTO: Use the System Color on ScrollBars Under Windows NT

{% raw %}

	Article: Q244236
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbAPI kbColor kbCtrl kbScrollBar kbSDKWin32 kbVBp600 kbWndwMsg kbGrpDSVB kbDSupport
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The background color of the horizontal and vertical scrollbar controls is white
	under Microsoft Windows NT, while the system color is used under Microsoft
	Windows 9.x. To use the system color on Windows NT, it is necessary to subclass
	the form to prevent the WM_CTLCOLORSCROLBAR windows message from being processed
	by the default windows procedure (WindowProc) of the form.
	
	WARNING: Failure to unhook a window before its imminent destruction results in
	application errors, Invalid Page Faults, and data loss. This is due to the fact
	that the new WindowProc function being pointed to no longer exists, but the
	window has not been notified of the change. Always unhook the sub-classed window
	upon unloading the sub-classed form or exiting the application. This is
	especially important while debugging an application that uses this technique
	within the Microsoft Visual Basic Development Environment (IDE). Pressing the
	END button or selecting END from the Run menu without unhooking can cause an
	Invalid Page Fault and close Microsoft Visual Basic.
	
	MORE INFORMATION
	================
	
	Microsoft Windows controls applications by sending messages to the windows that
	are created by each application. These messages alert the targeted window when
	it is time to redraw, when a mouse button is pressed, and all of the other
	information a window needs to know in order to act appropriately.
	
	Thus, a minimal Windows application consists of a function that processes these
	messages (called WindowProc). This function is registered with the system when
	the window is created so the system knows where to send messages.
	
	The WM_CTLCOLORSCROLLBAR message is sent to the parent window of a scrollbar
	control when the control is about to be drawn. By responding to this message,
	the parent window can use the device context handle (hDC) to set the background
	color of the scroll bar control. If this message is intercepted and not passed
	on to the WindowProc, the scrollbar is set to the system color.
	
	The following sample consists of a simple form with two CommandButtons and a
	vertical scrollbar. It intercepts the WM_CTLCOLORSCROLLBAR message and discards
	it.
	
	NOTES:
	
	- The scrollbar control flickers unless at least one other control is sited on
	  the form. Setting the TabStop property of the VScrollBar to False prevents it
	  from getting the focus.
	
	- It is generally a good idea to start a hook from the Form_Load procedure and
	  end it from the Form_Unload procedure. In this sample, CommandButtons are
	  used so that the difference in the VScrollBar is more readily apparent.
	
	Step-by-Step Example
	--------------------
	
	1. Start a new Visual Basic Standard EXE project. Form1 is created by default.
	
	2. Add two CommandButtons and a VScrollBar to Form1. Set the TabStop property of
	  VScrollBar1 to False.
	
	3. On the Project menu, click Add Module to add a BAS Module to the project.
	
	4. Add the following code to the General Declarations section of Module1:
	
	  Option Explicit
	
	  Declare Function CallWindowProc Lib "user32" Alias _
	   "CallWindowProcA" (ByVal lpPrevWndFunc As Long, _
	   ByVal hwnd As Long, ByVal Msg As Long, _
	   ByVal wParam As Long, ByVal lParam As Long) As Long
	
	  Declare Function SetWindowLong Lib "user32" Alias _
	   "SetWindowLongA" (ByVal hwnd As Long, _
	   ByVal nIndex As Long, ByVal dwNewLong As Long) As Long
	
	  Public Const GWL_WNDPROC = -4
	  public Const WM_CTLCOLORSCROLLBAR = 311
	
	  Public Sub Hook()
	     lpPrevWndProc = SetWindowLong(gHW, GWL_WNDPROC, _
	     AddressOf WindowProc)
	  End Sub
	
	  Public Sub Unhook()
	     Dim temp As Long
	     temp = SetWindowLong(gHW, GWL_WNDPROC, lpPrevWndProc)
	  End Sub
	
	  Function WindowProc(ByVal hw As Long, ByVal uMsg As Long, _
	                      ByVal wParam As Long, ByVal lParam As Long) As Long
	     If uMsg <> WM_CTLCOLORSCROLLBAR Then
	        Debug.Print uMsg, hw
	        WindowProc = CallWindowProc(lpPrevWndProc, hw, uMsg, wParam, lParam)
	     End If
	  End Function
	
	5. Add the following code to the General Declarations section of Form1:
	
	  Option Explicit
	
	  Dim lpPrevWndProc As Long
	  Dim gHW As Long
	
	  Private Sub Form_Load()
	     gHW = Me.hwnd
	     Command1.Caption = "Hook"
	     Command2.Caption = "Unhook"
	  End Sub
	
	  Private Sub Command1_Click()
	     Hook
	     VScroll1.Refresh
	  End Sub
	
	  Private Sub Command2_Click()
	     Unhook
	  End Sub
	
	6. Run the project and click the Hook button to hook the form. Observe that the
	  scrollbar changes from white to the system color.
	
	7. Click the Unhook button and then terminate the program.
	
	REFERENCES
	==========
	
	  Q168795 HOWTO: Hook Into a Window's Messages Using AddressOf
	
	Additional query words:
	
	======================================================================
	Keywords          : kbAPI kbColor kbCtrl kbScrollBar kbSDKWin32 kbVBp600 kbWndwMsg kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
