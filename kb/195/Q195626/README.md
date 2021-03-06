---
layout: page
title: "Q195626: FIX: Save As HTML Not Working Correctly with Double Data Types"
permalink: /kb/195/Q195626/
---

## Q195626: FIX: Save As HTML Not Working Correctly with Double Data Types

{% raw %}

	Article: Q195626
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbvfp600 kbvfp600bug kbFFC kbVS600sp3fix kbGrpDSFox kbMiscTools1098fix
	Last Modified: 31-JUL-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use the GenHTML engine to save the contents of a Visual FoxPro table to
	a .html file, any fields of the type double are not represented correctly in the
	resulting .html file.
	
	RESOLUTION
	==========
	
	The October 1998 Visual FoxPro 6.0 Gallery and FoxPro Foundation Classes (FFC)
	update includes a new version of the GenHTML.prg file, which addresses this
	problem. You can download the update from the following Web address:
	
	http://msdn.microsoft.com/vfoxpro/downloads/updates.asp
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.This bug was corrected in the October
	1998 Visual FoxPro 6.0 Gallery and FFC updates.
	
	-and-
	
	This bug was corrected in Visual Studio 6.0 Service Pack 3.
	
	For more information about Visual Studio service packs, please see the following
	articles in the Microsoft Knowledge Base:
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That Visual Studio 6.0 Service Packs Are Installed
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	Run the following code:
	
	  *!*  Create Sample Data
	  CREATE TABLE testdata (data b(5))
	  APPEND BLANK
	  REPLACE DATA WITH 99999
	  BROWSE NOWAIT
	  *!*  Generate HTML and display in browser
	  DO (_GENHTML) WITH 'Double Field',alias(),2
	
	Note that the .html file displayed in the browser does not show any decimal
	places for the data contained in the table.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbvfp600 kbvfp600bug kbFFC kbVS600sp3fix kbGrpDSFox kbMiscTools1098fix 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
