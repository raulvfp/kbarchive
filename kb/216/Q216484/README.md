---
layout: page
title: "Q216484: Alternate Way to Install Application During GUI-mode Setup"
permalink: /kb/216/Q216484/
---

## Q216484: Alternate Way to Install Application During GUI-mode Setup

{% raw %}

	Article: Q216484
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbOPK kbSBK
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	There are different ways to install applications during the graphical user
	interface (GUI) portion of Windows NT 4.0 in a deployment situation. The
	Deployment Guide covers using the Cmdlines.txt or the /E parameter, but there is
	a third option that can be used in the answer file.
	
	The Deployment Guide is available at:
	
	  http://www.microsoft.com/windows/downloads/bin/ntw/depguide.exe
	
	MORE INFORMATION
	================
	
	To have a application run during the GUI portion of Setup, such as a service
	pack, insert the following parameter into the answer file (Unattend.txt):
	
	     [SetupParams]
	     Userexecute="c:\sp4\update.exe"
	
	This assumes that the Service Pack has been downloaded to the distribution share
	in the i386\$oem$\c\sp4\ folder. When the unattended installation is started,
	Windows NT Setup will then create the directory path and copy the files to the
	target computer.
	
	The command on this line runs after the video detection runs. You can run more
	than one application by specifying a batch file to be run, and then specify
	multiple applications with in it.
	
	For additional information about how to install service packs in a deployment,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q168814 Installing WinNT 4.0 Service Packs During Unattended Install
	
	For additional information about other parameters in the answer file, please see
	the following article in the Microsoft Knowledge Base:
	
	  Q155197 Unattended Setup Parameters for Unattend.txt File
	
	Additional query words: Unattended Setup Install
	
	======================================================================
	Keywords          : kbOPK kbSBK 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
