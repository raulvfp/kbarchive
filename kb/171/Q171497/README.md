---
layout: page
title: "Q171497: FIX: ListView in PictureBox on Tabbed Dialog Disappears"
permalink: /kb/171/Q171497/
---

## Q171497: FIX: ListView in PictureBox on Tabbed Dialog Disappears

{% raw %}

	Article: Q171497
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbVBp500 kbVS97sp2fix kbGrpDSVB kbvbp500sp2fix
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A ListView control that is displayed in a PictureBox on a Tabbed Dialog Control
	is not repainted after the SetFocus method has been called.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been fixed in Visual Studio 97 Service
	Pack 2.
	
	For more information on the Visual Studio 97 Service Pack 2, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q170365 INFO: Visual Studio 97 Service Packs - What, Where, and Why
	
	For a list of the Visual Basic 5.0 bugs that were fixed in the Visual Studio 97
	Service Pack 2, please see the following article in the Microsoft Knowledge
	Base:
	
	  Q171554 INFO: Visual Basic 5.0 Fixes in Visual Studio 97 Service Pack 2
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new "Standard EXE" project in Microsoft Visual Basic 5.0.
	
	2. Click Components on the Project menu and check "Microsoft Tabbed Dialog
	  Control 5.0" (TABCTL32.OCX) and "Microsoft Windows Common Controls 5.0"
	  (COMCTL32.OCX).
	
	3. Add an SSTab control to Form1.
	
	4. Add a PictureBox control to the second Tab of SSTab1.
	
	5. Place a ListView control inside the PictureBox control.
	
	6. Add a ListView control to the third Tab of SSTab1.
	
	7. Add the following code to Form1:
	
	        Private Sub SSTab1_Click(PreviousTab As Integer)
	           Select Case SSTab1.Tab
	           Case 1
	              ListView1.SetFocus
	           Case 2
	              ListView2.SetFocus
	           End Select
	        End Sub
	
	8. Run the project.
	
	9. Click Tab2. Note that the ListView control on the second Tab is not visible.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVBp500 kbVS97sp2fix kbGrpDSVB kbvbp500sp2fix 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500 kbVB500
	Version           : 5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
