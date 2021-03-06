---
layout: page
title: "Q102469: How to Display Network Registry Parameters"
permalink: /kb/102/Q102469/
---

## Q102469: How to Display Network Registry Parameters

{% raw %}

	Article: Q102469
	Product(s): Microsoft Windows NT
	Version(s): 3.1 3.51 4.0
	Operating System(s): 
	Keyword(s): kbenv
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.1 
	- Microsoft Windows NT Workstation version 3.1 
	- Microsoft Windows NT Advanced Server, version 3.1 
	- Microsoft Windows NT Server versions 3.51, 4.0 
	- Microsoft Windows NT Workstation versions 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	You can get most of the Lan Manager Server and Workstation parameters to appear
	in the registry automatically by using the NET CONFIG command.
	
	WARNING: When you run NET CONFIG SERVER (or NET CONFIG SRV), server related
	parameters that are normally autoconfigured each time you boot (for example,
	maxworkitems)are permanently set in the registry to whatever values Windows NT
	is currently using. These parameters will continue to override the defaults
	until you change them in the registry. You cannot change the values by running
	Control Panel, choosing Server, and then choosing Configure. Consequently, if
	you add or remove memory, or change the server size setting
	(minimize/balance/maximize), you will not get the benefit of server
	autoconfiguration.
	
	MORE INFORMATION
	================
	
	By default, the only parameters in the
	
	  HKEY_LOCAL_MACHINE
	
	  \SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters
	
	section of the registry are the following:
	
	                        Size  3
	                  Lmannounce  0
	
	Windows NT 3.51 and 4.0 have the following additional entries:
	
	                                ==========
	
	                         NullSessionPipes
	                        NullSessionShares
	
	However, if you type the following at the command line
	
	  C:\>net config server /HIDDEN:NO
	  The command completed successfully.
	
	you will see the following appear in the registry:
	
	  HKEY_LOCAL_MACHINE\SYSTEM
	
	  \CurrentControlSet\Services\LanmanServer\parameters
	
	                        Size  3
	                  Lmannounce  0
	                     comment  ""
	                  srvcomment  ""
	                       users  -1
	                        disc  15
	              autodisconnect  15
	                      hidden  1
	                    announce  720
	                    anndelta  3000
	                    userpath  "c:\"
	                   sessopens  2048
	                     sessvcs  1
	                  opensearch  2048
	                maxworkitems  128
	                maxrawbuflen  65535
	                   sessusers  2048
	                   sessconns  2048
	         maxpagedmemoryusage  -1
	      maxnonpagedmemoryusage  -1
	            enablesoftcompat  1
	          enableforcedlogoff  1
	                  timesource  0
	
	Windows NT 3.51 and 4.0 have the same above entries EXCEPT the "disc" and the
	"comment" are eliminated.
	
	                     comment
	                        disc
	
	This situation also applies to the Lan Manager Workstation section of the
	registry. By default the
	
	  HKEY_LOCAL_MACHINE
	
	  \SYSTEM\CurrentControlSet\Services\Lanmanworkstation\parameters
	
	section of the registry is empty. However, if you type
	
	  net config work /CHARTIME:250
	
	the following appears:
	
	  HKEY_LOCAL_MACHINE
	
	  \SYSTEM\CurrentControlSet\Services\Lanmanworkstation\parameters
	
	                    CharWait  3600
	          MaxCollectionCount  16
	              CollectionTime  250
	                    KeepConn  600
	                     MaxCmds  50
	                 SessTimeout  45
	                  SizCharBuf  512
	                  MaxThreads  17
	                   LockQuota  6144
	               LockIncrement  10
	                 LockMaximum  500
	               PipeIncrement  10
	                 PipeMaximum  500
	            CacheFileTimeout  10
	            DormantFileLimit  45
	         ReadAheadThroughput  -1
	             MailslotBuffers  8
	       ServerAnnounceBuffers  20
	    NumIllegalDatagramEvents  5
	    IllegalDatagramResetTime  60
	          LogElectionPackets  0
	     UseOpportunisticLocking  1
	             UseUnlockBehind  1
	              UseCloseBehind  1
	               BufNamedPipes  1
	           UseLockReadUnlock  1
	            UtilizeNtCaching  1
	                  UseRawRead  1
	                 UseRawWrite  1
	             UseWriteRawData  1
	               UseEncryption  1
	           BufFilesDenyWrite  1
	            BufReadOnlyFiles  1
	         ForceCoreCreateMode  1
	       Use512ByteMaxTransfer  0
	
	Windows NT 3.51 and 4.0 have the same above entries.
	
	Additional query words: prodnt tune tuning
	
	======================================================================
	Keywords          : kbenv 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT400search kbWinNTW351search kbWinNTW351 kbWinNTW310 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS310 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS351search kbWinNTS310search kbWinNT310Search kbWinNTW310Search
	Version           : 3.1 3.51 4.0
	
	=============================================================================
	

{% endraw %}
