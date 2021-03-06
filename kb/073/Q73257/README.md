---
layout: page
title: "Q73257: Manual Installation of Microsoft MS-DOS 5 Upgrade"
permalink: /kb/073/Q73257/
---

## Q73257: Manual Installation of Microsoft MS-DOS 5 Upgrade

{% raw %}

	Article: Q73257
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 22-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system version 5.0 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	If the Setup routine for MS-DOS version 5.0 fails, try manually installing
	Microsoft MS-DOS 5 Upgrade as described in this article.
	
	NOTE: The manual installation does not produce an Uninstall disk like the normal
	upgrade; therefore, you cannot easily return to your previous version.
	
	MORE INFORMATION
	================
	
	To manually install Microsoft MS-DOS 5 Upgrade, do the following:
	
	1. Back up all of your current files.
	
	2. Insert the Microsoft MS-DOS 5 Upgrade Disk 1 in drive A and type the
	  following command:
	
	  " a: setup /f" (without the quotation marks)
	
	  This creates a set of bootable MS-DOS 5.0 floppy disks (the procedure requires
	  seven 5.25-inch disks or four 3.5-inch disks).
	
	3. Start the machine with the Startup disk (5.25 inch) or Startup/Support disk
	  (3.5 inch). Check to ensure that all partitions can be accessed and the
	  machine is working correctly.
	
	4. If repartitioning is desired, now is the time to use the MS-DOS 5.0 FDISK
	  command. Insert the disk that contains FDISK.EXE (5.25-inch Startup disk;
	  3.5-inch Startup/Support disk), type "FDISK" (without the quotation marks),
	  and follow the instructions. After you run FDISK, run FORMAT.
	
	5. If you can access all drives, insert the floppy disk that contains SYS.COM
	  (5.25-inch Startup disk; 3.5-inch Startup/Support disk) into drive A and type
	  "SYS C:" (without the quotation marks). This program makes the C: drive boot
	  MS-DOS 5.0.
	
	6. Create an OLDDOS directory and copy all of the files from your current DOS
	  directory to the OLDDOS directory. Then, delete your old MS-DOS files in the
	  DOS directory. For example:
	
	  MD C:\OLDDOS
	  COPY C:\DOS\*.* C:\OLDDOS\*.*
	  ERASE C:\DOS
	
	7. Copy the MS-DOS 5.0 files from the bootable floppy disks to the DOS directory
	  on your hard drive. For example:
	
	  COPY A:*.* C:\DOS\*.*
	
	8. If you are using Microsoft Windows, copy the WINA20.386 file to the root
	  directory of drive C. This file is necessary for Windows 3.0 to work
	  correctly. The WINA20.386 file is located on the Utility disk (5.25-inch) or
	  Basic/Edit/Utility disk (3.5-inch). Insert the disk into your floppy disk
	  drive (for example drive A) and type the following command:
	
	  " copy a:WINA20.386 c:\ " (without the quotation marks)
	
	9. Update your current CONFIG.SYS and AUTOEXEC.BAT files referring to CONFIG.NEW
	  and AUTOEXEC.NEW located on the first floppy disk.
	
	Additional query words: 5.00
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS500
	Version           : MS-DOS:5.0
	
	=============================================================================
	

{% endraw %}
