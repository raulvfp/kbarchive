---
layout: page
title: "Q169715: XCON: Exchange Server MTA Generates Event ID 208"
permalink: /kb/169/Q169715/
---

## Q169715: XCON: Exchange Server MTA Generates Event ID 208

{% raw %}

	Article: Q169715
	Product(s): Microsoft Exchange
	Version(s): WinNT:4.0,5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 22-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When a message is submitted for delivery, the Microsoft Exchange Server message
	transfer agent (MTA) may generate the following Event ID in the Application
	Event Log:
	
	  MSExchangeMTA Event ID: 208
	  Type: Warning
	  Category: Security
	  The default latest delivery time for the message C=US;AMD;P=PRMD;L= has
	  expired (10080 minutes after a submission). A non-delivery report has
	  been generated with reason code unable-to-transfer and diagnostic code
	  maximum-time-expired. [MTA XFER-IN 17 358] (14)
	
	You may also notice the following events appearing in the application event log
	intermittently:
	
	  Event ID:  208
	  Source:  MSExchangeMTA
	  Type:  Warning
	  Category:  Security
	  Description:  The default latest delivery time for message
	  C=US;A=ATTMAIL;P=ACMECORP;L=SEATTLE-EXCHANGE-00065E89 has expired
	  (10080 minutes after submission). A non-delivery report has been
	  generated with reason code Unable to Transfer and diagnostic code
	  MAX TIME EXPIRED. [MTA XFER-I 23 358] (14)
	
	  Event ID:  290
	  Source MSExchangeMTA
	  Type:  Warning
	  Category:  X.400 Service
	  Description:  A non-delivery report (reason code unable-to-transfer
	  and diagnostic code maximum-time-expired) is being generated for
	  message C=US;A=ATTMAIL;P=ACMECORP;L=SEATTLE-EXCHANGE-00065E89. It
	  was originally destined for DN:/o=ACMECORP/ou=SEATTLE/cn=MS Mail
	  Addresses/n=SMTP: arnold.schwarzeneggar@acmecorp.com 2F52A9AC[ASCII 167]
	  (recipient number 1), and was to be redirected to . [MTA DISP:ROUTER
	  14 136] <12)
	
	In a large organization, this may be the only existing evidence that a message is
	generating a non-delivery report.
	
	MORE INFORMATION
	================
	
	If the Event ID is generated for messages immediately following their
	submission, it is usually an indication that one or more of the servers involved
	has an incorrect system date or time setting.
	
	Using Message Tracking and the Message ID reported in Event 208 (namely
	C=US;A=ATTMAIL;P=ACMECORP;L=SEATTLE-EXCHANGE-00065E89), it is possible to
	determine the originator of the message. In one case, it was discovered that the
	computer DATE on the Sender's computer was set one year off (1996 instead of
	1997). Hence, when messages arrived at the Exchange Server MTA for routing and
	delivery, the MTA compared the message date stamp (generated at the originating
	system) to the local system date setting for the Exchange Server MTA, and
	determined that the maximum time for delivery had expired.
	
	WORKAROUND
	==========
	
	Verify that the date and time settings are set appropriately for each server and
	computer involved in message submission and delivery.
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : WinNT:4.0,5.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
