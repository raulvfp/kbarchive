---
layout: page
title: "Q235210: SMS: Site Unable to Remove CAP"
permalink: /kb/235/Q235210/
---

## Q235210: SMS: Site Unable to Remove CAP

{% raw %}

	Article: Q235210
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0,2.0 SP1,2.0 SP2,2.0 SP3
	Operating System(s): 
	Keyword(s): kbsetup kbConfig kbMMC kbServer kbsms200 kbsms200bug kbCAP kbSiteComp kbsmsAdmin kbStat
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1, 2.0 SP2, 2.0 SP3 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	You cannot successfully remove or reinstall a Client Access Point (CAP) and the
	CAP server eventually reports critical system status. You view messages for the
	SMS_SITE_COMPONENT_MANAGER service in the Component Status folder, and see
	messages similar to the following:
	
	  SMS Site Component Manager failed to deinstall all SMS server components from
	  site system "\\servername".
	
	  SMS Site Component Manager failed to reinstall this component on this site
	  system.
	
	If logging is enabled for the SMS_SITE_COMPONENT_MANAGER service, entries similar
	to the following are found in the Sms\Logs\Sitecomp.Log file:
	
	  Starting service SMS_SERVER_BOOTSTRAP_RIVIERA with command-line arguments
	  "RE0 E:\SMS /deinstall \\LUXOR\E$\SMS\bin\i386\smsexecd.exe"...
	  Execution of "\\LUXOR\E$\SMS\bin\i386\smsexecd.exe /deinstall
	  /siteserver:RIVIERA" on server LUXOR failed: The file
	  "\\LUXOR\E$\SMS\bin\i386\smsexecd.exe" does not exist.
	  Bootstrap operation failed.
	  Deinstalled service SMS_SERVER_BOOTSTRAP_RIVIERA.
	  Bootstrap operations aborted.
	  Deinstallation failed and will be retried in the next polling cycle.
	
	  Could not start service SMS_SERVER_BOOTSTRAP_LUXOR. The operating system
	  reported error 997: Overlapped I/O operation is in progress.
	  Bootstrap operation failed.
	
	If you attempt to reinstall the CAP at this point, the sitecomp.log may show
	errors similar to the following:
	
	  Installed service SMS_SERVER_BOOTSTRAP_SERVERNAME.
	  Starting service SMS_SERVER_BOOTSTRAP_SERVERNAME with command-line arguments
	  "TOP E:\SMS /deinstall \\SERVERNAME\E$\SMS\bin\i386\smsexecd.exe"...
	  Execution of "\\SERVERNAME\E$\SMS\bin\i386\smsexecd.exe /deinstall
	  /siteserver:SERVERNAME" on server SERVERNAME failed: Win32 GetShortPathName()
	  failed for path "\\SERVERNAME\E$\SMS\bin\i386\smsexecd.exe". Win32
	  GetLastError() returned error 2.
	  Bootstrap operation failed.
	  Deinstalled service SMS_SERVER_BOOTSTRAP_SERVERNAME.
	  Bootstrap operations aborted.
	  Deinstallation failed and will be retried in the next polling cycle.
	
	CAUSE
	=====
	
	If the SMS folder (or any of its subfolders or files) has been removed from the
	CAP server, the SMS site component manager may be unable to deinstall (remove)
	or reinstall the CAP properly.
	
	Specifically, Site Component Manager cannot find the Smsexecd.exe file on the CAP
	server. The Smsexecd.exe is used by the SMS Server Bootstrap to reinstall or
	remove the SMS Executive service on the CAP. If this file is not found on the
	CAP, the bootstrap service is unable to complete removal or installation of the
	CAP.
	
	WORKAROUND
	==========
	
	To work around this issue, follow these steps.
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	1. If a recent backup of the SMS directory exists, restore the SMS folder to the
	  CAP. Stop and restart the SMS_SITE_COMPONENT_MANAGER service on the Site
	  Server to force a Site Component Manager update cycle.
	
	  In some cases the Site Component Manager will still be unable to remove
	  (deinstall) or reinstall the CAP. In this situation, remove the CAP role from
	  the server (if reinstallation is being attempted). The Site Component Manager
	  will attempt to remove the CAP role from the CAP server for 1440 minutes (24
	  hours), and then it will time out. After the Site Component Manager has timed
	  out, the errors will cease and you can attempt reinstallation can be
	  attempted if you want to. If a 24-hour wait is not feasible, proceed to step
	  2.
	
	2. If a 24-hour wait is not feasible, the removal timeout process can be
	  accelerated by modifying an SMS registry key.
	
	  To accelerate the CAP removal timeout, modify the following registry value:
	
	  HKLM\Software\Microsoft\SMS\Components\SMS_SITE_COMPONENT_MANAGER\Component
	  Servers\SERVERNAME\Deinstallation Start Time
	
	  Change the value of Deinstallation Start Time to 1. Stop and restart the
	  SMS_SITE_COMPONENT_MANAGER service on the Site Server to force a Site
	  Component Manager update cycle.
	
	The Site Component Manager log should indicate the deinstallation process has
	timed out as follows:
	
	  Bootstrap operation failed.
	  Deinstalled service SMS_SERVER_BOOTSTRAP_NETLKWI02.
	  Bootstrap operations aborted.
	  Deinstallation failed. Deinstall retry interval of 1440 minutes exceeded.
	  Component assumed to be deinstalled; deinstallation will not be retried.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	To enable logging for the SMS_SITE_COMPONENT_MANAGER service, follow these
	steps:
	
	1. Expand the Tools folder in the Systems Management Server Administrator
	  console for your site.
	
	2. Right-click SMS Service Manager, point to All Tasks, and then click "Start
	  SMS Service Manager".
	
	3. On the SMS Service Manager window, single-click the Components folder.
	
	  The list of services for your site is displayed in the right pane.
	
	4. Right-click the SMS_SITE_COMPONENT_MANAGER service, and then click Logging.
	
	5. Check "Logging enabled", note the "Log filename" box for the location of the
	  log, and then click OK.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsetup kbConfig kbMMC kbServer kbsms200 kbsms200bug kbCAP kbSiteComp kbsmsAdmin kbStatSum 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1 kbSMS200SP2 kbSMS200SP3
	Version           : :2.0,2.0 SP1,2.0 SP2,2.0 SP3
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
