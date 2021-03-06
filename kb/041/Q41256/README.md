---
layout: page
title: "Q41256: ROMable Code Using Microsoft C"
permalink: /kb/041/Q41256/
---

## Q41256: ROMable Code Using Microsoft C

{% raw %}

	Article: Q41256
	Product(s): See article
	Version(s): 5.10
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | SR# G890121-10245 appnote | mspl13_c
	Last Modified: 31-MAY-1989
	
	Question:
	
	How can I use the Microsoft C Compiler to produce code that will be
	put into ROM?
	
	Response:
	
	The best way is to use a third-party package designed to produce
	ROMable code using Microsoft C. The linker supplied with our compiler
	only produces code designed to run under the DOS and OS/2
	environments. CodeView only runs under DOS or OS/2. Third-party
	packages typically include an alternate linker and debugger.
	
	You can find out more about these third-party packages by obtaining a
	copy of a technically oriented PC magazine or by talking with a dealer
	who sells such packages. Microsoft also provides an application note
	called "Writing ROMable Code in Microsoft C," which can be obtained
	from Microsoft Product Support Services by calling (206) 454-2030.

{% endraw %}
