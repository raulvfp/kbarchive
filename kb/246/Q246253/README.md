---
layout: page
title: "Q246253: XADM: Site Folders Deleted for Exchange Sites in the Directory"
permalink: /kb/246/Q246253/
---

## Q246253: XADM: Site Folders Deleted for Exchange Sites in the Directory

{% raw %}

	Article: Q246253
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): exc55 kbExchange550preSP4fix kbExchange550sp4Fix kbgraphxlinkcritical
	Last Modified: 01-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	Site folders are deleted for Exchange Server sites that exist in the directory.
	Servers experiencing this issue may have messaging clients that have
	difficulties accessing Schedule+ free and busy information and offline Address
	Books for specific sites in the Exchange Server organization.
	
	Users may receive a message similar to the following:
	
	  Unable to update public free/busy data. The contents of this public folder
	  are currently unavailable. Either the Microsoft Exchange Server computer
	  servicing this public folder is down or the public folder has not been
	  replicated to this site. See your administrator.
	
	-or-
	
	  An error occurred while opening the Microsoft Exchange offline address book
	  files on the Microsoft Exchange Server. See your administrator.
	
	If diagnostic logging levels are turned to Maximum for Replication Site Folders
	in the public information store, you may see events similar to the following
	when you start the information store:
	
	  Event ID: 3051
	  Source: MSExchangeIS Public
	  Type: Information
	  Category: Replication Site Folders
	  Description: The unused site folder (1b4-7) NON_IPM_SUBTREE\SCHEDULE+ FREE
	  BUSY\EX:/o=ORGANIZATION/ou=SITE-NAME was deleted.
	
	-and-
	
	  Event ID: 3051
	  Source: MSExchangeIS Public
	  Type: Information
	  Category: Replication Site Folders
	  Description: The unused site folder (1b4-8) NON_IPM_SUBTREE\OFFLINE ADDRESS
	  BOOK\EX:/o=ORGANIZATION/ou=SITE-NAME was deleted.
	
	CAUSE
	=====
	
	A process within the information store compares a sorted list of Exchange Server
	sites (obtained from the directory) to a sorted list of Exchange Server sites
	present in the public information store (obtained by a query to the information
	store). These two lists are not sorted by the same string comparison operation,
	which results in two lists that differ slightly (usually a difference which
	affects sites with special characters, such as the hyphen character).
	
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server 5.5.
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the latest Exchange Server 5.5 Service Pack
	
	
	The following files are available for download from the Microsoft Download
	Center:
	
	  x86: DownloadDownload Q248838engi.exe now
	  (http://www.microsoft.com/downloads/release.asp?ReleaseID=25443)
	  Alpha: DownloadDownload Q248838enga.exe now
	  (http://www.microsoft.com/downloads/release.asp?ReleaseID=25444)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	NOTE: When you start this version of the information store, the information store
	databases are automatically upgraded to a new format. After the databases have
	been upgraded, you can restore an earlier version of the Store.exe file on the
	server, but only if it is version 5.5.2651.32 or later. If you restore a
	Store.exe file earlier than version 5.5.2651.32 after the database has been
	upgraded, you are no longer able to start the information store. For additional
	information, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q244976 XADM: Event ID 1197 and 1005 When Starting the Information Store
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5. This problem was first corrected in Exchange Server 5.5 Service
	Pack 4.
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55 kbExchange550preSP4fix kbExchange550sp4Fix kbgraphxlinkcritical 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
