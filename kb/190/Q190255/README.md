---
layout: page
title: "Q190255: BUG: DHTML Page Designer Does Not Insert the &lt;HTML&gt; Tag"
permalink: /kb/190/Q190255/
---

## Q190255: BUG: DHTML Page Designer Does Not Insert the &lt;HTML&gt; Tag

{% raw %}

	Article: Q190255
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbInternet kbPageDesigner kbVBp kbVBp600bug
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	1. The browser incorrectly displays your HTML page.
	
	2. Unexpected behavior occurs when you work on your page in the designer window
	  of your DHTML application.
	
	CAUSE
	=====
	
	DHTML Page Designer is not inserting an <HTML> tag at the beginning of the
	HTML file it creates.
	
	RESOLUTION
	==========
	
	To work around this problem, use one of the following three options:
	
	Option 1
	--------
	
	Store your DHTML Page Designer page as an external HTML file. Edit the HTML file
	manually using an external editor and insert the <HTML> tag.
	
	Option 2
	--------
	
	Import an existing HTML file when creating a new DHTML Page Designer page.
	
	Option 3
	--------
	
	Change the default DHTML Page Designer template so all HTML files have the
	<HTML> tag. The template project is "DHTML application.vbp". This project
	is stored under the Visual Studio folder in the VB98\Template\Projects
	subfolder.
	
	NOTE: Save copies of all the files for the "DHTML application.vbp" (this is the
	default DHTML Page Designer template) in a backup location in case something
	goes wrong. Follow these steps:
	
	1. Open the "DHTML application.vbp" project in Visual Basic.
	
	2. Open the DHTMLPage1 Properties dialog box.
	
	3. Select "Save the HTML as an External file".
	
	4. Select "Create new HTML file".
	
	5. Launch the external editor to edit this HTML page.
	
	6. Delete the two lines with <HTML> and <HEAD> tags (there seems to
	  be a corrupted character on one of them).
	
	7. Retype the <HTML> and <HEAD> tags.
	
	8. Open the DHTMLPage1 Properties dialog box.
	
	9. Select "Save HTML as part of the VB project".
	
	10. Select the File menu item and save both the DHTMLPage1.dsr file and
	  DHTMLPage1.vbp file
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. We are researching this bug and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	To take advantage of more editing features, you may want to use an external
	editor. To use an external editor on your page, you must store it as an external
	HTML file. Or, use the Launch Editor icon in the DHTML Page Designer toolbox, as
	described in the following article in the Microsoft Knowledge Base:
	
	  Q190252 HOWTO: Change the External HTML Editor
	
	REFERENCES
	==========
	
	Please see the following Microsoft Knowledge Base article for more information
	on the DHTML Page Designer:
	
	  Q190249 INFO: VB 6.0 Readme Part 9: DHTML Page Designer Issues
	
	Additional query words:
	
	======================================================================
	Keywords          : kbInternet kbPageDesigner kbVBp kbVBp600bug 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
