---
layout: page
title: "Q129941: PRB:Unexpected Results When Raise Method Propogates OLE Errors"
permalink: /kb/129/Q129941/
---

## Q129941: PRB:Unexpected Results When Raise Method Propogates OLE Errors

{% raw %}

	Article: Q129941
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When creating OLE Servers, you often need to propagate errors specific to the
	OLE Server back to the client application by using the Raise method. The valid
	range of Error numbers is 0 - 65535, including those defined by Visual Basic.
	While there is a constant (vbObjectError) from which all OLE Server errors can
	start, unexpected results can occur when errors are raised between vbObjectError
	and vbObjectError + 512.
	
	CAUSE
	=====
	
	Visual Basic remaps some error messages between vbObjectError and vbObjectError
	+ 512 to standard run-time errors, which can result in unexpected behavior if
	user-defined error numbers are not greater then vbObjectError + 512.
	
	Because some error numbers are re-mapped by Visual Basic to standard OLE
	Automation run-time errors, error trapping code that relies on values between
	vbObjectError and vbObjectError + 512 are never be executed.
	
	RESOLUTION
	==========
	
	Below is sample OLE Server that correctly uses the Raise method to generate a
	user-defined error > vbObjectError + 512.
	
	Step-by-Step Example
	--------------------
	
	1. Start a new project in Visual Basic. Form1 is created by default.
	
	2. Add a command button (Command1) to Form1.
	
	3. Add the following code to the Command1_Click procedure:
	
	     Sub Command1_Click()
	        On Error GoTo errhand
	
	        Dim clsClass1 As New Class1
	        clsClass1.Prop1 = -4        ' Set property to invalid value
	        Exit Sub
	
	     errhand:
	        If Err.Number > vbObjectError Then
	           MsgBox prompt:="User Defined OLE Automation Error (" & _
	           CStr(Err.Number - vbObjectError) & "):" & _
	           Chr$(13) & Chr$(10) & Err.Description, _
	           Buttons:=vbExclamation, Title:=Err.Source
	        Else
	           MsgBox prompt:=Err.Description, Buttons:=vbExclamation
	        End If
	     End Sub
	
	4. Insert a Class Module by choosing Class Module from the Insert Menu (ALT, I,
	  C). Class1 is assigned to the Name property by default.
	
	5. Add the following code to the Class1:
	
	     Property Let Prop1(vntValue)
	        If vntValue < 0 Then
	           ' Note the Error Number is > the vbObjectError + 512
	           Err.Raise Number:=vbObjectError + 1000, Source:="Class1", _
	           Description:="Invalid Property Value (Valid Values are 0 - 65535)"
	           ' Note "Invalid Property Value (Valid Values are 0 - 65535)" is a
	           ' custom error message
	        End If
	     End Property
	
	6. Change the Error Trapping option to Break on Unhandled Errors by choosing
	  Options form the Tools menu and selecting the Advanced Tab.
	
	  This allows the error to be trapped in code, instead of the debuger stopping
	  on the Raise Method within the Property Procedure in Class1.
	
	7. Press the F5 key to run the program.
	
	8. Click the Command1 button. A Message Box appears indicating a user-defined
	  OLE Automation error has occured.
	
	Additional query words: 4.00 vb4win vb4all
	
	======================================================================
	Keywords          :  
	Technology        : kbVBSearch kbAudDeveloper kbVB400Search kbVB400 kbVB16bitSearch
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
