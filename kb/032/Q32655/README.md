---
layout: page
title: "Q32655: DIR Does Not Work with ANSI Escape Sequence ESC&#91;nh"
permalink: /kb/032/Q32655/
---

## Q32655: DIR Does Not Work with ANSI Escape Sequence ESC&#91;nh

{% raw %}

	Article: Q32655
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:3.3,4.x,5.0,5.0a,6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 3.3, 4.0, 4.01, 5.0, 5.0a, 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you set the mode through ANSI escape sequences with the PROMPT command,
	the following occurs regardless of the particular mode chosen. When you call
	directory listing with the DIR command, the screen clears immediately after
	displaying the directory listing, so that you do not have a chance to look at
	the directory listing. However, if you type "prompt $p$g" (without the quotation
	marks) and then use the DIR command, the directory works correctly.
	
	CAUSE
	=====
	
	Any time you use one of the ANSI escape codes to set the screen mode, the screen
	is cleared. This explains why you are seeing the screen cleared after doing a
	DIR command.
	
	WORKAROUND
	==========
	
	To avoid this problem, set the screen mode in a batch file. For example, if you
	wanted to set the screen mode to 40x25 monochrome mode, you would insert the
	following text into a batch file:
	
	  echo <ESC>[0h
	
	Depending upon your editor, you would replace <ESC> with whatever character
	represents ESCAPE. In EDLIN, you use ^[. And in other word processors, you use
	the back arrow character.
	
	
	Additional query words: 6.22 3.30 4.00 5.00 5.00a 6.00 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS400 kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS500 kbMSDOS330 kbMSDOS401 kbMSDOS500a
	Version           : MS-DOS:3.3,4.x,5.0,5.0a,6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
