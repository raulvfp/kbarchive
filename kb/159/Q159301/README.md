---
layout: page
title: "Q159301: XCON: Messages Sent Over X.400 Connector Should NDR First"
permalink: /kb/159/Q159301/
---

## Q159301: XCON: Messages Sent Over X.400 Connector Should NDR First

{% raw %}

	Article: Q159301
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbusage exc4 exc5 exc55
	Last Modified: 22-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Microsoft Exchange Message Transfer Agent (MTA) may attempt, over an X.400
	connector, to deliver a message that was sent to a Microsoft Exchange mailbox
	that was recently removed from the system. The message will eventually result in
	a non-delivery report (NDR) and the sender will receive a message similar to the
	following:
	
	  Your message did not reach some or all of the intended recipients.
	
	  Subject: This is a test
	  Sent: 1/24/97 11:17:44 AM
	
	  The following recipient(s) could not be reached:
	
	  /c=US/a=ATTMAIL/p=Org/DDA:MSXCHNGE=
	  //o=Org//ou=Site//cn=RECIPIENTS//cn=Mailbox
	
	  on 1/24/97 11:16:59 AM
	
	  The recipient was detected looping within the message transfer service.
	
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange version 4.0.
	This problem was corrected in the latest Microsoft Exchange 4.0 U.S. Service
	Pack. For information on obtaining the service pack, query on the following word
	in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	MORE INFORMATION
	================
	
	This problem only happens under certain circumstances where a message has been
	sent from a user in a site where the intended recipient was not originally
	located. This could occur if someone attempts to reply to a message sent by
	someone who was recently removed from the mail system. Senders who reside in the
	same site where the intended recipient was originally located will receive an
	NDR immediately with a message similar to the following:
	
	  Your message did not reach some or all of the intended recipients.
	
	  Subject: This is a test
	  Sent: 1/24/97 11:17:44 AM
	
	  The following recipient(s) could not be reached:
	
	  'User Name' on 1/24/97 11:14:44 AM
	
	  The recipient name is not recognized.
	
	To explain this behavior more clearly, assume there is an Exchange organization
	called "Org" that consists of three sites, Site A, Site B, and Site C. Both Site
	A and Site C are connected via site connectors to Site B which is the hub for
	the organization. Site B connects the organization to the rest of the world via
	an X400 connector. There used to be a mailbox in Site C for OldUserOnC. When a
	user in Site A attempts to reply to a message that had been sent by OldUserOnC
	prior to that user being removed from the system, the message is sent to the hub
	server in Site B. When the message reached the hub server, there are two parts
	to the recipient's address. These two parts are the DN (Distinguished Name) and
	OR (Originator/Recipient) addresses.
	
	The hub first tries to resolve the full DN which may have been similar to:
	
	/O=Org/Ou=Site C/CN=Recipients/CN=OldUserOnC
	
	The DN no longer exists in the DS since the user's mailbox had been deleted.
	Thus, it then tries to resolve the OR address via a proxy lookup. It does not
	find a new DN based on the OR address proxy lookup. It then nulls out the
	original DN and then attempts to route the message out over the X400 connector
	where it does not match anything, and ultimately NDRs.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbusage exc4 exc5 exc55 
	Technology        : kbExchangeSearch kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
