---
layout: page
title: "Q195905: XCON: Address Space Not Updated When You Recalculate GWART"
permalink: /kb/195/Q195905/
---

## Q195905: XCON: Address Space Not Updated When You Recalculate GWART

{% raw %}

	Article: Q195905
	Product(s): Microsoft Exchange
	Version(s): WinNT:5.5
	Operating System(s): 
	Keyword(s): exc55sp2fix
	Last Modified: 21-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If you modify an entry on the Address Space tab in the properties for a
	Microsoft Exchange Server connector so that the address is not specific enough,
	recalculate the gateway address routing table (GWART), and then modify the entry
	again so that the address is more specific, the address space may not be updated
	when you recalculate the GWART again. As a result, when you send a message
	through the connector, you receive a non-delivery report (NDR) that contains the
	following text:
	
	  The recipient name is not recognized.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For more information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Component: Message Transfer Agent (MTA)
	
	  File Name      Version
	  -------------------------
	  Dbserver.sch   5.5.2410.0
	  Dcprods.cat    5.5.2410.0
	  Ems_rid.dll    5.5.2410.0
	  Emsmta.exe     5.5.2410.0
	  Info4log.cfg   5.5.2410.0
	  Infodlog.cfg   5.5.2410.0
	  Infollog.cfg   5.5.2410.0
	  Infotlog.cfg   5.5.2410.0
	  Mtacheck.exe   5.5.2410.0
	  Mtamsg.dll     5.5.2410.0
	  P2.xv2         5.5.2410.0
	  X400om.dll     5.5.2410.0
	  X400omv1.dll   5.5.2410.0
	
	
	WORKAROUND
	==========
	
	To work around this problem, run the Exchange Server Administrator program in
	raw mode, and then in the properties for the Site Addressing object, manually
	remove the old address from the Site-Proxy-Space object attribute. After you
	remove the address, recalculate the GWART again.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5.
	
	======================================================================
	Keywords          : exc55sp2fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : WinNT:5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
