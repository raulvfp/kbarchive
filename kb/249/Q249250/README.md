---
layout: page
title: "Q249250: XADM: Proxy Addresses May Be Modified After Applying Window"
permalink: /kb/249/Q249250/
---

## Q249250: XADM: Proxy Addresses May Be Modified After Applying Window

{% raw %}

	Article: Q249250
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): exc55 kbExchange550preSP4fix kbExchange550sp4Fix
	Last Modified: 10-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	After you apply Windows NT Server version 4.0 Service Pack 4 (and later), the
	proxy addresses for directory entries that contain the following two Eastern
	European characters are modified to random values:
	
	- The Latin small letter z with caron (unicode 017e) is no longer converted to
	  z.
	
	- The Latin capital letter Z with caron (unicode 017d) is no longer converted
	  to Z.
	
	CAUSE
	=====
	
	In Windows NT Server 4.0 Service Pack 4 (and later), the two characters in the
	"Symptoms" section of this article from CP 1250 (Central Europe) have been added
	to CP 1252 (Latin I).
	
	Microsoft official codepage definitions can be found at the following Web site:
	
	  http://microsoft.com/globaldev/reference/wincp.asp
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server 5.5.
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the latest Exchange Server 5.5 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5. This problem was first corrected in Exchange Server 5.5 Service
	Pack 4.
	
	
	Additional query words: CP1250 CP1252 generator
	
	======================================================================
	Keywords          : exc55 kbExchange550preSP4fix kbExchange550sp4Fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
