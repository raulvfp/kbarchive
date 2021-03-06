---
layout: page
title: "Q145678: PRB: WIDTH # Statement Raises Error in Visual Basic 4.0"
permalink: /kb/145/Q145678/
---

## Q145678: PRB: WIDTH # Statement Raises Error in Visual Basic 4.0

{% raw %}

	Article: Q145678
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic for Applications version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The WIDTH # statement is used to assign an output-line width to a file opened
	using the Open statement. However, the sample code given in the Visual Basic
	Help file does not work in a form.
	
	STATUS
	======
	
	Microsoft has confirmed this to be an issue in the Microsoft products listed at
	the beginning of this article. We are researching this problem and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	The problem is that Visual Basic interprets the "Width" statement as a property
	of the Form when the code is run from a Form module. When run from a Code module
	or a Class module, the statement functions as documented because there is no
	default object on which to apply the Width property. Visual Basic 4.0 can be
	forced to use the correct Width statement in this case by specifying the call
	using "Typelib.Method" syntax. The Width statement is actually a "Visual Basic
	for Applications" (VBA) method, so the following syntax must be used:
	
	     VBA.Width filenum, width
	
	     Private Sub Command1_Click()
	
	        Open "TESTFILE" For Output As #1
	        VBA.Width 1, 5 ' Note:  "#" symbol omitted
	        For I = 0 To 9
	           Print #1, Chr(48 + I);
	        Next I
	        Close #1
	
	     End Sub
	
	NOTE: The compiler will not accept this statement unless the "#" symbol is
	removed.
	
	Steps to Reproduce
	------------------
	
	1. Start a new project in Visual Basic. Form1 is created by default. Place the
	  following code in Form1's Form_Click Event.
	
	        Private Sub Form_Click()
	          Open "TESTFILE" For Output As #1  ' Open file for output.
	          Width #1, 5 ' Set output-line width to 5.
	          For I = 0 To 9  ' Loop 10 times.
	              Print #1, Chr(48 + I); ' Prints 5 characters per line.
	          Next I
	          Close #1    ' Close file.
	        End Sub
	
	2. Run the program and then click the form. An "Invalid use of property" error
	  is generated.
	
	Additional query words: kbVBp400 kbVBp500 kbVBp600 kbVBp kbdsd kbDSupport kbVBA500 kbCompiler
	
	======================================================================
	Keywords          : kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400 kbVBASearch kbZNotKeyword3 kbVB16bitSearch
	Version           : WINDOWS:4.0,5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
