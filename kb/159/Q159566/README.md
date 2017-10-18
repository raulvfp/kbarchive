---
layout: page
title: "Q159566: XCON: MTA Error 209: Submitting Domain Is Inconsistent"
permalink: kb/159/Q159566/
---

## Q159566: XCON: MTA Error 209: Submitting Domain Is Inconsistent

	Article: Q159566
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 21-JUL-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When connecting the Microsoft Exchange Server X.400 Connector to a foreign X.400
	message transfer agent (MTA), the incoming message is not accepted by the
	Microsoft Exchange Server MTA. The MTA may generate the following error message
	in the Windows NT Server event log and the Microsoft Exchange Server Evx.log (if
	enabled):
	
	  Event: 209
	  Source: MSExchangeMTA
	  Category: X400 Service
	
	  Unable to transfer in message C=xx;A=attmail;
	  P=prmd;L=<m0vBOkQ-0000xxxxxxxxxxx> because the submitting domain
	  identifier was inconsistent. A non-delivery report was generated with reason
	  code unable-to-transfer and diagnostic code invalid-arguments. Contact
	  Microsoft Product Support Services. [MTA XFER-IN 22 101] [14]
	
	  EVx.log
	
	  (MTA XFER-IN(22) Proc 101) 10-30-96 11:44:26am
	  Transfer-In failure, submitting domain inconsistent
	  X.400 reason code unable-to-transfer
	  X.400 diagnostic code invalid-arguments
	  MTS Identifier C=US;A=ATTMAIL;L=0045900001000181000002
	
	CAUSE
	=====
	
	The Microsoft Exchange Server MTA rejects the message whenever the global domain
	identifier on the first element of the trace information is different from the
	one specified in the MTSID. The global domain identifier information in the
	MTSID must be the same as the first element on the trace information. These
	values are generated by the submitting MTA.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 4.0. This problem was corrected in the latest Microsoft Exchange 4.0
	U.S. Service Pack. For information on obtaining the service pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	MORE INFORMATION
	================
	
	There are two reasons as to why Microsoft Exchange Server rejects this message,
	and both of them are by design.
	
	The first reason has to do with the firewall function. The firewall is designed
	to prevent any message transfer if the message's true origin appears to have
	been altered. Because the MTSID cannot be changed across any relaying MTA, it
	reflects the true global domain identifier of the message. However, the global
	domain identifier on the trace information can be altered to reflect a different
	country, ADMD, or PRMD, creating contradictory information about the message's
	origin. The firewall does not allow this inconsistency.
	
	The second reason has to do with conformance testing. This is required to pass
	NCC conformance tests.
	
	
	With Exchange Server 4.0, when the MTA receives this error, the message is not
	submitted for delivery to the recipient. The fix implemented in Service Pack 4
	resolves the problem of message delivery but does not remove the event ID.
	Exchange Server version 5.0 and 5.5 still log the event and deliver the message.
	The reason to log the event is that according the X.400 specifications, when the
	information is not consistent, there is likely a security concern. In practice,
	however, it is commonplace for an X.400 service provider MTA to alter the
	information. For this reason, Microsoft fixed the product to allow delivery but
	opted to still log the event.
	
	Additional query words: Inconsistent GDI
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0,5.0,5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	