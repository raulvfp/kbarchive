---
layout: page
title: "Q228738: Null in First Byte of &#91;Input&#93; String When 'Pad With Blanks' Spec"
permalink: /kb/228/Q228738/
---

## Q228738: Null in First Byte of &#91;Input&#93; String When 'Pad With Blanks' Spec

{% raw %}

	Article: Q228738
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:4.0 SP2
	Operating System(s): 
	Keyword(s): kbsna400sp3fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft COM Transaction Integrator for CICS and IMS, version 4.0 SP2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The first byte of an input string is 0x00 and the rest of the string is padded
	with EBCDIC blanks, that is, 0x40. In the COM Transaction Integrator (COMTI)
	component library, the parameter is of the 'String' automation type, and the
	corresponding COBOL definition is PIC X(n), where n is the length of the string.
	The parameter's "COBOL Definition" properties have the "Pad with spaces" check
	box selected to specify that the string delivered to the host is to be padded on
	the right with spaces by COMTI runtime.
	
	CAUSE
	=====
	
	When the pointer to the string in the client application code is NULL, or if it
	points to a zero-length string, COMTI runtime treats the variable as if a NULL
	terminator is present. If the string is not variable length, the null is then
	padded with spaces to the full length of the string as defined in the component
	library.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for SNA Server version
	4.0. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q215838 How to Obtain the Latest SNA Server Version 4.0 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in COM Transaction Integrator for
	CICS and IMS, version 4.0 SP2. This problem was first corrected in SNA Server
	version 4.0 Service Pack 3.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsna400sp3fix 
	Technology        : kbAudDeveloper kbCOMTISearch kbCOMTI400SP2
	Version           : WINDOWS:4.0 SP2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
