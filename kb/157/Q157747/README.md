---
layout: page
title: "Q157747: PPT: Palatino Font Prints Squished From Windows 95"
permalink: /kb/157/Q157747/
---

## Q157747: PPT: Palatino Font Prints Squished From Windows 95

{% raw %}

	Article: Q157747
	Product(s): Microsoft PowerPoint for Windows
	Version(s): WINDOWS:3.0,4.0,4.0a,4.0c,7.0,7.0b; winnt:4.0
	Operating System(s): 
	Keyword(s): kbprint kbFont
	Last Modified: 07-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft PowerPoint for Windows 95, versions 7.0, 7.0b 
	- Microsoft PowerPoint for Windows, versions 3.0, 4.0, 4.0a, 4.0c 
	- the operating system: Microsoft Windows 95 
	- the operating system: Microsoft Windows NT 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If your slide contains text using the Palatino font, and you print it to a
	PostScript printer from a computer running Windows 95 or Windows NT 4.0, the
	text is printed with incorrect character spacing. Specifically, letters are
	printed too close together and wide letters and symbols (such as W, /, m, and so
	forth) overlap each other. This effect is most noticeable in text that uses
	Palatino, though it also occurs in text that uses Palatino Bold, Palatino
	Italic, and Palatino Bold Italic.
	
	If your version of PowerPoint runs under Windows 3.1 or 3.11 and you print the
	same slide, the text prints correctly.
	
	The same text prints correctly from Microsoft Word for Windows and Word for
	Windows 95.
	
	WORKAROUND
	==========
	
	PowerPoint ships with a TrueType font called Book Antiqua. This TrueType font is
	virtually identical to Palatino. Substitute Book Antiqua for Palatino.
	
	PowerPoint 7.0 and 4.0
	----------------------
	
	1. On the Format menu, click Replace Fonts.
	
	2. From the Replace list, click Palatino.
	
	3. From the With list, click Book Antiqua.
	
	4. Click Replace and then click Close.
	
	PowerPoint 3.0
	--------------
	
	1. On the Text menu, click Replace Fonts.
	
	2. In the Replace column, click the check box next to Palatino.
	
	3. In the With column, click Book Antiqua.
	
	4. Click OK.
	
	
	Additional query words: 4.00a 4.00c 7.00b kerning squished too close overlapping PS QMS Agfa LaserJet 4SI post script internal font ppt95
	
	======================================================================
	Keywords          : kbprint kbFont 
	Technology        : kbOSWin95 kbOSWinSearch kbPowerPtSearch kbOSWinNT400 kbPowerPt95 kbZNotKeyword2 kbPowerPt95Search kbPowerPt400 kbPowerPt95b kbPowerPt300 kbPowerPt400c kbPowerPt400a kbOSWinNTSearch
	Version           : WINDOWS:3.0,4.0,4.0a,4.0c,7.0,7.0b; winnt:4.0
	Hardware          : x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
