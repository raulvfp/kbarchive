---
layout: page
title: "Q103704: How to Change a Windows NT Computer Name in an NT AS Domain"
permalink: /kb/103/Q103704/
---

## Q103704: How to Change a Windows NT Computer Name in an NT AS Domain

{% raw %}

	Article: Q103704
	Product(s): Microsoft Windows NT
	Version(s): 3.1 3.5 3.51
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.1 
	- Microsoft Windows NT Workstation version 3.1 
	- Microsoft Windows NT Advanced Server, version 3.1 
	- Microsoft Windows NT Workstation versions 3.5, 3.51 
	- Microsoft Windows NT Server versions 3.5, 3.51 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	If you have a Windows NT workstation in a Windows NT Advanced Server domain and
	you want to change the machine's computer name, the machine must leave the
	domain and rejoin the domain in order for the change to take effect.
	
	MORE INFORMATION
	================
	
	Pages 151-152 in the Windows NT "System Guide" instruct you to change a Windows
	NT workstation's computer name as follows:
	
	1. Have the Windows NT Advanced Server domain administrator create an account
	  for the new computer name.
	
	2. In the Network Settings dialog box, choose the Change button next to the
	  computer name.
	
	3. In the Computer Name dialog box, type a unique name (the new name) for the
	  computer, and choose OK.
	
	This procedure results in your Windows NT workstation being unable to log on in
	the Windows NT Advanced Server domain with any user account. (It makes no
	difference if the Windows NT Advanced Server domain administrator creates the
	computer name before or after the computer name change.)
	
	If you find that you are unable to log on in an Windows NT Advanced Server domain
	after a name change, you should log on to your local database as an admin user.
	Next, leave the Windows NT Advanced Server domain by either joining another
	Windows NT Advanced Server domain or by selecting any workgroup. After you
	reboot the system, your machine can rejoin the original domain with the new
	computer name; you will be correctly prompted with the "WELCOME TO THE
	<original domain> DOMAIN" message.
	
	NOTE: You cannot add the new computer name for the Windows NT workstation in the
	domain by reentering the current domain name and providing an Admin account for
	the domain. The machine must leave and rejoin the domain.
	
	Step-by-Step Instructions for Changing a Computer Name on a 
	Windows NT Workstation in a Windows NT Advanced Server Domain
	--------------------------------------------------------------------------------------------------------------------------
	
	1. Create a new machine account for the Windows NT workstation in the Windows NT
	  Advanced Server domain.
	
	2. Choose the Network icon in Control Panel, choose the Change button next to
	  the current domain name, and enter any workgroup name or the name of another
	  Windows NT Advanced Server domain.
	
	  NOTE: If you choose another Windows NT Advanced Server domain, you will need
	  an administrator of that domain to create a machine account for you in Server
	  Manager or you will need to provide an admin account and password so that you
	  can add the machine account to the Windows NT Advanced Server domain.
	
	3. Choose the Network icon in Control Panel and change the computer name of the
	  Windows NT workstation to the new name.
	
	  NOTE: Once a computer name is changed, the Change button for the domain named
	  is dimmed, which indicates that you cannot change the computer name and the
	  domain name at the same time unless you change the domain name first, as
	  indicated by the order of steps 2 and 3.
	
	4. When prompted, reboot the system in order for the domain name and computer
	  name changes to take affect.
	
	5. Log on to the local machine with Admin privileges.
	
	6. Choose the Network icon in Control Panel, choose the Change button next to
	  the domain name, and enter the original domain name.
	
	  NOTE: In step 1, you created a new machine account, and as a result, you will
	  not need to provide a valid administrator and password for the original
	  domain.
	
	  You will receive the "WELCOME TO THE <original domain> DOMAIN" message.
	
	7. When prompted, reboot the system so that the domain name change can take
	  effect.
	
	You should now be able to log on to the Windows NT Advanced Server domain with
	any valid account.
	
	Additional query words: prodnt rename
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTW310 kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbWinNTS310 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS351search kbWinNTS350search kbWinNTS310search kbWinNT310Search kbWinNTW310Search
	Version           : 3.1 3.5 3.51
	
	=============================================================================
	

{% endraw %}
