---
layout: page
title: "Q200017: Domain Controller with 2012 Errors and Connectivity Problems"
permalink: /kb/200/Q200017/
---

## Q200017: Domain Controller with 2012 Errors and Connectivity Problems

{% raw %}

	Article: Q200017
	Product(s): Microsoft Windows NT
	Version(s): WINDOWS:95; winnt:3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	- Microsoft Windows 98 
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Your Windows NT Server computer may occasionally log the following events in the
	Event Viewer System log:
	
	  Event ID: 2012
	  Source: Srv,
	  Type: Error
	  Description: The server has encountered a network error.
	
	The event may be generated when trying to log on from Windows 95 clients, who
	will get the following error:
	
	  The domain password you supplied is incorrect or access to your logon server
	  has been denied.
	
	The event may be generated when trying to connect to the domain controller
	through Explorer or browsing through Network Neighborhood, and the response may
	be:
	
	  The network has responded incorrectly.
	
	The event may be generated when trying to print to some of the printers queued on
	the troubled domain controller, and will generate the following error:
	
	  The system call level is not correct.
	
	NOTE: You will be able to ping the IP address and NetBIOS name successfully to
	and from the server displaying Event ID 2012.
	
	CAUSE
	=====
	
	The following situations can cause these symptoms:
	
	- Your network interface card (NIC) may not be functioning correctly.
	
	- You may have an outdated or incompatible NIC.
	
	RESOLUTION
	==========
	
	To resolve this problem, do either of the following:
	
	- Replace the NIC on the server that is having the Event ID 2012 errors.
	
	- Contact the manufacturer of the NIC and get an updated driver.
	
	MORE INFORMATION
	================
	
	Error 2012 in the Event Viewer, in general, indicated there is a connectivity
	problem. It is advised to go through the normal connectivity troubleshooting
	steps:
	
	1. If the client is receiving one of the above error messages, a quick test to
	  rule out something on the client side causing the problem would be to pause
	  the NetLogon service on a domain controller with the 2012 errors. If the
	  client is able to log on to another domain controller successfully, then the
	  problem has been isolated to the server.
	
	2. Check for the IPX protocol and the Btrieve applications on the server. For
	  additional information, please see the following article(s) in the Microsoft
	  Knowledge Base:
	
	  Q195641 Btrieve, IPX, and Event ID 2012
	
	3. Replace the network interface card (NIC) on the server with the Event ID 2012
	  errors. The faulty NIC may be any variety of Token Ring or Ethernet.
	
	4. Review the Windows NT Hardware Compatibility List (HCL) to ensure that the
	  NIC in the computer is on the HCL. If the card is not on the HCL, replace it
	  with an HCL-compatible NIC.
	
	5. Another known cause of connectivity problems is that the NIC driver may be
	  outdated. Obtaining an updated driver from the manufacturer may resolve the
	  issue.
	
	6. The problem has also been seen with network switch problems that may be
	  preventing the connectivity on an intermittent basis. Resetting the network
	  switch may resolve the issue. Contact the switch manufacturer for detailed
	  information on resetting your network switch.
	
	For additional information, please see the following article(s) in the Microsoft
	Knowledge Base:
	
	  Q195641 Btrieve, IPX, and Event ID 2012
	
	  Q125218 Madge Smart 16/4 AT Plus Ringnode Token Ring Adapter Fails
	
	  Q193839 Explanation of "Status Buffer Overflow" Error
	
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search kbWin95search kbWin98search kbZNotKeyword3 kbWin98
	Version           : WINDOWS:95; winnt:3.5,3.51,4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
