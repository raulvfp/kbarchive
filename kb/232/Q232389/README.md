---
layout: page
title: "Q232389: XCON: DRAS Failing after You Upgrade to Windows NT 4.0 SP4"
permalink: /kb/232/Q232389/
---

## Q232389: XCON: DRAS Failing after You Upgrade to Windows NT 4.0 SP4

{% raw %}

	Article: Q232389
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0,4.0 SP4,5.0,5.5
	Operating System(s): 
	Keyword(s): exc4 exc5 exc55
	Last Modified: 18-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	- the operating system: Microsoft Windows NT 4.0 SP4 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The Dynamic RAS Connector may fail to transfer mail after you upgrade to
	Microsoft Windows NT Server version 4.0 Service Pack 4. The dialing server
	receives the following event and is immediately disconnected:
	
	  Event ID: 20082
	  The account for user %1\%2 connected on port %3 does not have Remote Access
	  privilege. The line has been disconnected.
	
	The remote server receives the following events:
	
	  Event ID: 9309
	  Source: MSExchangeMTA
	  Category: Field Engineering
	  A RAS Dial error has occurred for gateway
	  /o=Company/ou=XXX/cn=Configuration/cn=Connections/cn=RAS TO SITEA. RAS error
	  code returned: 676, RAS Table index: 0. The MTA will attempt to recover the
	  RAS connection. [BASE IL PIPE RAS 103 230] (12)
	
	  Event ID: 9323
	  Source: MSExchangeMTA
	  Category: Interface
	  An interface error has occurred. An MtaUnBindBack over RPC has failed.
	  Locality Table (LTAB) index: 73, NT/MTA error code: 1783. [BASE IL MAIN BASE
	  5 519] (14)
	
	WORKAROUND
	==========
	
	There are two workarounds:
	
	- On all servers that are initiating the connection:
	
	  1. Start the Exchange Server Administrator program.
	
	  2. In the left pane, click the Connections object, and in the right pane,
	     double click the Dynamic Ras Connector to be modified.
	
	  3. Click the RAS Override tab, and specify an account other than Service in
	     the Connect As portion.
	
	  The alternate account specified must have Service Account Admin permissions on
	  the remote Exchange Server computer.
	
	- Copy in Rassapi.dll from a Windows NT Service Pack 3 installation to the
	  Winnt\System32 directory.
	
	MORE INFORMATION
	================
	
	Dynamic RAS fails to transfer if the account specified on the Override tab is
	called Service. The problem has been known to occur when you dial computers
	running Windows NT Server that have been upgraded to Service Pack 4.
	
	After the upgrade is complete, accessing the Service account through the RAS
	Administrator interface yields the following error message:
	
	  Error 6: The handle is invalid.
	
	Additional query words:
	
	======================================================================
	Keywords          : exc4 exc5 exc55 
	Technology        : kbWinNTsearch kbWinNTW400search kbWinNTW400sp4 kbWinNTSsearch kbWinNTSEntSearch kbExchangeSearch kbExchange550 kbExchange400 kbZNotKeyword2 kbGraph500
	Version           : winnt:4.0,4.0 SP4,5.0,5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
