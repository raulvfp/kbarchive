---
layout: page
title: "Q148367: Possible Network File Damage with Redirector Caching"
permalink: /kb/148/Q148367/
---

## Q148367: Possible Network File Damage with Redirector Caching

{% raw %}

	Article: Q148367
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 
	Operating System(s): 
	Keyword(s): kbfile kbnetwork win95 kbgraphxlinkcritical
	Last Modified: 11-JUN-2002
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use the Microsoft Client for Microsoft Networks, a file on a Microsoft
	networking server (such as a Microsoft Windows NT, Windows 95, Microsoft Windows
	for Workgroups, or Microsoft LAN Manager server) may become damaged or may
	contain invalid data if multiple workstations access the file at the same time.
	
	CAUSE
	=====
	
	The network redirector (Vredir.vxd) caches data locally for files it accesses on
	a Microsoft networking server. If the file size does not change or if the last
	modified time does not change within a two-second period, the redirector reads
	file data from the locally stored cache rather than from the file on the server.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	This issue is resolved by the following updated file for Windows 95:
	
	  VREDIR.VXD version 4.00.1112 (dated 2/11/97) and later
	
	The following file is available for download from the Microsoft Download Center:
	
	  Download Vredrupd.exe now
	  (http://download.microsoft.com/download/win95upg/vredir/1/W95/EN-US/vredrupd.exe)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. After it is posted, the file is housed on
	secure servers that prevent any unauthorized changes to the file.
	
	
	This update resolves this issue by disabling caching on all FileOpen calls only
	if the following binary value is present in the registry:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\VxD\VREDIR
	  Value Name: DiscardCacheOnOpen
	  Value: 01 00 00 00
	
	If this value is not present or is set to 0, this update behaves the same as
	Vredir.vxd versions 4.00.955 and earlier.
	
	This value is not added by default and must be added manually in order to disable
	caching when opening files.
	
	STATUS
	======
	
	This issue is resolved in Microsoft Windows 98.
	
	MORE INFORMATION
	================
	
	For additional information about issues resolved by updates to this component,
	please see the following articles in the Microsoft Knowledge Base:
	
	  Q172594 Cannot Connect to Server with 15 Characters and Period in Name
	
	  Q165402 Windows 95 Update to Encrypt Passwords in Memory
	
	  Q161100 File May Be Truncated When Copied to a Full Network Drive
	
	  Q157114 "Access Denied" Attempting to Run File on LM/X Server
	
	  Q152186 Possible Network Data Corruption If Locking Not Used
	
	  Q142803 Hang or Locking Error Accessing Database Files Over Network
	
	  Q140558 Deleting Files on Samba Servers May Delete Local Files Instead
	
	  Q138249 Updated Vredir.vxd Corrects Errors Running Files on LMX
	
	  Q160807 Cannot Connect to Windows NT Server with Many Shares
	
	  Q150215 Disabling Automatic Network Shortcut Resolution
	
	  Q138014 File May Be Truncated to Zero Bytes When Copied Onto Itself
	
	  Q136834 Error Copying Read-Only Files to Core SMB Server
	
	Additional query words: corrupt w95cn
	
	======================================================================
	Keywords          : kbfile kbnetwork win95 kbgraphxlinkcritical 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
