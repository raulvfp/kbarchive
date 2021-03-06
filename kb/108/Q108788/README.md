---
layout: page
title: "Q108788: How to Return to MS-DOS After Installing PC DOS 6.1"
permalink: /kb/108/Q108788/
---

## Q108788: How to Return to MS-DOS After Installing PC DOS 6.1

{% raw %}

	Article: Q108788
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:6.2,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 22-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 6.2, 6.22 
	-------------------------------------------------------------------------------
	
	This information applies to both Microsoft DoubleSpace and Microsoft
	DriveSpace. For MS-DOS 6.22, use DRVSPACE in place of DBLSPACE for commands
	and filenames.
	
	SUMMARY
	=======
	
	To upgrade from IBM PC DOS 6.1 to MS-DOS 6.2, or to return to your previous
	version of MS-DOS, follow the appropriate procedure (based on your system
	configuration and the options you chose when you installed IBM PC DOS 6.1)
	below.
	
	MORE INFORMATION
	================
	
	Your Hard Disk Drive Is Not Compressed and You Want to Install
	
	MS-DOS 6.2 Upgrade
	------------------
	
	Run MS-DOS 6.2 Upgrade Setup. For example, put MS-DOS 6.2 Upgrade Setup Disk 1 in
	drive A, type "a:setup" (without the quotation marks) at the IBM PC DOS command
	prompt, and then press ENTER.
	
	You Did Not Create an Uninstall Disk, Your Hard Disk Drive Is Not
	
	Compressed, and You Want to Return to MS-DOS 6.0
	------------------------------------------------
	
	1. Use the MOVE command to change the C:\DOS directory to another name. For
	  example, type "move c:\dos c:\pcdos" (without the quotation marks) at the
	  MS-DOS command prompt and then press ENTER.
	
	2. Run MS-DOS 6 Upgrade Setup. For example, put MS-DOS 6 Upgrade Setup Disk 1 in
	  drive A, and type "a:setup" (without the quotation marks) at the MS-DOS
	  command prompt and then press ENTER.
	
	3. After Setup is finished and has rebooted your system, delete the IBM PC DOS
	  6.1 files and directory. For example, type "deltree /y c:\pcdos" (without the
	  quotation marks) at the MS-DOS command prompt and then press ENTER.
	
	You Did Not Create an Uninstall Disk, Your Hard Disk Drive Is Not
	
	Compressed, and You Want to Install MS-DOS 6.2 Upgrade
	------------------------------------------------------
	
	Put the MS-DOS 6.2 Upgrade Setup Disk 1 in drive A and type "a:setup" (without
	the quotation marks) at the IBM PC DOS 6.1 command prompt.
	
	You Did Not Create an Uninstall Disk, Your Hard Disk Drive Is Not Compressed, and
	You Want to Return to MS-DOS 6 Upgrade So That You Can Then Install MS-DOS 6.2
	Step-Up)
	
	1. Move the C:\DOS directory to another name. For example, type "move c:\dos
	  c:\pcdos" (without the quotation marks) at the MS-DOS command prompt and then
	  press ENTER.
	
	2. Run MS-DOS 6 Upgrade Setup. For example, put MS-DOS 6 Upgrade Setup Disk 1 in
	  drive A, and type "a:setup" (without the quotation marks) at the MS-DOS
	  command prompt and then press ENTER.
	
	3. After Setup is finished and has rebooted your system, delete the IBM PC DOS
	  6.1 files and directory. For example, type "deltree /y c:\pcdos" (without the
	  quotation marks) at the MS-DOS command prompt and then press ENTER.
	
	4. Run MS-DOS 6.2 Step-Up Setup. For example, put MS-DOS 6.2 Step-Up Disk 1 in
	  drive A, and type "a:setup" (without the quotation marks) at the MS-DOS
	  command prompt and then press ENTER.
	
	Your Hard Disk Drive Is Compressed, Your System Does Not Have a Partition
	
	Less Than 32 Megabytes, and You Want to Return to MS-DOS 6.0
	------------------------------------------------------------
	
	1. If you have enough free space, run SSUNCOMPRESS.EXE to remove the IBM PC DOS
	  6.1 compression software.
	
	  If you do not have enough free space, refer to the section of this article
	  titled "Your Hard Drive Is Compressed, Your System Has a Partition Less Than
	  32 Megabytes or Insufficient Free Space to Run SSUNCOMPRESS.EXE, and You Want
	  to Return to MS-DOS 6.0."
	
	2. Use the MOVE command to change the C:\DOS directory to another name. For
	  example, type "move c:\dos c:\pcdos" (without the quotation marks) at the
	  MS-DOS command prompt and then press ENTER. EX.
	
	3. Run MS-DOS 6 Upgrade Setup. For example, put MS-DOS 6 Upgrade Setup Disk 1 in
	  drive A, and type "a:setup" (without the quotation marks) at the MS-DOS
	  command prompt and then press ENTER.
	
	4. After Setup is finished and has rebooted your system, delete the IBM PC DOS
	  6.1 files and directory. For example, type "deltree /y c:\pcdos" (without the
	  quotation marks) at the MS-DOS command prompt and then press ENTER.
	
	NOTE: If you try to use your Uninstall disk and one or your drives is compressed,
	your system will be left with an unusual configuration (that is, it will contain
	two DOS systems). Your compressed volume file (CVF) gets modified whether or not
	you chose to install SuperStor during the IBM PC DOS 6.1 installation. For this
	reason, you must remove the compression software before returning to MS-DOS 6.0,
	even if you have an Uninstall disk.
	
	You Did Not Create an Uninstall Disk, Your Hard Disk Drive Is Compressed, Your
	System Has a Partition Less Than 32 Megabytes or Insufficient Free
	
	Space to Run SSUNCOMPRESS.EXE, and You Want to Return to MS-DOS 6.0.
	--------------------------------------------------------------------
	
	You must use the following procedure because the IBM PC DOS 6.1 SSUNCOMPRESS.EXE
	fails (in the middle of the uncompress process) on a partition with less than 32
	megabytes.
	
	1. Back up your data on all the compressed drives.
	
	2. Run SSTOR to determine which drives are compressed and which are not. Write
	  this information down.
	
	3. Restart your computer using your MS-DOS 6 Upgrade Setup Disk 1.
	
	4. Press F5 when you see the "Starting MS-DOS..." prompt.
	
	5. Type "format <drive>: /s" (without the quotation marks), where
	  <drive> is the startup host drive. For example, "format h: /s."
	
	6. Type "format <drive>:" (without the quotation marks) on all host
	  drives, where <drive> is the host drive.
	
	7. Run MS-DOS 6 Upgrade Setup. For example, put MS-DOS 6 Upgrade Setup Disk 1 in
	  drive A, type "a:setup" (without the quotation marks) at the MS-DOS command
	  prompt, and then press ENTER.
	
	8. Type "dblspace" (without the quotation marks) to run DoubleSpace and compress
	  drive C.
	
	9. Run DoubleSpace again.
	
	10. From the Tools menu, choose Compress.
	
	11. Select the drives that were compressed under IBM PC DOS 6.1 and compress
	  them.
	
	12. Install the program you used to back up your data.
	
	13. Restore your data.
	
	Additional query words: stepup 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS622 kbMSDOS620
	Version           : MS-DOS:6.2,6.22
	
	=============================================================================
	

{% endraw %}
