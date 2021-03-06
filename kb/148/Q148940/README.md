---
layout: page
title: "Q148940: Admin &quot;Select Domain&quot; SNA Server in Subdomain Fails"
permalink: /kb/148/Q148940/
---

## Q148940: Admin &quot;Select Domain&quot; SNA Server in Subdomain Fails

{% raw %}

	Article: Q148940
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.11,2.11 SP1
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.11, 2.11 SP1, on platform(s):
	   - the operating system: Microsoft Windows NT 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If the SNA Server Administrator tool is used to open a configuration of a server
	that is in the same Microsoft Windows NT domain, but on a different SNA
	subdomain, the SNA Server Administrator tool will incorrectly show the current
	local configuration; however, it will show the requested domain in the lower
	right hand side status bar entry (Domain: XXXXXX).
	
	This problem does not occur if the remote SNA Server is in a different Windows NT
	domain.
	
	CAUSE
	=====
	
	This problem was inadvertently introduced in SNA Server 2.11 Service Pack 1 when
	the Distributed Link Service support was added to the product.
	
	
	WORKAROUND
	==========
	
	An update to SNA Server 2.11 Service Pack 1 is available to correct this
	problem.
	
	Without applying this update, a workaround exists if you are connecting to the
	remote server over a LAN interface other than TCP/IP sockets:
	
	Use the following syntax when you use SNA Server Admin to administer a server in
	the same Windows NT domain, but a different SNA subdomain:
	
	  SNAADMIN /NET:<subdomain name>
	
	where <subdomain name> is the name of the subdomain you wish to
	administer.
	
	NOTE: The above workaround will not work when you use TCP/IP sockets to connect
	to the remote SNA Server machine (for example, there is no subdomain ->
	server IP address name resolution mechanism available when using TCP/IP
	sockets).
	
	For additional information on the /NET switch for SNAADMIN, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q141906 Domain/Server Command Line Parameter Added to SNAADMIN
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server version 2.11 with
	Service Pack 1 installed. This problem was corrected in the latest Microsoft SNA
	Server 2.11 U.S. Service Pack. For information on obtaining the service pack,
	query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	
	Additional query words: prodsna
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbAudDeveloper kbSNAServSearch
	Version           : WINDOWS:2.11,2.11 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
