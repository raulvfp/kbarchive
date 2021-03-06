---
layout: page
title: "Q68391: C 6.00/6.00a Do Not Give Warning That /Gm Is Not Functioning"
permalink: /kb/068/Q68391/
---

## Q68391: C 6.00/6.00a Do Not Give Warning That /Gm Is Not Functioning

{% raw %}

	Article: Q68391
	Product(s): See article
	Version(s): 6.00 6.00a | 6.00 6.00a
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | buglist6.00 buglist6.00a docerr | mspl13_c
	Last Modified: 1-FEB-1991
	
	The /Gm compiler option for moving strings to the const segment is not
	supported in C 6.00 or in C 6.00a. The compiler will permit /Gm to be
	specified on the command line, but no functionality is attached to the
	option.
	
	No warnings are displayed to inform you that /Gm is not performing any
	function, and strings are not moved to the const segment. In addition,
	the online help incorrectly lists /Gm as a valid option. However, the
	README.DOC correctly notes that the option has been removed.
	
	Microsoft has confirmed this to be a problem in C versions 6.00 and
	6.00a. We are researching this problem and will post new information
	here as it becomes available.

{% endraw %}
