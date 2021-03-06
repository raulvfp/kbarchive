---
layout: page
title: "Q303725: SMS: Logon Server Manager May Use Sender Credentials"
permalink: /kb/303/Q303725/
---

## Q303725: SMS: Logon Server Manager May Use Sender Credentials

{% raw %}

	Article: Q303725
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): kbsms200
	Last Modified: 17-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to update backup domain controllers (BDCs) that act as Systems
	Management Server (SMS) 2.0 logon points, the Logon Server Manager (LSM)
	component of the SMS Executive service may not properly update logon points that
	are also SMS site servers. The following Warning status messages may occur:
	
	  Message ID 1412:
	  SMS NT Logon Server Manager failed to find a suitable drive on domain
	  controller "BDC22" for domain "DOMAIN11" to hold the "SMSLOGON" directory.
	  Possible cause: Every NTFS drive on the domain controller has less than 50 MB
	  of free disk space. Solution: Either free up enough space on an NTFS drive or
	  manually create the "SMSLOGON" directory on the root directory of an NTFS
	  drive and share it out as "SMSLOGON". If you manually create the directory,
	  it might have less than 50 MB of free disk space.
	
	  Message ID 1418:
	  SMS NT Logon Server Manager failed to complete all of the configuration tasks
	  on domain controller "BDC22" for domain "DOMAIN11". These tasks include:
	
	  1. Assigning the SMS Logon Point role to the site system "\\BDC22".
	
	  2. Modifying the user logon scripts, if instructed to do so by the configuration
	  of the Windows Networking Logon Discovery and Client Installation methods.
	
	  3. Creating and updating the "SMSLOGON" share and the directories and files
	  associated with it.
	
	  4. Installing the SMS_NT_LOGON_DISCOVERY_AGENT service.
	
	If logging is enabled, an error message similar to the following message may be
	logged in the Nt_logon.log file:
	
	  ~NetShareEnum failure Unable to Enumerate NTLM volumes on server BDC22,
	  error=5
	
	CAUSE
	=====
	
	This issue can occur if all of the following conditions exist:
	
	- At least one site server in the site hierarchy is installed on a Microsoft
	  Windows NT-based or Microsoft Windows 2000-based domain controller.
	
	- Windows NT Logon Installation or Discovery is enabled on at least one site in
	  the hierarchy.
	
	- The site server of the site that is designated as the senior site for the
	  domain has a Sender address defined and in use for an SMS site server that
	  also acts as an SMS logon point.
	
	- The defined SMS Sender site address is configured with account credentials
	  that do not have administrative rights to the destination site domain
	  controller.
	
	- SMS Sender is actively sending data, or has a session open with the
	  destination site domain controller when Logon Server Manager is updating the
	  domain controllers in the domain.
	
	When Logon Server Manager attempts to connect to a domain controller to configure
	the SMSLOGON share or the SMS_LOGON_DISCOVERY_AGENT service, it does not succeed
	because it attempts to use the existing session credentials that are in use by
	SMS Sender to connect to the Admin$ share on the BDC. The session credentials
	that Sender uses do not necessarily have administrative rights to the domain
	controller.
	
	WORKAROUND
	==========
	
	To work around this problem, use any of the following methods:
	
	- Configure the account that is specified in Sender Address properties for the
	  target site to be an administrator in the domain.
	
	- Configure the account that is specified in Sender Address properties for the
	  target site to be the SMS Service account, and ensure that it has
	  administrative rights in the domain.
	
	  For additional information about configuring site addresses, see the Microsoft
	  Systems Management Server Administrator's Guide or online Help.
	
	- Specify a different site as the senior site. The criteria for selecting the
	  site should be:
	
	   - The site server does not have direct SMS Sender site-to-site connectivity
	     with any other site that is hosted on a Windows NT-based or Windows
	     2000-based domain controller.
	
	   - The site server is centrally located on the wide area network (WAN) and
	     has reliable communications with all of the domain controllers in the
	     domain that are specified as SMS logon points.
	
	For additional information about configuring a site as the senior site, click the
	article number below to view the article in the Microsoft Knowledge Base:
	
	  Q235726 SMS: How to Specify Senior Site for WinNT Logon Point Management in a
	  Single Domain with Multiple Sites
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200 
	Technology        : kbSMSSearch kbSMS200
	Version           : :2.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
