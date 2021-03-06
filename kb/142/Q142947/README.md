---
layout: page
title: "Q142947: Problems Reinstalling Microsoft Exchange Information Service"
permalink: /kb/142/Q142947/
---

## Q142947: Problems Reinstalling Microsoft Exchange Information Service

{% raw %}

	Article: Q142947
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:95
	Operating System(s): 
	Keyword(s): kbenv kbtool win95
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	- Microsoft Windows 95 OEM Service Release, versions 2.0, 2.1, 2.5 
	- Microsoft Plus! for Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you remove an information service in Microsoft Exchange or Microsoft Windows
	Messaging and then try to reinstall it, the information service may not appear
	when you click Services on the Tools menu and then click Add.
	
	CAUSE
	=====
	
	This behavior can occur if a dynamic-link library file (DLL) associated with the
	information service is missing.
	
	RESOLUTION
	==========
	
	To resolve this issue, use one of the following methods:
	
	- If you want to reinstall the Personal Folders, Personal Address Book,
	  Microsoft Fax, Microsoft Mail, The Microsoft Network Online Service, or
	  Internet Mail information service, extract each of the missing files from
	  your original Windows 95 or Plus! for Windows 95 disks or CD-ROM to your
	  Windows\System folder. For information about using the Extract tool, type
	  "extract" at a command prompt, or see the following article in the Microsoft
	  Knowledge Base:
	
	  Q129605 How to Extract Original Compressed Windows Files
	
	  For a listing of files associated with each information service, please see
	  the "More Information" section of this article. NOTE: If you have installed
	  Internet Explorer version 4.0 or 4.01, you should extract the Awfxcg32.dll
	  file from the Ie4_2.cab cabinet file or reinstall Internet Explorer. For
	  additional information about this issue, please see the following article in
	  the Microsoft Knowledge Base:
	
	  Q174887 Error Message: Exchng32 Caused an Invalid Page Fault...
	
	- If you want to reinstall the CompuServe Mail information service,
	  double-click the Setup.exe file in the Drivers\Other\Exchange\Compusrv folder
	  on the Windows 95 CD-ROM.
	
	MORE INFORMATION
	================
	
	The following tables list the DLLs associated with each information service:
	
	Windows 95
	----------
	
	Personal Folders and Personal Address Book:
	
	  File name     Location
	  ---------------------------------------------------------
	  Mspst32.dll   Win95_06.cab on Windows 95 CD-ROM or disk 6
	
	Microsoft Fax:
	
	  File name      Location
	  ----------------------------------------------------------
	  Awcl1_32.dll   Win95_05.cab on Windows 95 CD-ROM or disk 5
	  Awdevl32.dll   Win95_05.cab on Windows 95 CD-ROM or disk 5
	  Awfaxp32.dll   Win95_05.cab on Windows 95 CD-ROM or disk 5
	  Awfxab32.dll   Win95_05.cab on Windows 95 CD-ROM or disk 5
	  Awfxcg32.dll   Win95_05.cab on Windows 95 CD-ROM or disk 5
	  Awrndr32.dll   Win95_05.cab on Windows 95 CD-ROM or disk 5
	
	Microsoft Mail:
	
	  File name    Location
	  -----------------------------------------------------------------
	  Msfs32.dll   Win95_06.cab on Windows 95 CD-ROM or Win95_07.cab on
	               disk 7
	
	The Microsoft Network Online Service:
	
	  File name      Location
	  ----------------------------------------------------------
	  Mosabp32.dll   Win95_07.cab on Windows 95 CD-ROM or disk 7
	  Moscfg32.dll   Win95_07.cab on Windows 95 CD-ROM or disk 7
	  Mosrxp32.dll   Win95_07.cab on Windows 95 CD-ROM or disk 7
	
	Internet Mail:
	
	  File name     Location
	  ----------------------------------------------------------------
	  Minet32.dll   Plus_7.cab on Microsoft Plus! CD-ROM or Plus_6.cab
	                on disk 6
	
	CompuServe Mail:
	
	  File name      Location
	  -------------------------------------------------------------------
	  Csmapa32.dll   Drivers\Other\Exchange\Compusrv folder on Windows 95
	                 CD-ROM
	
	  Csmapx32.dll   Drivers\Other\Exchange\Compusrv folder on Windows 95
	                 CD-ROM
	
	Windows 95 OEM Service Release 2, 2.1, 2.5
	------------------------------------------
	
	Personal Folders and Personal Address Book:
	
	  File name     Location
	  --------------------------
	  Mspst32.dll   Win95_09.cab
	
	Microsoft Fax:
	
	  File name      Location
	  ---------------------------
	  Awcl1_32.dll   Win95_06.cab
	  Awdevl32.dll   Win95_06.cab
	  Awfaxp32.dll   Win95_06.cab
	  Awfxab32.dll   Win95_06.cab
	  Awfxcg32.dll   Win95_06.cab
	  Awrndr32.dll   Win95_07.cab
	
	Microsoft Mail:
	
	  File name    Location
	  -------------------------
	  Msfs32.dll   Win95_10.cab
	
	The Microsoft Network Online Service:
	
	  File name      Location
	  ---------------------------
	  Mosabp32.dll   Win95_10.cab
	  Moscfg32.dll   Win95_10.cab
	  Mosrxp32.dll   Win95_10.cab
	
	Internet Mail:
	
	  File name     Location
	  -------------------------
	  Minet32.dll   Plus_19.cab
	
	Notes
	-----
	
	- You cannot extract the Csmapa32.dll and Csmapx32.dll files from the CD-ROM.
	  To reinstall the CompuServe Mail information service, run Setup.exe in the
	  Drivers\Other\Exchange\Compusrv folder on the Windows 95 CD-ROM.
	
	- The CompuServe Mail information service is included in the CD-ROM version of
	  Windows 95, but not in the floppy disk version. To use the CompuServe Mail
	  information service, you must have the CD-ROM version of Windows 95.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kbtool win95 
	Technology        : kbWin95search kbGamesSearch kbPlusSearch kbOPKSearch kbWin95 kbWin95OPKOSR25 kbWin95OPKOSR210 kbPlus95
	Version           : WINDOWS:95
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
