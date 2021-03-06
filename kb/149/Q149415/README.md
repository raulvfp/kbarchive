---
layout: page
title: "Q149415: Group Policies Are Not Recognized with MSNDS"
permalink: /kb/149/Q149415/
---

## Q149415: Group Policies Are Not Recognized with MSNDS

{% raw %}

	Article: Q149415
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 
	Operating System(s): 
	Keyword(s): win95
	Last Modified: 25-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry. Before you edit the registry, you should first make a backup copy of the registry files (System.dat and User.dat). Both are hidden files in the Windows folder.
	
	SYMPTOMS
	========
	
	After you install the Microsoft Service for NetWare Directory Services (MSNDS),
	group policies may no longer work. This problem is more evident when you are
	connecting to a Novell NetWare 3.1x server.
	
	CAUSE
	=====
	
	NetWare servers require that user names be submitted in all uppercase letters.
	The MSNDS client allows you to submit your user name in lowercase or uppercase
	letters. If you enter your user name in the logon dialog box in lowercase
	letters, group policies are ignored.
	
	RESOLUTION
	==========
	
	
	STATUS
	======
	
	This problem no longer occurs in Windows 98. To resolve this problem, install
	the current version of Windows. For information about the current version of
	Windows, visit http://www.microsoft.com/windows.
	
	MORE INFORMATION
	================
	
	The following conditions must be true for group policies to work properly:
	
	1. User profiles must be enabled. To verify that user profiles are enabled,
	  follow these steps:
	
	  a. In Control Panel, double-click Passwords.
	
	  b. Click the User Profiles tab.
	
	  c. Verify that "Users can customize their preferences and desktop
	     settings..." is selected.
	
	  d. Click OK.
	
	2. The preferred server must be selected in Network properties. To verify this,
	  follow these steps:
	
	  a. In Control Panel, double-click Network.
	
	  b. Click the Configuration tab.
	
	  c. In the Primary Network Logon box, click Client For NetWare Networks.
	
	  d. In the "The following network components are installed" box, click Client
	     For NetWare Networks, and then click Properties.
	
	  e. On the General tab, verify that a preferred server is selected.
	
	  f. Click OK or Close until you return to Control Panel.
	
	  NOTE: The Config.pol file must be located in the Public folder on the
	  preferred server.
	
	3. The registry must contain the following entries:
	
	   - Registry key: HKEY_LOCAL_MACHINE\Network\Logon
	     Value name (STRING): PolicyHandler
	     Value data: GROUPPOL.DLL, ProcessPolicies
	
	   - Registry key: HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\
	     MSNP32\NetworkProvider
	     Value name (STRING): GroupFcn
	     Value data: GROUPPOL.DLL, NTGetUserGroups
	
	   - Registry key: HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\
	     NWNP32\NetworkProvider
	     Value name (STRING): GroupFcn
	     Value data: GROUPPOL.DLL, NWGetUserGroups
	
	  If any of these entries does not exist, use either of the following methods:
	
	   - Reinstall group policies from the Windows 95 CD-ROM. This replaces the
	     revised Grouppol.dll file with the original file. If you use this method,
	     make sure to copy the revised Grouppol.dll file over the original file in
	     the Windows\System folder. This is the recommended method.
	
	   - Manually edit the registry and add the missing value(s).
	
	     NOTE: For information about how to edit the registry, view the Changing
	     Keys And Values online Help topic in Registry Editor (Regedit.exe). Note
	     that you should make a backup copy of the registry files (System.dat and
	     User.dat) before you edit the registry.
	
	     WARNING: Using Registry Editor incorrectly can cause serious problems that
	     may require you to reinstall Windows 95. Microsoft cannot guarantee that
	     problems resulting from the incorrect use of Registry Editor can be
	     solved. Use Registry Editor at your own risk.
	
	
	Note that the person setting up group policies on an NDS server must also
	administer the NDS tree to supply an NDS volume and the path to a Config.pol
	file. Bindery services do not need this information because the correct location
	for the policy file is looked at automatically. NDS servers need to be told
	where the policy file is located.
	
	Additional query words: system policy
	
	======================================================================
	Keywords          : win95 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
