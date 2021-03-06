---
layout: page
title: "Q99396: Troubleshooting Tips Updating LM 2.2 for MS-DOS 6.0"
permalink: /kb/099/Q99396/
---

## Q99396: Troubleshooting Tips Updating LM 2.2 for MS-DOS 6.0

{% raw %}

	Article: Q99396
	Product(s): Microsoft LAN Manager
	Version(s): 
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 30-JUL-2001
	
	SUMMARY
	=======
	
	This article lists some details to check if you are having problems updating
	Microsoft LAN Manager 2.2 to run with MS-DOS 6.0.
	
	MORE INFORMATION
	================
	
	SETVER
	------
	
	Assuming that MS-DOS 5.0 and LAN Manager have been previously installed, there
	should be no problem simply updating the workstation from MS-DOS 5.0 to MS-DOS
	6.0. Be sure that the SETVER command in CONFIG.SYS is from MS-DOS 6.0.
	
	NETWKSTA.EXE
	------------
	
	There is also a newer NETWKSTA.EXE, compiled specifically to run also with MS-DOS
	6.0. The file ensures that version 6.0 is valid for a workstation installation.
	The description of this is recorded in LM23_1338, CSD00.024. It is not strictly
	necessary to have this NETWKSTA file, as SETVER properly installed should
	circumvent any problems.
	
	NETWKSTA.???
	------------
	
	Some confusion has arisen from the supplemental diskette that ships with MS-DOS
	6.0--NETWKSTA.???. This file applies only to Microsoft LAN Manager versions
	2.0x, not 2.1x or 2.2x. The text of the README file is included below.
	
	README
	------
	
	DOS6SUPP.EXE \ NET.TXT
	
	To update LAN Manager version 2.0 Enhanced, replace your current NETWKSTA.EXE and
	NETBEUI.DOS files with the new versions included with the MS-DOS 6 supplemental
	disks. It's a good idea to preserve your current files by renaming them with a
	different extension such as .OLD or .BAK.
	
	1. After Setup finishes installing the Network files, rename these original
	  network files to back them up:
	
	  NETWKSTA.EXE (usually in C:\LANMAN.DOS\NETPROG)
	  NETBEUI.DOS (usually in C:\LANMAN.DOS\DRIVERS\PROTOCOL\NETBEUI)
	
	2. Copy the new version of NETBEUI.DOS to the same drive and directory as the
	  old version of the file.
	
	3. Copy the new NETWKSTA.2XE file to the same drive and directory as the old
	  NETWKSTA.EXE file. Rename the new file to NETWKSTA.EXE.
	
	4. Restart your computer. Or, if you have not installed MS-DOS 6, run Setup now.
	
	Additional query words: 2.20 2.2
	
	======================================================================
	Keywords          : kbnetwork 
	
	=============================================================================
	

{% endraw %}
