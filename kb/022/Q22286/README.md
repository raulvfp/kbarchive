---
layout: page
title: "Q22286: No More Than 255 Modules May Be Placed in Overlays"
permalink: /kb/022/Q22286/
---

## Q22286: No More Than 255 Modules May Be Placed in Overlays

{% raw %}

	Article: Q22286
	Product(s): See article
	Version(s): 4.00 5.00 5.10 6.00 6.00a
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | s_quickc s_link | mspl13_c
	Last Modified: 15-JAN-1991
	
	Question:
	
	The "too many overlays" error message indicates that my program
	defines more than 63 overlays. Is there also a limitation on the
	number of total modules that can be in overlays?
	
	I have a large C program that contains more than 255 modules in a
	total of 12 overlays. I receive no error messages, however, my link
	map indicates that all modules after the 255th are placed in the root
	instead of the overlays I specified.
	
	Response:
	
	There is a limit of 255 code segments that can be overlayed. Segments
	beyond this limit are put in the root.

{% endraw %}
