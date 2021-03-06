---
layout: page
title: "Q175935: NBTSTAT -A May Return Host not Found Error Message"
permalink: /kb/175/Q175935/
---

## Q175935: NBTSTAT -A May Return Host not Found Error Message

{% raw %}

	Article: Q175935
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kberrmsg kbnetwork
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you run a "Nbtstat -A" command to get a computer's NetBIOS name, you may
	receive the following error message:
	
	  Host not found.
	
	For example:
	
	  nbtstat -A a.b.c.d
	
	Where a.b.c.d is the IP address of the target computer. The expected result is
	the NetBIOS Remote Machine Name Table from the target computer.
	
	CAUSE
	=====
	
	The NetBIOS Interface device on the target computer is not started.
	
	RESOLUTION
	==========
	
	To resolve this issue, verify that the NetBIOS Interface device is set to start
	either Automatically or Manually and that the Messenger service is set to start
	Automatically. Perform the following steps on the target computer:
	
	1. Click the Start button, point to Settings, and then click Control Panel.
	
	2. Double-click the Services icon, and select the Messenger service.
	
	3. Click Startup, click Automatic, click OK, and then click Close.
	
	4. Double-click the Devices icon in Control Panel, and select the NetBIOS
	  Interface device.
	
	5. Click Startup, click either Automatic or Manual, click OK, and click Close.
	
	6. Restart the computer.
	
	NOTE: Simply starting the NetBIOS Interface device is not sufficient. The NetBIOS
	Interface device must be reset by a NetBIOS application such as the Messenger
	service.
	
	MORE INFORMATION
	================
	
	The Nbtstat.exe utility, when used with the parameters "-A <IpAddress>",
	sends a Node Status Request directly to the given IP address:
	
	  NBT: NS: Query req. for *<00...(15)>
	
	and receives the NetBIOS name from the Node Status Response:
	
	  NBT: NS: Query (Node Status) resp. for *<00...(15)>, Success
	
	This request is handled on the target computer by the NetBIOS Interface device
	(Netbios.sys). By default, the startup of this device is set to Manual so that
	it is only started on demand. The Messenger service (which is started
	Automatically), is by default the only service shipped with Windows NT that
	relies on the NetBIOS Interface device. Therefore, if the Messenger service is
	Disabled or not started, then the NetBIOS Interface device is not started and
	causes this issue.
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
