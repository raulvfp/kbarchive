---
layout: page
title: "Q174289: FIX: Memory Leak Occurs After Form is Unloaded"
permalink: /kb/174/Q174289/
---

## Q174289: FIX: Memory Leak Occurs After Form is Unloaded

{% raw %}

	Article: Q174289
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0 5.0
	Operating System(s): 
	Keyword(s): kbVBp400 kbVBp500 kbGrpDSVB kb32bitOnly
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A memory leak occurs in a Visual Basic project that has forms that are loaded
	and unloaded several times.
	
	CAUSE
	=====
	
	The small icon of a form remains in memory after the form is unloaded, which
	results in a memory leak.
	
	RESOLUTION
	==========
	
	To work around this bug in Visual Basic 4.0, use the DestroyIcon function during
	the Form_Unload event to remove the small icon from memory. Copy the following
	code sample to the code window of each form in your project:
	
	     Private Declare Function SendMessage Lib "user32" _
	        Alias "SendMessageA" _
	        (ByVal hwnd As Long, _
	         ByVal wMsg As Long, _
	         ByVal wParam As Long, _
	         lParam As Long) As Long
	
	     Private Declare Function DestroyIcon Lib "user32" _
	        (ByVal hIcon As Long) As Long
	
	     Private Const WM_SETICON = &H80
	     Private Const MiniIcon = 0
	     Private Const NullIcon = 0
	
	     Private Sub Form_Unload(Cancel As Integer)
	        Dim hIcon As Long
	        hIcon = SendMessage(hwnd, WM_SETICON, MiniIcon, ByVal _
	        NullIcon)
	        If hIcon <> 0 Then
	           DestroyIcon hIcon
	        End If
	     End Sub
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been fixed in Visual Basic Version 5.0.
	
	MORE INFORMATION
	================
	
	Programs that load and unload forms frequently can cause a significant leak in
	memory because the operating system will lose 1148 bytes every time a form is
	unloaded. The workaround is to destroy the icon when the form is unloaded.
	
	Use the SendMessage function with the WM_SETICON message to get the handle of
	either the large or small icon and to then replace it with the icon specified by
	the NullIcon parameter; in this case replacing it with Null. With the MiniIcon
	parameter set to zero, the message applies to the small icon.
	
	The return value is the handle to the old icon which is removed from memory by
	the DestroyIcon function.
	
	Steps to Reproduce the Behavior
	-------------------------------
	
	1. Start a new project. Form1 is created by default.
	
	2. Add another Form to the project.
	
	3. Add the following code to the Click event of Form1:
	
	        Dim i as Integer
	        For i = 1 To 1000
	           Form2.Show
	           Form2.Hide
	        Next i
	
	4. Press the F5 key to run the project. You will notice a performance drop where
	  Form2 loads more slowly as the iterations progress. Press the CTRL+BREAK keys
	  to end the application.
	
	======================================================================
	Keywords          : kbVBp400 kbVBp500 kbGrpDSVB kb32bitOnly 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500Search kbVBA500 kbVB500 kbVB400Search kbVB400 kbZNotKeyword3
	Version           : WINDOWS:4.0 5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
