---
layout: page
title: "Q138818: BUG: VB 4.0 32-bit Quits When Deleting a Menu at Design Time"
permalink: /kb/138/Q138818/
---

## Q138818: BUG: VB 4.0 32-bit Quits When Deleting a Menu at Design Time

{% raw %}

	Article: Q138818
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0
	Operating System(s): 
	Keyword(s): kbenvkbbuglist
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After a specific series of menu manipulations with the Menu Editor and the
	Properties window, deleting a menu and continuing with work causes VB32.EXE to
	crash.
	
	RESOLUTION
	==========
	
	This problem occurs only with a very specific sequence of actions, and you can
	easily work around it by avoiding the series of actions outlined in the "Steps
	to Reproduce Problem" section of this article.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. We are researching this problem and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Start a new project in Visual Basic.
	
	2. Click the Menu Editor icon in the toolbar to bring up the Menu Editor.
	
	3. In the Menu Editor dialog box, enter 'a' in the Name text box and 'a' in the
	  Caption text box to create a single menu with no subitems. Click OK.
	
	4. In the Properties window, select the menu that was just created.
	
	5. Click anywhere in the non-client area of the form - the menu bar, title bar,
	  or borders.
	
	6. Click the Menu Editor icon again, and when the Menu Editor dialog box
	  appears, delete the menu 'a' and click OK. The properties for the menu will
	  stay visible in the Properties window, and the Name, Caption, and Shortcut
	  properties will become gibberish. If you now attempt to add a new control,
	  Visual Basic will quit.
	
	Additional query words: 4.00 vb4win vb432 crash buglist4.00
	
	======================================================================
	Keywords          : kbenv kbbuglist
	Technology        : kbVBSearch kbAudDeveloper kbVB400Search kbVB400
	Version           : WINDOWS:4.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
