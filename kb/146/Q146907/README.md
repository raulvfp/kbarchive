---
layout: page
title: "Q146907: HOWTO: Create a Screen Saver in Visual Basic"
permalink: /kb/146/Q146907/
---

## Q146907: HOWTO: Create a Screen Saver in Visual Basic

{% raw %}

	Article: Q146907
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0
	Operating System(s): 
	Keyword(s): kbsetup kb16bitonly kbVBp400 kbGrpDSVB kbDSupport
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	You can create a Windows screen saver with Visual Basic by following the
	guidelines listed below. However, please note that this article gives only a
	very rough outline of what you should do for a robust screen saver. These are
	general guidelines only.
	
	
	MORE INFORMATION
	================
	
	Follow these guidelines when creating a Windows screen saver with Visual Basic:
	
	- In the File Make EXE File dialog, insert the string SCRNSAVE: (in upper case)
	  at the beginning of the Application Title. For example:
	
	  SCRNSAVE:Flying Fish.
	
	- In the File Make EXE File dialog, specify the program file name extension as
	  .SCR instead of .EXE.
	
	- Locate the .SCR program file in the \WINDOWS directory.
	
	- Give your form the following property settings so that it occupies the entire
	  screen and does not have a title bar:
	
	     Caption     = ""     (no caption)
	     ControlBox  = False
	     MaxButton   = False
	     MinButton   = False
	     WindowState = 2      (maximized)
	
	- Add code to all MouseMove, MouseDown, and KeyDown event handlers that exit
	  the program. Because Visual Basic may invoke the MouseMove event when the
	  form is first loaded, you must write code to ignore the first MouseMove
	  event. The following MouseMove code avoids an artifact event that occurs when
	  the application is first activated or when the application is running and
	  another instance starts (causing loss of focus) and then quits (restoring
	  focus):
	
	        Private Sub Form_MouseMove (Button As Integer, Shift As Integer, _
	           X As Single, Y As Single)
	           Static count As Integer
	           If count > 2 Then
	              End
	           Else
	              count = count + 1
	           End If
	        End Sub
	
	  This gives you a bit of slack when it comes to artifact MouseMove events. You
	  will want to do something similar with the MouseDown and KeyDown events.
	
	Preventing Multiple Launches
	----------------------------
	
	Windows usually launches the screen saver program multiple times. To prevent more
	than one copy of your screen saver from running, add the following statements to
	the Form_Load event handler, or Sub Main if used:
	
	     Private Sub Form_Load ()
	        If App.PrevInstance Then
	           End
	        End If
	     End Sub
	
	There is no reason to attempt to restore the previous instance of the screen
	saver as the active window because it will become the active window when the new
	instance ends. All you have to do is terminate when you see another instance
	running.
	
	
	To prevent multiple instances of the application from running as well as to keep
	the application running, you should move the code from the Form_Load() to a Sub
	Main(). Then set the project's Startup Form Option to Sub Main(). Setting the
	project to begin processing at Sub Main is done on the Project tab which is part
	of Options... under Tools menu. For example:
	
	     Public Sub Main ()
	        If App.PrevInstance Then   ' If already running, end the application.
	           End
	        Else
	           Form1.Show 1             ' Show the screen saver form.
	        End If
	     End Sub
	
	Launching the Screen Saver
	--------------------------
	
	Windows takes care of launching the Screen Saver. It keeps track of system idle
	time and launches the screen saver program. You can use a timer control to
	periodically draw graphics on the form.
	
	Screen savers are selected and configured from Windows Control Panel in the
	Desktop dialog. The screen saver section of this dialog has a button labeled
	Setup that invokes the screen saver program with the command line option /c.
	When your program is invoked with this option, you can display a configuration
	form to allow the user to select settings such as speed, number of objects,
	colors, and so on. Detect the /c command line parameter by checking the Command$
	function. For example:
	
	     Private Sub Form_Load ()
	        If Command$ = "/c" Then
	           frmConfig.Show   ' Display configuration form.
	           Unload Me        ' Bypass regular form.
	        End If
	     End Sub
	
	When Windows launches the screen saver, it usually specifies the command line
	option /s.
	
	Possible Improvements
	---------------------
	
	You may also want your program to appear on top of all other windows by making it
	a TOPMOST window.
	
	For additional information, please see the following article(s) in the Microsoft
	Knowledge Base:
	
	  Q84251 How to Create a Topmost or Floating Window in Visual Basic
	
	Also, you can find two example programs and a complete explanation showing how to
	write your own screen savers in Visual Basic in the following book:
	
	  "Visual Basic Workshop 3.0" by John C. Craig, published by Microsoft Press.
	
	This article is a rough outline of what you should do for a robust screen saver.
	For example, you might want to have the startup be a Sub Main() in which you
	check for a previous instance and End if there is one. This would avoid the form
	load totally if there were already an instance running. It might also avoid the
	artifact MouseMove problem.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsetup kb16bitonly kbVBp400 kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB400Search kbVB400
	Version           : WINDOWS:4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
