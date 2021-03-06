---
layout: page
title: "Q95102: MS-DOS: How to Combine All Logical Drives into One C Drive"
permalink: /kb/095/Q95102/
---

## Q95102: MS-DOS: How to Combine All Logical Drives into One C Drive

{% raw %}

	Article: Q95102
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 19-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you upgrade from MS-DOS versions 3.x to version 5.0, you may want to
	repartition your hard disk drive into one primary DOS partition. Doing so
	requires deleting the current partitions, which in turn deletes all the
	information currently on those logical drives, including MS-DOS. Therefore,
	before deleting the current partitions, you must back up all the files you want
	to keep. After you delete all the current partitions, you can create and format
	the new primary DOS partition, and then reinstall MS-DOS and restore the backed
	up files.
	
	MORE INFORMATION
	================
	
	To upgrade to MS-DOS version 5.0 using Microsoft MS-DOS 5 Upgrade and
	repartition your hard disk drive into one primary DOS partition, do the
	following:
	
	1. Create an MS-DOS 5.0 system disk that contains FORMAT.COM and FDISK.EXE by
	  doing one of the following:
	
	  a. If you have already installed MS-DOS 5.0, insert a formatted disk in drive
	     A and use the following commands to create the system disk. Press ENTER
	     after typing each command at the MS-DOS prompt.
	
	  " sys c: a:
	  copy c:\dos\fdisk.exe a:
	  copy c:\dos\format.com a:
	  copy c:\dos\restore.exe a:" (without the quotation marks)
	
	  b. If you have not installed MS-DOS 5.0, insert Disk 1 of the MS-DOS 5.0
	     setup disks in drive A and type "a:setup /f" (without the quotation marks)
	     at the MS-DOS prompt to create the Startup and Support disks (installing
	     from 5.25-inch disks) or the Startup/Support disk (3.5 inch). The Startup
	     disk is a system disk and contains FORMAT.COM; the Support disk contains
	     FDISK.EXE.
	
	2. Use Microsoft Backup to back up all the files that you want to keep.
	
	3. Start (boot) the machine from the system or Startup disk and run the Fdisk
	  program. (If you've booted from the Startup disk, remove it and insert the
	  Support disk in order to run Fdisk.)
	
	4. Choose Fdisk option 4, Display Partition Information. Fdisk will display your
	  current DOS partitions and, if you have them, any logical drives in the
	  extended DOS partition.
	
	5. Use Fdisk option 3, Delete DOS Partition Or Logical Drive. If you have an
	  extended DOS partition, it must be deleted before the primary DOS partition
	  can be deleted. If you have logical drives in the extended DOS partition,
	  they must all be deleted before you can delete the extended DOS partition.
	
	6. Use Fdisk option 1, Create DOS Partition Or Logical Drive, to create the new
	  primary DOS partition. Accept the default choice of one partition, which
	  includes the entire drive and is set to active.
	
	7. Exit Fdisk. Because you changed the partitioning structure, Fdisk will now
	  reboot the machine.
	
	8. Boot the machine from the system or Startup disk and type the following
	  command at the MS-DOS prompt to format the newly partitioned hard disk
	  drive:
	
	  " format c: /s" (without the quotation marks)
	
	9. Restore your backed up files.
	
	10. Insert Disk 1 of Microsoft MS-DOS 5 Upgrade and run the Setup program to
	  (re)install MS-DOS version 5.0.
	
	Additional query words: 5.00
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS500
	Version           : MS-DOS:5.0
	
	=============================================================================
	

{% endraw %}
