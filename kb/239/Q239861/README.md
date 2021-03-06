---
layout: page
title: "Q239861: SNA Server Host Print Service Supports 1,024 3270 Print Sessions"
permalink: /kb/239/Q239861/
---

## Q239861: SNA Server Host Print Service Supports 1,024 3270 Print Sessions

{% raw %}

	Article: Q239861
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0,3.0 SP1,3.0 SP2,3.0 SP3,3.0 SP4,4.0,4.0 SP1,4.0 SP2
	Operating System(s): 
	Keyword(s): kbsna300sp1 kbsna300sp2 kbsna300sp3 kbsna300sp4 sna4 kbsna400sp1 kbsna400sp2
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0 SP1, 3.0 SP2, 3.0 SP3, 3.0 SP4, 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SUMMARY
	=======
	
	The host print service (Snaprint.exe) included with SNA Server supports a
	maximum of 1,024 3270 print sessions. 3270 print sessions are limited to 1,024
	because of the threading model used by the Snaprint service. The Snaprint
	service can create a maximum of 32 threads to service the 3270 print sessions.
	Each thread can support up to 32 sessions. Thirty-two threads supporting a
	maximum of 32 sessions each yields 1,024 sessions.
	
	Each of the first 32 3270 print sessions will cause the Snaprint service to
	create a new thread. Therefore, if the Snaprint service is configured with 32
	3270 print sessions, each print session will be assigned to its own thread.
	
	Additional 3270 print sessions are assigned to the existing threads in a
	round-robin order to ensure that the sessions are balanced among the 32
	threads.
	
	For additional information about the latest service pack for SNA Server 4.0,
	click the article number below to view the article in the Microsoft Knowledge
	Base:
	
	  Q215838 How to Obtain the Latest SNA Server Version 4.0 Service Pack
	
	MORE INFORMATION
	================
	
	The limit of 1,024 3270 print sessions is also a practical limit based on
	performance testing. The following are the recommended number of print sessions
	per host print service:
	
	- Maximum simultaneously active GDI printer sessions: 240
	- Recommended maximum simultaneously active non-GDI printer sessions: 500
	
	Please refer to the Microsoft SNA Print Service White Paper
	(http://www.microsoft.com/sna/library/snaprint2.exe) for complete details on the
	performance test results.
	
	The Snaprint service has been modified to support more than 1,024 3270 print
	sessions for those customers who require more 3270 print sessions for host print
	service.
	
	CAUTION: The use of more than 1,024 print sessions should only be considered in
	environments where printing throughput is light. Use the Microsoft SNA Print
	Service White Paper (http://www.microsoft.com/sna/library/snaprint2.exe) as a
	guideline when determining if the print requirements are light. The use of more
	than 1,024 print sessions may result in unacceptable printing performance. Other
	unpredictable results may also occur with high volume printing due to the
	resources (for example, GDI, memory, CPU) required for heavy printing loads.
	
	After you apply the updated print server binaries, the following registry entries
	need to be added to allow more than 1,024 3270 print sessions.
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate the following key in the registry:
	
	  
	  HKEY_LOCAL__MACHINE\System\CurrentControlSet\Services\SnaPrint\Parameters
	
	3. On the Edit menu, click Add Value, and then add the following registry
	  value:
	
	  Value Name: Max3270Sessions
	  Data Type: REG_DWORD
	  Value: <Number of 3270 Print sessions>
	
	  Note: The range for this parameter is 1 through 4096.
	
	4. On the Edit menu, click Add Value, and then add the following registry
	  value:
	
	  Value Name: OpenClose
	  Data Type: REG_SZ
	  Value: Yes
	
	  This parameter can have any value. It is enabled as long as the entry exists.
	  A value of Yes is shown for simplicity.
	
	5. Quit Registry Editor.
	
	Each thread created by the Snaprint service for 3270 print sessions still
	supports a maximum of 32 sessions. However, the Snaprint service can now create
	more than 32 threads. The maximum number of threads that can be used for 3270
	printing is obtained by dividing the Max3270Sessions registry setting by 32
	(rounding up if necessary), because each thread can support up to 32 sessions.
	As was the case before this change was made, the Snaprint service does not
	assign a second session to any thread unless it has started the maximum number
	of threads and assigned one session to each of these.
	
	If Max3270Sessions is set to 3000, the print service will create 94 threads
	(3000/32 = 93.75). If there are 94 print sessions, each of the 94 threads will
	have 1 session assigned to it. The 95th session will be assigned to the first
	thread created, giving that thread 2 sessions.
	
	Using the maximum numbers of sessions, which is now 4096, the Snaprint service
	now supports a maximum of 128 threads for 3270 print sessions.
	
	Note: Setting Max3270Sessions unnecessarily high will result in unnecessarily
	high thread and memory usage.
	
	The OpenClose registry setting specifies that the Snaprint service opens a
	printer at the beginning of a print job and closes the printer at the end of the
	print job. By default, the Snaprint service opens all defined printers at print
	service startup. Using this option (especially in conjunction with a large
	number of print sessions) prevents the number of open printer handles from being
	unnecessarily high.
	
	If the OpenClose option is set then the Monitor Job (for example Request Definite
	Response) option cannot be used on the 3270 printer sessions. If the Monitor
	Job/Request Definite Response option is specified on any session, it is
	ignored.
	
	If these registry entries are not set, the Snaprint service will continue to
	support a maximum of 1,024 3270 print sessions, as it did prior to applying
	these updates.
	
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsna300sp1 kbsna300sp2 kbsna300sp3 kbsna300sp4 sna4 kbsna400sp1 kbsna400sp2 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ400 kbSNAServ300SP3 kbSNAServ300SP1 kbSNAServ400SP1 kbSNAServ400SP2 kbSNAServ400SP3 kbSNAServ300SP2 kbSNAServ300SP4
	Version           : WINDOWS:3.0,3.0 SP1,3.0 SP2,3.0 SP3,3.0 SP4,4.0,4.0 SP1,4.0 SP2
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
