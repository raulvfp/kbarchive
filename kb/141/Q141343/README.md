---
layout: page
title: "Q141343: XCLN: POP3 Requires QUIT Command Before Delete"
permalink: /kb/141/Q141343/
---

## Q141343: XCLN: POP3 Requires QUIT Command Before Delete

{% raw %}

	Article: Q141343
	Product(s): Microsoft Exchange
	Version(s): 4.0 5.0
	Operating System(s): 
	Keyword(s): kbenv kbusage
	Last Modified: 12-MAR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	You may receive duplicate messages when retrieving Internet mail on subsequent
	connections with the Exchange Internet Provider, if your connection to the mail
	server is disrupted.
	
	The Microsoft Exchange e-mail client, with the Exchange Internet Provider,
	transports messages through the Internet using Post Office Protocol Version 3
	(POP3). This protocol requires that the client issue a QUIT command before the
	mail server removes messages marked for deletion.
	
	If the connection is disrupted before the client can issue the QUIT command, all
	messages marked for deletion will remain on the server and be downloaded again
	on the next connection.
	
	MORE INFORMATION
	================
	
	The Microsoft Exchange Internet Provider uses the POP3 protocol as outlined in
	RFC 1725. This is a protocol that outlines how e-mail clients connect to a POP3
	server to send, retrieve, and delete mail.
	
	When the client downloads mail from the POP3 server, it marks the messages for
	deletion unless COPY is specified from the Remote Mail menu in Exchange. After
	all messages are downloaded successfully, the Exchange client issues the POP3
	command QUIT, which causes the session to enter the Update state. During the
	Update state, mail marked for deletion is removed from the server and the
	network session (TCP) is closed.
	
	If a session terminates for some reason other than a client-issued QUIT command,
	the POP3 session does NOT enter the Update state and will not remove any
	messages from the server. This method assures that all messages are received OK
	before being deleted.
	
	The QUIT command must be supported by all POP3 implemented servers and clients,
	including Microsoft Exchange.
	
	Common problems that will cause an interrupted POP3 session include:
	
	- Lost carrier over a Dial-Up Networking connection via modem.
	
	- Failure at the network layer that causes TCP/IP connection to be dropped.
	
	- Call waiting signal on telephone line that causes a modem connection to be
	  lost.
	
	- Down POP3 server.
	
	Additional query words: SMTP maildrop RFC 1460
	
	======================================================================
	Keywords          : kbenv kbusage 
	Technology        : kbExchangeSearch kbExchange400 kbZNotKeyword2
	Version           : 4.0 5.0
	
	=============================================================================
	

{% endraw %}
