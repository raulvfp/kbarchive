---
layout: page
title: "Q174871: Printer Shares Lost after Changing Server Name"
permalink: /kb/174/Q174871/
---

## Q174871: Printer Shares Lost after Changing Server Name

{% raw %}

	Article: Q174871
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): kbnetwork kbprint kbWinNT400sp4fix
	Last Modified: 07-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 SP3 
	- Microsoft Windows NT Server version 4.0 SP3 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it
	if a problem occurs. For information on how to do this, view the "Restoring
	the Registry" online Help topic in Regedit.exe or the "Restoring a Registry
	Key" online Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	After you rename a print server, the shared printers no longer appear when You
	use NET VIEW at the command prompt. You may also receive the following error
	message when using the NET USE command to connect to the shared printer:
	
	  Error 53: The computer name specified in the network path cannot be located.
	
	CAUSE
	=====
	
	Windows NT Service Pack 3 began writing the full Universal Naming Convention
	(UNC) name of the printer in the registry. When you change the name of the
	server, Windows NT does not update the registry and the printer shares no longer
	appear.
	
	RESOLUTION
	==========
	
	Use one of the following methods to work around this problem:
	
	Method 1
	--------
	
	Update the registry to reflect the new UNC name of the print server.
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it.
	
	1. Start Registry Editor (Regedt32.exe) and select the following subkey:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CURRENTCONTROLSET\SERVICES\LANMANSERVER
	  \SHARES
	
	  NOTE: The above registry key is one path; it has been wrapped for readability.
	
	2. Double-click any of the printers listed under the Shares key to open the Data
	  dialog box.
	
	3. Update the Path setting to reflect the new UNC name of the server.
	
	4. Close Registry Editor.
	
	Method 2
	--------
	
	1. Click the Start button, point to Settings, and then click Control Panel.
	  Double-click the Printers folder.
	
	2. Right-click the shared printer and select Sharing.
	
	3. Click Not Shared and then click OK.
	
	4. Right-click the printer again and select Sharing.
	
	5. Click Shared and then click OK.
	
	The printer share should now be available to remote users and the NET VIEW and
	NET USE commands should work properly.
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0 or
	Windows NT Server 4.0, Terminal Server Edition. For additional information,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0 and Windows NT
	Server 4.0, Terminal Server Edition. This problem was first corrected in Windows
	NT 4.0 Service Pack 4.0 and Windows NT Server 4.0, Terminal Server Edition
	Service Pack 4.
	
	Additional query words: Netview browse browsing share
	======================================================================
	Keywords          : kbnetwork kbprint kbWinNT400sp4fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400search kbWinNT400search kbWinNTW400sp3 kbWinNTSsearch kbWinNTS400sp3 kbWinNTS400search kbNTTermServ400 kbNTTermServSearch
	Version           : WinNT:4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
