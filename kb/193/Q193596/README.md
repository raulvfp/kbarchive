---
layout: page
title: "Q193596: RASMAN Registry Values Cannot Be Set Higher Than 0xFF"
permalink: /kb/193/Q193596/
---

## Q193596: RASMAN Registry Values Cannot Be Set Higher Than 0xFF

{% raw %}

	Article: Q193596
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): kbWinNT400sp4fix
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Your server running both Windows NT version 4.0 and the Remote Access Service
	(RAS) may receive the following event in Event Viewer:
	
	  Event ID: 20051
	  Source: RAS
	  Type: Error
	  Description: Using the default value for Registry parameter
	               RestartTimer because the value given is not in the legal
	               range for the parameter.
	
	This happens when the following registry settings have been set to higher that
	0xFF:
	
	The following registry parameters can be found under:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Rasman\PPP
	
	     RestartTimer
	     MaxConfigure
	     MaxFailure
	     MaxReject
	     MaxTerminate
	
	The resource kit documentation states that values under the registry key
	mentioned above can be set as high as 0xFFFFFFFF. The product documentation
	states this value as unlimited. The maximum is actually 0xFF.
	
	RESOLUTION
	==========
	
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
	
	======================================================================
	Keywords          : kbWinNT400sp4fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch
	Version           : WinNT:4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
