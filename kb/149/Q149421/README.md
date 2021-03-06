---
layout: page
title: "Q149421: Using Detailed Logging to Debug SNMP Issues"
permalink: /kb/149/Q149421/
---

## Q149421: Using Detailed Logging to Debug SNMP Issues

{% raw %}

	Article: Q149421
	Product(s): Microsoft Windows NT
	Version(s): 3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): kbnetwork kbSDKPlatform kbSNMP kbGrpDSNet
	Last Modified: 20-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	You can obtain detailed SNMP debug information on Windows NT systems without
	attaching a debugger by using the checked build of Snmp.exe.
	
	MORE INFORMATION
	================
	
	Use the following steps to log detailed debug information to a log file
	(Snmpdbg.log) in the %SYSTEMROOT%\SYSTEM32 subdirectory, or to the system event
	log.
	
	
	1. Change to the %SYSTEMROOT\SYSTEM32 subdirectory.
	
	2. Rename the Snmp.exe file in your %SYSTEMROOT\SYSTEM32 subdirectory to
	  SNMP.FRE.
	
	3. Copy the checked Snmp.exe file to your %SYSTEMROOT\SYSTEM32 subdirectory.
	
	4. From a command prompt, type the following:
	
	  "NET START SNMP /loglevel:20 /logtype:7" (without the quotation marks)
	
	  Debug information will be written to %SYSTEMROOT%\SYSTEM32\SNMPDBG.LOG, and to
	  the system event log.
	
	5. You can adjust the output detail by lowering the /loglevel and /logtype
	  options to lower numbers.
	
	Sample Output Using /loglevel:20 /logtype:7
	-------------------------------------------
	
	Service: Debug log type changed to 7.
	Service: Begin initializing agent.
	agentConfigInit: entered.
	regconf: entered.
	vcConfig: entered.
	vcConfig: RegKey Opened OK.
	vcConfig: Calling RegEnumValue.
	vcConfig: value found - type :1
	vcConfig: value found - name :1
	vcConfig: value found - data:pigland
	vcConfig: memcpy called
	vcConfig: memcpy returned
	vcConfig: Calling RegEnumValue again.
	vcConfig: RegEnumValue returned NO_MORE_ITEMS
	vcConfig: calling RegCloseKey
	vcConfig: RegCloseKey returned
	vcConfig: exit.
	pmConfig: entered.
	pmConfig: exit.
	eaConfig: entered.
	eaConfig: value found (eakey) - type :1
	eaConfig: value found (eakey) - name :1
	eaConfig: value found (eakey) -
	data:SOFTWARE\Microsoft\LANManagerMIB2Agent\CurrentVersion
	eaConfig: value found (agent) - type :2
	eaConfig: value found (agent) - name :Pathname
	eaConfig: value found (agent) - data:%SystemRoot%\System32\lmmib2.dll
	eaConfig: Pathname found (agent)
	eaConfig: ExpandEnvironmentStrings called
	%SystemRoot%\System32\lmmib2.dll
	eaConfig: ExpandEnvironmentStrings called
	%SystemRoot%\System32\lmmib2.dll
	eaConfig: ExpandEnvironmentStrings returned
	C:\WINNT35\System32\lmmib2.dll
	eaConfig: value found (eakey) - type :1
	eaConfig: value found (eakey) - name :2
	eaConfig: value found (eakey) -
	data:SOFTWARE\Microsoft\RFC1156Agent\CurrentVersion
	eaConfig: value found (agent) - type :2
	eaConfig: value found (agent) - name :Pathname
	eaConfig: value found (agent) - data:%SystemRoot%\System32\inetmib1.dll
	eaConfig: Pathname found (agent)
	eaConfig: ExpandEnvironmentStrings called
	%SystemRoot%\System32\inetmib1.dll
	eaConfig: ExpandEnvironmentStrings called
	%SystemRoot%\System32\inetmib1.dll
	eaConfig: ExpandEnvironmentStrings returned
	C:\WINNT35\System32\inetmib1.dll
	eaConfig: value found (eakey) - type :1
	eaConfig: value found (eakey) - name :3
	eaConfig: value found (eakey) -
	data:SOFTWARE\Microsoft\DhcpMibAgent\CurrentVersion
	eaConfig: value found (agent) - type :2
	eaConfig: value found (agent) - name :Pathname
	eaConfig: value found (agent) - data:%SystemRoot%\System32\dhcpmib.dll
	eaConfig: Pathname found (agent)
	eaConfig: ExpandEnvironmentStrings called
	%SystemRoot%\System32\dhcpmib.dll
	eaConfig: ExpandEnvironmentStrings called
	%SystemRoot%\System32\dhcpmib.dll
	eaConfig: ExpandEnvironmentStrings returned
	C:\WINNT35\System32\dhcpmib.dll
	eaConfig: value found (eakey) - type :1
	eaConfig: value found (eakey) - name :4
	eaConfig: value found (eakey) -
	data:SOFTWARE\Microsoft\WinsMibAgent\CurrentVersion
	eaConfig: value found (agent) - type :2
	eaConfig: value found (agent) - name :Pathname
	eaConfig: value found (agent) - data:%SystemRoot%\System32\winsmib.dll
	eaConfig: Pathname found (agent)
	eaConfig: ExpandEnvironmentStrings called
	%SystemRoot%\System32\winsmib.dll
	eaConfig: ExpandEnvironmentStrings called
	%SystemRoot%\System32\winsmib.dll
	eaConfig: ExpandEnvironmentStrings returned
	C:\WINNT35\System32\winsmib.dll
	eaConfig: exit.
	tdConfig: entered.
	tdConfig: exit.
	regconf: exit.
	Init: Read registry parameters.
	error on ipx socket 10047
	error on GetProcAddress(InitEx) 127
	Init: Loaded/initialized 'C:\WINNT35\System32\lmmib2.dll'.
	Init: Dupping 4 - 'C:\WINNT35\System32\inetmib1.dll'.
	Init: Dupping 5 - 'C:\WINNT35\System32\inetmib1.dll'.
	Init: Dupping 6 - 'C:\WINNT35\System32\inetmib1.dll'.
	Init: Dupping 7 - 'C:\WINNT35\System32\inetmib1.dll'.
	Init: Dupping 8 - 'C:\WINNT35\System32\inetmib1.dll'.
	Init: Dupping 9 - 'C:\WINNT35\System32\inetmib1.dll'.
	Init: Loaded/initialized 'C:\WINNT35\System32\inetmib1.dll'.
	error on GetProcAddress(InitEx) 127
	Init: Loaded/initialized 'C:\WINNT35\System32\dhcpmib.dll'.
	error on GetProcAddress(InitEx) 127
	Init: Loaded/initialized 'C:\WINNT35\System32\winsmib.dll'.
	Init: Set-up UDP listen port (SNMP).
	error on IPX socket 10047
	Init: created agentCommThread tid=0x76.
	agentCommThread entered
	agentCommThread in select
	Init: becoming agentTrapThread.
	Service: serviceHandlerFunction(dwControl=4).
	trapThread: event 1 set.
	trapThread: trap by extension agent 1.
	trapThread: trap by extension agent 1.
	trapThread: trap by extension agent 1.
	trapThread: event 1 set.
	trapThread: event 1 set.
	trapThread: event 1 set.
	trapThread: event 1 set.
	trapThread: event 1 set.
	trapThread: event 1 set.
	trapThread: event 1 set.
	trapThread: event 1 set.
	trapThread: event 1 set.
	trapThread: event 1 set.
	trapThread: event 1 set.
	Service: serviceHandlerFunction(dwControl=1).
	trapThread: event 0 set.
	trapThread: agentTrapThread exiting.
	Term: agentTrapThread returned.
	Term: comm thread in safe state for termination.
	Term: agentCommThread terminated.
	Service: Ending execution.
	
	Additional query words: clever debugging tips
	
	======================================================================
	Keywords          : kbnetwork kbSDKPlatform kbSNMP kbGrpDSNet 
	Technology        : kbWinNTsearch kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : :3.5,3.51,4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
