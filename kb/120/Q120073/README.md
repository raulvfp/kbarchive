---
layout: page
title: "Q120073: How to Rotate a Pen Windows Application"
permalink: /kb/120/Q120073/
---

## Q120073: How to Rotate a Pen Windows Application

{% raw %}

	Article: Q120073
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Some Pen Windows operating systems allow the rotation of the screen from O to
	270 degrees to allow for greater comfort for the user's hand. Unfortunately,
	there is no straightforward way to use this capability from within a Visual
	Basic program.
	
	However, if you change some settings in the SYSTEM.INI file, you may be able to
	rotate your application relative to the screen. The SYSTEM.INI file contains the
	information that Pen Windows operating system looks at as it loads the display
	drivers.
	
	NOTE: The Professional Edition of Visual Basic version 3.0 for Windows has the
	Pen Controls, which you can use to create Pen Windows applications. The Pen
	Windows operating system is required to load these controls and use them in your
	applications. Therefore, the sample code shown in the More Information section
	below requires that you have both the Professional Edition of Visual Basic
	version 3.0 for Windows and the Pen Windows operating system, which is available
	through Original Equipment Manufacturers (OEMs).
	
	MORE INFORMATION
	================
	
	Applicable Settings in the SYSTEM.INI File
	------------------------------------------
	
	The following entries in SYSTEM.INI relate to the display orientation and
	rotation:
	
	[boot]
	display.drv=vgap.drv  ' Sets the video driver that supports inking.
	
	[Display Driver]
	DisplayOrientation=n  ' Specifies the tablet orientation. The value
	                     ' of n is the number of times the screen and
	                     ' tablet have been rotated 90 degrees
	                     ' counterclockwise (default is zero).
	
	OrientatableDrivers={list of drivers}
	                     ' Specifies on a single line, the path to the
	                     ' rotatable screen drivers.
	
	OrientatableDrivers=driver1,driver2,driver3,driver4
	                     ' Each driver in the line represents the driver
	                     ' for 0, 90, 180, 270 degrees right, in that
	                     ' order.
	
	Using the API calls GetPrivateProfileString, WritePrivateProfileString and
	ExitWindows, you can change the display orientation by using the sample code
	listed below.
	
	Step-by-Step Instructions for Creating the Program
	--------------------------------------------------
	
	1. Start a new project in Visual Basic. This creates Form1 by default.
	
	2. Copy and paste the sample code (listed below) into a text document by using
	  an editor such as NOTEPAD.EXE.
	
	3. Review the code in the file line by line. As instructed by the comments in
	  the code, change each of the long continued lines of code into one, single
	  line of code.
	
	4. Save the file as a text file with the name PEN.FRM.
	
	5. Start Visual Basic. Choose the Remove File option from the File menu, and
	  remove the default Form1.FRM already in the project.
	
	6. Choose Add File from the File menu, and add the PEN.FRM file to your project.
	
	7. Choose Project from the Options menu, and select Form1 for the Start Up Form
	  in the dialog box.
	
	8. Run the program. Click the various command buttons to get the different
	  rotations written on the buttons.
	
	Sample Code
	-----------
	
	  VERSION 2.00
	  Begin Form Form1
	        Caption         =   "Change Screen Orientation"
	        ClientHeight    =   3315
	        ClientLeft      =   1320
	        ClientTop       =   1830
	        ClientWidth     =   5925
	        Height          =   3780
	        Left            =   1230
	        LinkTopic       =   "Form1"
	        ScaleHeight     =   3315
	        ScaleWidth      =   5925
	        Top             =   1455
	        Width           =   6105
	        Begin ListBox List1
	           Height          =   1395
	           Left            =   240
	           TabIndex        =   5
	           Top             =   600
	           Width           =   2535
	        End
	        Begin CommandButton Command6
	           Caption         =   "270 degrees Orientation"
	           Height          =   375
	           Left            =   3120
	           TabIndex        =   3
	           Top             =   1680
	           Width           =   2295
	        End
	        Begin CommandButton Command5
	           Caption         =   "180 degrees Orientation"
	           Height          =   375
	           Left            =   3120
	           TabIndex        =   2
	           Top             =   1200
	           Width           =   2295
	        End
	        Begin CommandButton Command3
	           Caption         =   "Exit"
	           Height          =   615
	           Left            =   1920
	           TabIndex        =   4
	           Top             =   2400
	           Width           =   1935
	        End
	        Begin CommandButton Command2
	           Caption         =   "90 degrees Orientation"
	           Height          =   375
	           Left            =   3120
	           TabIndex        =   1
	           Top             =   720
	           Width           =   2295
	        End
	        Begin CommandButton Command1
	           Caption         =   "0 degrees Orientation"
	           Height          =   375
	           Left            =   3120
	           TabIndex        =   0
	           Top             =   240
	           Width           =   2295
	        End
	        Begin Label Label1
	           Caption         =   "List of Orientations:"
	           Height          =   255
	           Left            =   240
	           TabIndex        =   6
	           Top             =   360
	           Width           =   1695
	        End
	     End
	
	     ' Declare the API's used:
	     ' Place the following four lines on one, single line:
	     Declare Function GetPrivateProfileString Lib "Kernel" (ByVal
	        lpApplicationName As String, ByVal lpKeyName As Any, ByVal lpDefault
	        As String, ByVal lpReturnedString As String, ByVal nSize As Integer,
	        ByVal lpFileName As String) As Integer
	
	     ' Place the following two lines on one, single line:
	     Declare Function ExitWindows Lib "User" (ByVal dwReturnCode As Long,
	     ByVal wReserved As Integer) As Integer
	
	     ' Place the following three lines on one, single line:
	     Declare Function WritePrivateProfileString Lib "Kernel" (ByVal
	     lpApplicationName As String, ByVal lpKeyName As Any, ByVal lpString
	     As Any, ByVal lplFileName As String) As Integer
	
	     ' Dimension the variables to hold each of the display driver's names:
	     Dim rotation1$
	     Dim rotation2$
	     Dim rotation3$
	     Dim rotation4$
	
	     ' Set the constant to restart Windows:
	     Const EW_RESTARTWINDOWS = &H42
	
	     Sub Command1_Click ()
	        ' This will change the screen orientation to 0 deg.
	
	        ' Check to see whether the driver for the degree mode exists:
	        If Len(rotation1$) = 0 Then
	           ' Place the following two lines on one, single line:
	           MsgBox "This Rotation is Not Supported under current system
	                   configuration.", 16, "Error Rotating Screen"
	           Exit Sub
	        End If
	
	        ' Restore screen to normal:
	        Call Rotate(rotation1$, "0")
	     End Sub
	
	     Sub Command2_Click ()
	        ' This will change the screen orientation to 90 deg.
	
	        ' Check to see whether the driver for the degree mode exists:
	        If Len(rotation2$) = 0 Then
	           ' Place the following two lines on one, single line:
	           MsgBox "This Rotation is Not Supported under current system
	                   configuration.", 16, "Error Rotating Screen"
	           Exit Sub
	        End If
	        ' Rotate the screen.
	        Call Rotate(rotation2$, "1")
	     End Sub
	
	     Sub Command3_Click ()
	         Unload Me
	         End
	     End Sub
	
	     Sub Command5_Click ()
	        ' This will change the screen orientation to 180 deg.
	        ' Check to see whether the driver for the degree mode exists:
	        If Len(rotation3$) = 0 Then
	           ' Place the following two lines on one, single line:
	           MsgBox "This Rotation is Not Supported under current system
	                   configuration.", 16, "Error Rotating Screen"
	           Exit Sub
	        End If
	        ' Rotate the screen:
	        Call Rotate(rotation3$, "2")
	     End Sub
	
	     Sub Command6_Click ()
	        ' This will change the screen orientation to 270 deg.
	        ' Check to see whether the driver for the degree mode exists:
	        If Len(rotation4$) = 0 Then
	           ' Place the following two lines on one, single line:
	           MsgBox "This Rotation is Not Supported under current system
	                   configuration.", 16, "Error Rotating Screen"
	           Exit Sub
	        End If
	        ' Rotate the screen:
	        Call Rotate(rotation4$, "3")
	     End Sub
	
	     Sub Form_Load ()
	        ' Set up the variables for GEtPrivatePrfileString:
	        Dim lpApplicationName As String
	        Dim lpKeyName As String
	        Dim lpszDefault As String
	        Dim lpReturnedString As String
	        Dim nSize As Integer
	        Dim lpFileName As String
	
	        lpReturnedString = Space$(1024)  ' Initialize the buffer to spaces.
	        lpFileName = "System.ini"        ' Set fileName to the SYSTEM.INI.
	        lpApplicationName = "Display Driver"    ' Set the section name to the
	                                                ' Display drivers section.
	        lpKeyName = "OrientableDrivers"   ' Obtain the list of orientable
	                                          ' drivers.
	        nSize = Len(lpReturnedString)     ' Set the size of the return
	                                          ' buffer.
	
	        ' Get the list of orientable drivers:
	        ' Place the following two lines on one, single line:
	        x% = GetPrivateProfileString(lpApplicationName, lpKeyName,
	           lpszDefault, lpReturnedString, nSize, lpFileName)
	        ' Place the following two lines on one, single line:
	        rotation1$ = Mid$(lpReturnedString, 1, InStr(1, lpReturnedString,
	           ",") - 1)
	        ' Place the following two lines on one, single line:
	        rotation2$ = Mid$(lpReturnedString, Len(rotation1$) + 2,
	           Len(lpReturnedString))
	        rotation2$ = Mid$(rotation2$, 1, InStr(1, rotation2$, ",") - 1)
	        ' Place the following two lines on one, single line:
	        rotation3$ = Mid$(lpReturnedString, Len(rotation1$) + Len(rotation2$)
	           + 3, Len(lpReturnedString))
	        rotation3$ = Mid$(rotation3$, 1, InStr(1, rotation3$, ",") - 1)
	        ' Place the following two lines on one, single line:
	        rotation4$ = Mid$(lpReturnedString, Len(rotation1$) + Len(rotation2$)
	           + Len(rotation3$) + 4, Len(lpReturnedString))
	        rotation4$ = Mid$(rotation4$, 1, Len(rotation4$))
	        ' Fill the list box:
	        list1.AddItem "1 - 0 degrees   " & rotation1$
	        list1.AddItem "2 - 90 degrees  " & rotation2$
	        list1.AddItem "3 - 180 degrees " & rotation3$
	        list1.AddItem "4 - 270 degrees " & rotation4$
	     End Sub
	
	     Sub Rotate (RotationDriver$, Orientation$)
	        ' This sub modifies the SYSTEM.INI file to rotate the screen
	        ' orientation.
	        Dim lpApplicationName As String
	        Dim lpKeyName As String
	        Dim lpString As String
	        Dim lpFileName As String
	
	        ' Change the display driver entry in the SYSTEM.INI:
	        lpFileName = "System.ini"
	        lpApplicationName = "boot"
	        lpKeyName = "display.drv"
	        lpString = Trim$(RotationDriver$)
	
	        ' Place the following two lines on one, single line:
	        x% = WritePrivateProfileString(lpApplicationName, lpKeyName,
	           lpString, lpFileName)
	
	        ' Change the Display Orientation entry of the SYSTEM.INI:
	        lpApplicationName = "Display Driver"
	        lpKeyName = "DisplayOrientation"
	        lpString = Orientation$
	
	        ' Place the following two lines on one, single line:
	        x% = WritePrivateProfileString(lpApplicationName, lpKeyName,
	           lpString, lpFileName)
	
	        ' Restart Windows so that the changes will take effect.
	        ' Place the following two lines on one, single line:
	        MsgBox "The system will now restart so that the changes can be made",
	           16, "Change screen Orientation"
	        x% = ExitWindows(EW_RESTARTWINDOWS, 0&)
	     End Sub
	
	REFERENCES
	==========
	
	Pen Windows API section of Microsoft Developer Network (MSDN) CD 7.
	
	Additional query words: 3.00 penwindows
	
	======================================================================
	Keywords          :  
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB300Search kbVB300
	Version           : :3.0
	
	=============================================================================
	

{% endraw %}
