---
layout: page
title: "Q248880: SMS:SMSCliToknAcct&amp; Accesses Network on Computer w/ Auddrive.sys"
permalink: /kb/248/Q248880/
---

## Q248880: SMS:SMSCliToknAcct&amp; Accesses Network on Computer w/ Auddrive.sys

{% raw %}

	Article: Q248880
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0,2.0 SP1
	Operating System(s): 
	Keyword(s): kbinterop kbClient kbConfig kbSecurity kbsms200 kbsms200bug kbsms200sp2fix
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Systems Management Server (SMS) 2.0 Service Pack 1 (SP1) Windows NT clients may
	experience "SMSCliToknAcct&" account lockout issues with the installation of
	certain audio drivers. Disabling the audio driver and restarting the computer
	may resolve the problem.
	
	CAUSE
	=====
	
	These problems can be caused by the SMSCliToknAcct& account being used in
	the background by a client component such as the Hardware Inventory Agent when
	the audio driver initializes or needs to perform a function. Some audio drivers
	are designed to use the currently active account which will usually be the
	"logged on user" account.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Systems Management
	Server version 2.0. For additional information, click the following article
	number to view the article in the Microsoft Knowledge Base:
	
	  Q236325 How to Obtain the Latest Systems Management Server 2.0 Service Pack
	
	WORKAROUND
	==========
	
	To work around this problem, use any of the following methods:
	
	Remove the Audio Driver
	-----------------------
	
	This will remove Auddrive.sys from the computer.
	
	1. On the Devices tab of the Multimedia applet in Control Panel, expand Audio
	  Devices.
	
	2. Select AUDDRIVE, and then click the Remove button at the bottom of the
	  Multimedia Properties window.
	
	Disable the Audio Driver
	------------------------
	
	This will remove Auddrive.sys and its supporting DLL. A restart is required after
	the removal.
	
	1. In the Devices applet, select AUDDRIVE, and then click the Startup button.
	
	2. On the Devices screen, select Disabled as the Startup Type.
	
	Use USER PATH Environment Variable
	----------------------------------
	
	Place the network paths in the USER PATH environment variable rather than the
	SYSTEM PATH environment variable.
	
	1. Right-click My Computer, and then click Properties (or double-click the
	  System applet in Control Panel).
	
	2. Click the Environment tab. In the upper box, labeled Systems Variables, find
	  any UNC paths (\\servername\share), and move them to the lower box marked
	  "User Variables for Administrator".
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 2.0. This problem was first corrected in Systems Management Server
	version 2.0 Service Pack 2.
	
	
	Additional query words: prodsms wav audio driver smsclitokacct HINV32 HINV
	
	======================================================================
	Keywords          : kbinterop kbClient kbConfig kbSecurity kbsms200 kbsms200bug kbsms200sp2fix 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1
	Version           : winnt:2.0,2.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
