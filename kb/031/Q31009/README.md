---
layout: page
title: "Q31009: Protected-Mode C Extensions Fail with &quot;Protection Fault&quot;"
permalink: /kb/031/Q31009/
---

## Q31009: Protected-Mode C Extensions Fail with &quot;Protection Fault&quot;

{% raw %}

	Article: Q31009
	Product(s): See article
	Version(s): 1.00 | 1.00
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | docerr | mspl13_basic
	Last Modified: 29-AUG-1988
	
	Problem:
	   I am writing C extensions for the protected mode of OS/2. All my
	extensions fail with a general-protection fault. The sample program on
	Page 85 of the "Microsoft Editor for MS OS/2 and MS-DOS: User's Guide"
	also fails.
	
	Response:
	   Page 78 of the "Microsoft Editor for MS OS/2 and MS-DOS: User's
	Guide" incorrectly states that the second argument is a NULL pointer.
	   The programs are crashing because the incorrect value is being
	passed to the FileNameToHandle routine. This routine requires a
	pointer to a null string, not a null pointer.
	   For example, the following statement
	
	   cfile=FileNameTohandle("",NULL);
	
	should read as follows:
	
	   cfile=FileNameTohandle("","");

{% endraw %}
