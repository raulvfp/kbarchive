---
layout: page
title: "Q214597: Cannot Run Office in Maintenance Mode After Using Sysprep"
permalink: /kb/214/Q214597/
---

## Q214597: Cannot Run Office in Maintenance Mode After Using Sysprep

{% raw %}

	Article: Q214597
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-AUG-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	On a system that was created from an image of Windows NT and Microsoft Office
	where Sysprep was applied, Office will not run in maintenance mode. To run
	Office in maintanance mode, double-click the Add/RemovePrograms icon in Control
	Panel and select Microsoft Office 97. The system may show an error message about
	a corrupted .stf file and fail to run.
	
	CAUSE
	=====
	
	This problem is caused by the Sysprep file Psydo957.dll changing the Product ID
	in the Office 97 .stf file.
	
	RESOLUTION
	==========
	
	To work around this problem, before you run Sysprep on the master system, remove
	the Psydo957.dll file from the directory containing the System Preperation tool
	files. Without this file, Sysprep will not change the Product ID in Office 97.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.0.
	
	
	MORE INFORMATION
	================
	
	Sysprep refers to the System Preparation Tool for Winnt 4.0. This tool can be
	used in conjunction with third-party tools that copy the opperating system and
	application files from one system to another, to create a duplicate
	installation.
	
	For additional information, please see the following article(s) in the Microsoft
	Knowledge Base:
	
	  Q195446 How Customers Can Obtain System Preparation Tool for WinNT 4.0
	
	Additional query words: Sysprep Sysclone
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400xsearch kbWinNTSsearch kbWinNTS400xsearch kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
