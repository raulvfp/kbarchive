---
layout: page
title: "Q269439: XADM: Synchronization of .ost Files Won't Work w. Antivirus API"
permalink: /kb/269/Q269439/
---

## Q269439: XADM: Synchronization of .ost Files Won't Work w. Antivirus API

{% raw %}

	Article: Q269439
	Product(s): Microsoft Exchange
	Version(s): 5.5 SP3
	Operating System(s): 
	Keyword(s): exc55sp3
	Last Modified: 22-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 SP3 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	If Exchange clients attempt to synchronize the .ost files when third-party
	software that uses the new antivirus application programming interface (API) is
	installed on the Exchange Server computer, the clients may experience slow
	synchronization, synchronization time-outs, or inability to complete the
	synchronization process.
	
	CAUSE
	=====
	
	This issue can occur because when the antivirus API is in use, each message that
	contains an attachment must be scanned before the message is released to a
	client by the Exchange Server information store. If the scanning queue contains
	messages that contain many attachments or several large attachments, the client
	may time out while it waits for the server to release the message that contains
	the attachment.
	
	RESOLUTION
	==========
	
	To determine whether you are experiencing the issue that is described in this
	article, disable the antivirus API by either disabling the third-party software
	or changing the Enable value in the registry. To change the Enable value, you
	need to edit the registry:
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	WARNING: When you disable the antivirus API and subsequently re-enable the
	antivirus API, all attachments are resubmitted to the third-party software to be
	scanned.
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate the Enabled value under the following key in the registry:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSExchangeIS\VirusScan
	
	3. On the Edit menu, click DWORD, type "0" (without the quotation marks), and
	  then click OK.
	
	4. Quit Registry Editor.
	
	After you change the Enabled value, allow up to two minutes for the change to
	take effect, and then test .ost synchronization.
	
	If .ost synchronization finishes normally, re-enabled the antivirus API by
	changing the Enabled value back to "1" (without the quotation marks).
	
	Although the performance of the antivirus API is bound by the third-party
	software implementation, you can add or change the OpenRetryDelay value in the
	registry to try to resolve this issue. This value is the time interval in
	milliseconds that the information store pauses before it attempts to reopen
	attachments that are currently being scanned when those attachments are
	requested by the client. If you set this value too high, you may cause client
	time-outs, and if you set this value too low, you may cause additional
	processing overhead by the information store. If this value is not present in
	the registry when the antivirus API is in use, it has a hard-coded default value
	of 500 milliseconds.
	
	IMPORTANT: Although the following procedure uses a value of 250 milliseconds,
	this value may not be the correct value in every case. Choose this value based
	upon your particular environment.
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate the following key in the registry:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSExchangeIS\VirusScan
	
	If the VirusScan key is not present, the antivirus API is not in use or has never
	been enabled on the Exchange Server computer.
	
	3. Locate the OpenRetryDelay value under the preceding key in the registry. If
	  the OpenRetryDelay value is not present, go directly to step 5.
	
	4. On the Edit menu, click DWORD, type "250" (without the quotation marks),
	  select a Radix of Decimal, and then click OK.
	
	5. If the OpenRetryDelay value is not present, add it; on the Edit menu, click
	  Add Value, and then add the following registry value:
	
	  Value Name: OpenRetryDelay
	  Data Type: REG_DWORD
	  Radix: Decimal
	  Value: 250
	
	6. Quit Registry Editor.
	
	7. Restart the information store service to make the changes take effect.
	
	If you do not notice any improvement after you change this value, contact the
	third-party software representative for assistance in further improving
	performance of the antivirus scanning process.
	
	Additional query words: Anti-Virus AVAPI Sync timeout vapi
	
	======================================================================
	Keywords          : exc55sp3 
	Technology        : kbExchangeSearch kbZNotKeyword2 kbExchange550SP3
	Version           : :5.5 SP3
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
