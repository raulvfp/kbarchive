---
layout: page
title: "Q169299: XCON: HP Openmail Returns a Loop Detected NDR to Exchange"
permalink: /kb/169/Q169299/
---

## Q169299: XCON: HP Openmail Returns a Loop Detected NDR to Exchange

{% raw %}

	Article: Q169299
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): kbusage exc4 exc5 exc55
	Last Modified: 19-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you send a mail message to an HP Openmail message transfer agent (MTA) over
	an X.400 88 Connector in X.410 RTS mode (84), you may receive a non- delivery
	report (NDR) indicating that the originator of the message detected looping.
	Note that the recipient on the HP system does receive the message.
	
	CAUSE
	=====
	
	This behavior may happen if you select the default "Use the GDI from Site
	Addressing" option on the Advanced tab of an X.400 Connector and the remote MTA
	is in fact in a different Private Management Domain (PRMD).
	
	RESOLUTION
	==========
	
	To resolve this problem, specify a Global Domain Identifier (GDI) on the
	Exchange Server X.400 Connector that matches the remote system's GDI:
	
	1. In the Exchange Server Administrator program, select the X.400 Connector
	  corresponding to the remote MTA:
	
	  Org/Site/Configuration/Connections/<X.400 Connector>
	
	2. On the File menu, click Properties to edit the properties of this X.400
	  Connector.
	
	3. On to the Advanced tab, select the "Use the GDI specified below" option.
	
	4. Set the Country, ADMD, and PRMD values according to the remote site values.
	
	The GDI, which is composed of three X.400 attributes (Country, Administration
	Management Domain, Private Management Domain), now contains the values of the
	remote site's attributes. This new setting will eliminate the loop detected
	NDRs.
	
	MORE INFORMATION
	================
	
	When you select the "Use the GDI from Site Addressing" option in the advanced
	property page of an X.400 Connector, the Internal X.400 Trace Information is
	conveyed to remote MTA instead of being removed from P1 envelope. In some cases,
	for example if you have asked for a delivery receipt, this trace information
	causes a loop detection NDR to be sent back to Exchange user:
	
	  Your message did not reach some or all of the intended recipients.
	
	     Subject: Test message to HP Openmail
	     Sent: 01.07.97 15:13:05
	
	  The following recipient(s) could not be reached:
	
	     /c=c/a=Admd/p=Prmd/o=Org/s=Surname/g=GivenName on 01.07.97 15:16:41
	     The recipient was detected looping within the message transfer
	    service.
	
	Additional query words: Trace
	
	======================================================================
	Keywords          : kbusage exc4 exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0,5.0,5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
