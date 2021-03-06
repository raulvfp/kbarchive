---
layout: page
title: "Q181630: SMS: Stranded TMP Files on Logon Servers"
permalink: /kb/181/Q181630/
---

## Q181630: SMS: Stranded TMP Files on Logon Servers

{% raw %}

	Article: Q181630
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): kbInventory smsinv
	Last Modified: 25-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Several TMP files exist on the Microsoft Systems Management Server logon servers
	in the Logon.srv\Inventry.box subdirectory. These TMP files may have an old time
	stamp and may appear to be stranded files.
	
	MORE INFORMATION
	================
	
	Normally TMP files are created by Systems Management Server client computers on
	logon servers. When taking the client's inventory, the Inventory Agent component
	running on Systems Management Server client computers creates these TMP files on
	the logon server in the Logon.srv\Inventry.box subdirectory. After the inventory
	process is completed the TMP files should be renamed with the RAW file name
	extension. If clients only have Add and Read permissions to this directory and
	not Change permissions, the TMP file is not renamed with the RAW extension and
	is stranded.
	
	WORKAROUND
	==========
	
	To work around this issue, ensure that all Systems Management Server clients
	(Everyone) has the default Change permissions at the directory level for all the
	logon server's Logon.srv\Inventry.box subdirectory.
	
	Please refer to the "BackOffice Resource Kit 1", Chapter 1, page 27 for a
	complete list of default directory permissions.
	
	If you have old stranded TMP files on your logon servers, you can move them to a
	temporary location and delete them later, if they are still not required.
	Restart the Systems Management Server Executive service on the site server after
	moving these files, so that the Maintenance Manager thread is restarted.
	
	The Systems Management Server Maintenance Manager service monitors all the logon
	server's Logon.srv\Inventry.box subdirectory for RAW files and moves them to the
	site server's Site.srv\Inventry.box subdirectory. Sometimes the Maintenance
	Manager service may seem to stop responding if there are several thousand .TMP
	files in the Logon.srv\Inventry.box subdirectory.
	
	This problem may also occur when network connectivity problems exist between the
	clients' computer and its logon server. This causes the inventory agent to start
	the inventory process, create a TMP file, and then disconnect because of the
	network problem which leaves the 0 byte TMP file stranded. The inventory agent
	loops through this process over and over again, thereby causing many TMP files
	to be created (usually with a 0 byte size) and then stranded in the
	Logon.srv\Inventry.box subdirectory.
	
	Additional query words: WinNT smsinv smsmaintman hang hung stop halt
	
	======================================================================
	Keywords          : kbInventory smsinv 
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
