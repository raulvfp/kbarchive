---
layout: page
title: "Q179361: WD97: Toolbar Button Color Lost Converting Word 95 Toolbar"
permalink: /kb/179/Q179361/
---

## Q179361: WD97: Toolbar Button Color Lost Converting Word 95 Toolbar

{% raw %}

	Article: Q179361
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbui
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In Microsoft Word 97, if you open a Microsoft Word for Windows 95, version 7.0
	document or template containing a toolbar with the sad face assigned to a
	toolbar button, the original color of the sad face button is lost.
	
	CAUSE
	=====
	
	There are certain reserved colors in both Word 95 and Word 97 for Windows. In
	Word 95, bright purple is reserved, while in Word 97, bright green and bright
	purple are reserved. When you open a toolbar button containing a reserved color
	in Word 97, Word makes those colors transparent.
	
	The original color of the sad face button in Word 95 is bright green. Because
	bright green is a Word 97 reserved color, it becomes transparent when converted
	to Word 97.
	
	WORKAROUND
	==========
	
	In Word 97, the sad face button image is the same color as the toolbar. If you
	want to use a button image with color, follow these steps:
	
	1. Right-click the mouse on the converted toolbar button and then click
	  Customize.
	
	2. Click once to select the sad face button (it should place a black border
	  around the sad face) and then right-mouse click the button to show its
	  shortcut menu.
	
	3. Use either of the following methods:
	   - Point to Change Button Image and select a button face with color on it.
	
	     NOTE: The sad face icon is the color of the background.
	
	  -or-
	
	   - Click Edit Button Image, make the appropriate color changes, and then
	     click OK.
	
	4. Click Close.
	
	MORE INFORMATION
	================
	
	For more information about customizing button faces, click the Office Assistant,
	type "change toolbar," click Search, and then click "Change the image on a
	toolbar button or menu command."
	
	NOTE: If the Assistant is hidden, click the Office Assistant button on the
	Standard toolbar. If Word Help is not installed on your computer, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q120802 Office: How to Add/Remove a Single Office Program or Component
	
	Additional query words:
	
	======================================================================
	Keywords          : kbui 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
