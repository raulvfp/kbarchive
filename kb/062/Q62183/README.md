---
layout: page
title: "Q62183: C2404 Error with /qc Compile Option and fidiv Instruction"
permalink: /kb/062/Q62183/
---

## Q62183: C2404 Error with /qc Compile Option and fidiv Instruction

{% raw %}

	Article: Q62183
	Product(s): See article
	Version(s): 6.00   | 6.00
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | s_quickc s_quickasm buglist6.00 | mspl13_c
	Last Modified: 29-MAY-1990
	
	When the following program is compiled with the quick compiler option
	(/qc), with C version 6.00 or with QuickC versions 2.50 and 2.51, the
	compiler will return error C2404.
	
	Sample Code
	-----------
	
	1. void main (void)
	2. {
	3.    int foo = 3 ;
	4.
	5.    _asm fidiv   foo
	6. }
	
	The compiler responds with the following error:
	
	   fpburgr.c(5) : error C2404: 'ST' : illegal register in 'operand 3'
	
	Currently, the only workaround is to not use the /qc option with C
	6.00. There is no known workaround for QuickC.
	
	Microsoft has confirmed this to be a problem with C version 6.00 and
	QuickC versions 2.50 and 2.51. We are researching this problem and
	will post new information here as it becomes available.

{% endraw %}
