---
layout: page
title: "Q81223: FIX: Animated Button Custom Control: Caption May Be Truncated"
permalink: /kb/081/Q81223/
---

## Q81223: FIX: Animated Button Custom Control: Caption May Be Truncated

{% raw %}

	Article: Q81223
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 23-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 2.0 
	- Microsoft Professional Toolkit for Microsoft Visual Basic programming system for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Caption property of the Animated Button custom control allows up to 255
	characters to be entered, but only displays a varying number of those
	characters. The number of characters displayed depends on the FontSize and the
	width of the characters. The larger the font, or the wider the characters, the
	less the number of characters that will appear in the caption.
	
	WORKAROUND
	==========
	
	To work around the problem, make the font for the caption as small as feasible,
	and whenever possible, use the smallest size of characters.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Animated Button custom control
	provided with the products listed above. This problem was corrected in Animated
	Button custom control provided with Microsoft Visual Basic version 3.0 for
	Windows.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Start Visual Basic or from the File menu, choose New Project (ALT, F, N) if
	  Visual Basic is already running. Form1 is created by default.
	
	2. From the File menu, choose Add File. In the Files box, select the
	  ANIBUTTON.VBX custom control file. The Animated Button tool will appear in
	  the toolbox.
	
	3. Place an Animated Button control on Form1.
	
	4. From the Properties list box, select the Caption property for the Animated
	  Button control. Enter 255 W characters. Notice that the caption of the
	  Animated Button control is now filled with W characters.
	
	5. Maximize Form1 by clicking the maximize button in the upper-right corner of
	  Form1.
	
	6. Stretch the right side of the Animated Button control so that you can see the
	  whole caption. (To do this, click the control, and pull the handle on the
	  right side of the control.)
	
	If you change the W characters to I characters, you will be able see more of the
	characters in the caption before they are truncated because I characters takes
	proportionately less space than W characters.
	
	Additional query words: 1.00 2.00 3.00 buglist1.00 buglist2.00 fixlist3.00
	
	======================================================================
	Keywords          :  
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB200
	Version           : :2.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
