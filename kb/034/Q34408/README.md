---
layout: page
title: "Q34408: Far Pointer Comparisons Assume Same Segment"
permalink: /kb/034/Q34408/
---

## Q34408: Far Pointer Comparisons Assume Same Segment

{% raw %}

	Article: Q34408
	Product(s): See article
	Version(s): 5.10   | 5.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | | mspl13_c
	Last Modified: 12-OCT-1988
	
	When comparing Far pointers with the <, >, <=, or >= operators, the
	two pointers must be in the same segment. The equality operator (==)
	tests both segment and offset to prevent two pointers that have the
	same offset but different segments from being considered equal.
	
	The <, >, <=, and >= operators assume that the pointer share the same
	segment because according to the Draft proposed ANSI C standard,
	pointers can only be compared for precedence if they point to the same
	object. In a segmented architecture such as Intel's, two pointers to
	the same object must share the same segment value (unless the
	pointers are declared to point to a huge object, in which case
	the pointers are handled using 32-bit arithmetic).

{% endraw %}
