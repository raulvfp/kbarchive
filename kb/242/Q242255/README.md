---
layout: page
title: "Q242255: XCLN: Outlook Web Access First Chance Exception in Emsui32.dll"
permalink: /kb/242/Q242255/
---

## Q242255: XCLN: Outlook Web Access First Chance Exception in Emsui32.dll

{% raw %}

	Article: Q242255
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5 SP2,5.5 SP3
	Operating System(s): 
	Keyword(s): exc55sp2 exc55sp3 kbExchange550preSP4fix kbExchange550sp4Fix
	Last Modified: 12-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5 SP2, 5.5 SP3 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you debug Microsoft Outlook Web Access (OWA), you may receive a first
	chance exception in a call stack that is similar to the following:
	
	  
	
	  FramePtr  RetAddr   Param1   Param2   Param3   Function Name
	  02baf08c  625e4ace  63a24a00 00000000 63a24b81 EMSUI32!ScWriteTransportStoreAB+0x41
	  02baf0bc  625e502c  63a24a00 000004e4 00000409 EMSUI32!ScSaveGeneralChanges+0xce
	  02baf128  625de49e  00000000 02baf11c 00000007 EMSUI32!ScEMSCfgSansUI+0x3cc
	  02baf224  6fb3cdd0  625d0000 77bc9198 2477f528 EMSUI32!EMSCfg+0x2ce
	  02baf290  6fb3cf3c  42792f28 42559f68 625d0000 MAPI32!ScCallServiceEntry+0x100
	  02baf2f4  6fb3c3f3  42792f28 42559f68 00000000 MAPI32!ScConfigService+0x11c
	  02baf358  6f084313  24297c48 42559f68 00000000 MAPI32!MFISA_ConfigureMsgService+0x53
	  02baf470  6fb375c3  02bafdd8 6fb44220 6fa94f30 CDO!HrCreateProfile+0x4e3
	  02baf4f4  6f06cc63  2da16174 6f0868e8 6f083060 MAPI32!PvGetInstanceGlobalsExInt+0x53
	  02baf504  6f06ca10  185b0330 246d5210 00000000 CDO!CDispatchObj::M_ResetErr+0x43
	  02baf554  78004743  00c2b190 00000000 00000007 CDO!CDispatchObj::Invoke+0xa0({...})
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server 5.5.
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the latest Exchange Server 5.5 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5 Service Packs 2 and 3. This problem was first corrected in Exchange
	Server 5.5 Service Pack 4.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55sp2 exc55sp3 kbExchange550preSP4fix kbExchange550sp4Fix 
	Technology        : kbExchangeSearch kbZNotKeyword2 kbExchange550SP2 kbExchange550SP3
	Version           : winnt:5.5 SP2,5.5 SP3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
