---
layout: page
title: "Q79052: Reference to NetAsyncSwithching in NETWORKS.TXT"
permalink: /kb/079/Q79052/
---

## Q79052: Reference to NetAsyncSwithching in NETWORKS.TXT

{% raw %}

	Article: Q79052
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.0,3.0a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 14-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.0, 3.0a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The NETWORKS.TXT document file included with Windows 3.0 refers to the
	NetAsyncSwitching statement. This statement is supposed to go under the
	[Standard] section in the SYSTEM.INI file; however, there is no explanation for
	this command in the SYSINI.TXT file.
	
	This information applies to Microsoft Windows versions 3.0 and 3.0a. This does
	not apply to later versions of Windows.
	
	
	MORE INFORMATION
	================
	
	The following explains NetAsyncSwitching.
	
	NetAsynchSwitching=<0 or 1>
	Default: 0
	Purpose: Indicates whether Windows will allow you to switch away from an
	        application (running in standard mode) after it has made an
	        asynchronous network BIOS call. The default value of 0
	        specifies that task switching is not allowed. Switching away
	        from some applications that make these calls might cause
	        your system to fail. Once Windows detects an asynchronous
	        NetBIOS call, it will not allow switching from the application
	        even if no more of these calls are made. Set this value to 1 if
	        you are sure the applications you use will not receive network
	        messages while they are not active.
	
	To change: Use Notepad to edit the SYSTEM.INI file.
	
	Additional query words: 3.00 3.00a 3.0 3.0a novell networks win30 docerr
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin300 kbWin300a
	Version           : WINDOWS:3.0,3.0a
	
	=============================================================================
	

{% endraw %}
