---
layout: page
title: "Q51240: Mouse and Renaissance Legacy II Switch Graphics Adapter"
permalink: /kb/051/Q51240/
---

## Q51240: Mouse and Renaissance Legacy II Switch Graphics Adapter

{% raw %}

	Article: Q51240
	Product(s): See article
	Version(s): 1.00
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | | mspl13_basic
	Last Modified: 20-MAR-1990
	
	Problem:
	
	A serial mouse is installed on a computer with a Renaissance video
	card and the mouse driver reports that it is installed. However, the
	mouse does not respond in programs.
	
	Response:
	
	The Renaissance card has an InPort-type mouse adapter, which the mouse
	driver finds before it checks for a serial mouse.
	
	To correct this problem, include the /C1 or /C2 option on the mouse
	command line to specify where the mouse driver should look for the
	mouse. For example, do the following for COM1:
	
	   mouse /C1

{% endraw %}
