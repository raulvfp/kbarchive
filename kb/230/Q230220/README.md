---
layout: page
title: "Q230220: TN3270 Emulators May Fail to Reconnect After Inactivity Timeout"
permalink: /kb/230/Q230220/
---

## Q230220: TN3270 Emulators May Fail to Reconnect After Inactivity Timeout

{% raw %}

	Article: Q230220
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:4.0SP2
	Operating System(s): 
	Keyword(s): kbsna400sp3fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, version 4.0SP2 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When TN3270 emulators are connecting through the TN3270 server included with SNA
	Server 4.0 Service Pack 2 (SP2) to a host session, the TN3270 emulators may fail
	to automatically reconnect when the session ends because of inactivity.
	
	The following message may be displayed in the TN3270 emulator window when the
	TN3270 server ends the session due to inactivity:
	
	  TN3270E Service Error 503
	
	  Session terminated due to inactivity.
	
	NOTE: This message may not be displayed in the same manner in all TN3270
	emulators.
	
	In addition, the following event will be logged in the Windows NT application
	event log by the TN3270 server when a TN3270 session is ended due to
	inactivity:
	
	  Event ID: 603
	  Source: TN3270 Server
	  Description: TN3270(E) session with client at <TCP/IP Address> (port
	  <IP Port>) using LU <TN3270 LU Name> terminated abnormally
	  because:
	
	  TN3270E Service Error 503
	
	  Session terminated due to inactivity.
	
	When TN3270 emulators are configured to autoconnect, they successfully reconnect
	to a host session after receiving the previous inactivity timeout message
	without any user intervention when they are connecting to a host session through
	a TN3270 server included with SNA Server versions 4.0 Service Pack 1 and
	earlier.
	
	CAUSE
	=====
	
	The TN3270 emulator is unable to reconnect to the TN3270 server because the
	previous TN3270 session is not being cleaned up properly. This occurs because
	the TN3270 server has issued an RUI_READ() to the TN3270 client that never
	completes because the TN3270 emulator does not send any data to the TN3270
	server after it receives the inactivity error message described above. Because
	the TN3270 server is waiting for the RUI_READ() to complete, it does not reset
	the underlying TCP/IP session that is open between the TN3270 server and the
	TN3270 client. The TN3270 emulator does not attempt to reconnect while the
	previous TCP/IP session is still open.
	
	The TN3270 server in SNA Server 4.0 SP2 was updated to use Windows NT I/O
	Completion Ports to provide performance improvements. It is the use of I/O
	Completion Ports that causes this particular problem to occur. Therefore, the
	TN3270 server included with earlier versions of SNA Server does not exhibit this
	behavior.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for SNA Server version
	4.0. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q215838 How to Obtain the Latest SNA Server Version 4.0 Service Pack
	
	
	WORKAROUND
	==========
	
	The TN3270 emulator will reconnect to a host session if one of the following is
	done:
	
	- The user presses the ENTER key at the TN3270 session window.
	- The user explicitly disconnects/reconnects the session from within the TN3270
	  emulator window.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft SNA Server version 4.0
	SP2. This problem was first corrected in SNA Server version 4.0 Service Pack 3.
	
	MORE INFORMATION
	================
	
	For additional information about a similar TN3270 issue with SNA Server 4.0 SP2,
	please click the article number(s) below to view the article(s) in the Microsoft
	Knowledge Base:
	
	  Q239707 TN3270 Clients May Fail to Reconnect to a Host Session
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsna400sp3fix 
	Technology        : kbAudDeveloper kbSNAServSearch
	Version           : WINDOWS:4.0SP2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
