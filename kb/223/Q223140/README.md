---
layout: page
title: "Q223140: SMB Size Negotiation When Copying Files with Windows NT Explorer"
permalink: /kb/223/Q223140/
---

## Q223140: SMB Size Negotiation When Copying Files with Windows NT Explorer

{% raw %}

	Article: Q223140
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SUMMARY
	=======
	
	When you copy or move a file, the negotiated Server Message Block (SMB) size is
	different. The block size depends on a number of factors including:
	
	- Whether Windows NT Explorer or an MS-DOS command prompt is used to issue the
	  command.
	
	- Which direction the file is being moved or copied to (that is, copying a file
	  from your computer to another computer versus your computer copying a file
	  from another computer back to your own computer.)
	
	When you use Windows NT Explorer to copy a file from the client to a remote
	computer, data is typically transfered in Core mode in 4 KB blocks.
	
	When you use Windows NT Explorer to copy a file from the remote computer back to
	the client, data is typically transfered in Raw mode in 60 KB blocks.
	
	When you use an MS-DOS command prompt command to copy a file in either direction,
	data is generally transfered in Raw mode. Because Raw mode typically uses a
	60-64 KB transfer rate, and Core mode typically uses 4 KB, a Raw-mode transfer
	is faster.
	
	MORE INFORMATION
	================
	
	The factors listed below determine which transfer mode is chosen. However, in
	this example, what's happening is not getting exclusive use of the Virtual
	Circuit (VC), which is created when setting up the connection between the two
	computers. When you cut or copy a file in Windows NT Explorer, make a folder, or
	perform some other file system changes, Windows NT Explorer will show that
	change quickly by updating the display. The update in the display is triggered
	by a call called ChangeNotify.
	
	When copying a file to a remote computer, a long distance ChangeNotify call is
	triggered. This call goes over the network. This call also prevents getting
	exclusive use of the VC to copy the file. When copying a file from a remote
	computer back to the client (command issued locally), the ChangeNotify call is
	still triggered, but it's now a local call. So the call is not sent over the
	wire, therefore, the copy operation gets exclusive use of the VC.
	
	Because ChangeNotify is not called for to copy or move a file when you use an
	MS-DOS command prompt command, these transfers typically use Raw mode.
	
	From the specifications for Core versus Raw mode data transfers:
	
	  The Windows NT redirector has the following requirements for performing raw
	  mode I/O, all of which must be satisfied for raw mode I/O to occur.
	
	- The Server Message Block (SMB) protocol negotiated between the client and
	  server must support Raw mode.
	
	- The server must be configured to support Raw mode.
	
	- The client redirector must be configured to allow Raw mode.
	
	- No other SMB requests are pending on the same Virtual Circuit (VC).
	
	- The I/O is not on a blocking named pipe.
	
	- For a READ request: the requested data size is equal to or greater than 2
	  times the currently configured request buffer size, and the read offset is
	  not past the redirector's currently configured end-of-file.
	
	- For a WRITE request: the requested data size is equal to or greater than 1.5
	  times the currently configured request buffer size, and the write offset is
	  not more than approximately 1 MB past the current end-of-file.
	
	- The I/O is to take no longer than 5 seconds to complete."
	
	Core Mode Data Transfer:
	
	When writing data in Core mode, as in file copy to a remote server, size of data
	blocks transferred is 4KBytes by default. This can be modified using the
	following registry parameter on the remote server side.
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	To increase the buffer size, edit the SizReqBuf registry value using the
	following steps:
	
	1. Start Registry Editor (Regedt32.exe or Regedit.exe).
	
	2. Go to the following registry subkey:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services \LanmanServer\Parameters
	  NOTE: The above registry key is one path; it has been wrapped for
	  readability.
	
	3. Create the SizReqBuf value using the following information:
	
	  Value Name: SizReqBuf
	  Data Type : REG_DWORD
	  Data      : 512 - 65536 (bytes in decimal)
	  Default   : 4096
	
	  NOTE: Small buffers use less memory and large buffers can improve performance.
	  The exact value that works best in a given environment will depend on the
	  specific configuration of that environment, but 14596 is a value that has
	  been shown to work well in a fairly standard Ethernet environment. Setting
	  this parameter to the maximum value will make server to transfer data in 60
	  KB blocks.
	
	4. Close Registry Editor and restart the Server service.
	
	REFERENCES
	==========
	
	  Q152081 Use of Raw Data Transfer Mode Influenced by Application
	
	Additional query words: data transfer raw core SMB negotitate slow
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
