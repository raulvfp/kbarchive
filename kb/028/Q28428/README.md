---
layout: page
title: "Q28428: Menu Problems with Leading Edge D2 in 43-Line Mode"
permalink: /kb/028/Q28428/
---

## Q28428: Menu Problems with Leading Edge D2 in 43-Line Mode

{% raw %}

	Article: Q28428
	Product(s): See article
	Version(s): 1.0
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | | mspl13_basic
	Last Modified: 21-APR-1988
	
	The characters on the screen get trashed if you load a mouse menu
	in 43-line text mode using a Leading Edge D2 with monochrome display.
	The characters are readable, but the top two or three lines of pixels
	composing the characters are repeated beneath the characters (similar
	to a vertical ghost effect).
	
	   Resetting the EGA into the 43-line mode corrects the problem
	temporarily. Run EGA.EXE with the argument EGA, or set switch 5 on the
	display adapter to the open position to disable the auto-mode
	selection feature (this process produces the same effect as the EGA
	EGA command).

{% endraw %}
