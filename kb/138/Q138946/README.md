---
layout: page
title: "Q138946: PPT7: Errors Saving PowerPoint 95 File in PowerPoint 4.0 Format"
permalink: /kb/138/Q138946/
---

## Q138946: PPT7: Errors Saving PowerPoint 95 File in PowerPoint 4.0 Format

{% raw %}

	Article: Q138946
	Product(s): Microsoft PowerPoint for Windows
	Version(s): WINDOWS:7.0
	Operating System(s): 
	Keyword(s): kberrmsg kbinterop kbdta kbconversion
	Last Modified: 16-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft PowerPoint for Windows 95, version 7.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to save a PowerPoint 7.0 file into PowerPoint 4.0 format, you
	receive the following error message:
	
	  Sorry, either the file name is too long or PowerPoint cannot find or run the
	  Viewer, which it needs to save in PowerPoint 4.0 format. If the file name is
	  correct, you should run setup and reinstall to get the Viewer.
	
	Although the error message indicates that long file names cannot be used to save
	a file in PowerPoint 4.0, this is incorrect. You can use long file names when
	you run PowerPoint 4.0 under Windows 95.
	
	CAUSE
	=====
	
	This error occurs if either of the following are true:
	
	- The following two files are missing or incorrectly registered.
	
	  Pp7trans.dll
	  Pptview.dll
	
	
	- The following Windows files are missing or damaged:
	
	  Compobj.dll
	  Ole2.dll
	  Ole2disp.dll
	  Ole2nls.dll
	  Storage.dll
	  Typelib.dll
	
	  These files are installed when you install Windows 95 or Windows NT; they are
	  not installed by PowerPoint or PowerPoint Viewer.
	
	
	WORKAROUND
	==========
	
	To work around this problem, complete the steps 1-2 and then choose the
	appropriate method below:
	
	1. Make sure that the Pp7trans.dll and Pptview.dll files are installed on your
	  computer and that they are both located in the same folder where you
	  installed PowerPnt.exe.
	
	2. Make sure the files are the correct size:
	
	     File name        Size
	     ------------------------
	     Pp7trans.dll       101KB
	     Pptview.dll      1,619KB
	
	  Both of these files are installed by default when you select a typical
	  installation of either Microsoft Office or Microsoft PowerPoint.
	
	Method 1: Run PowerPoint Viewer Setup
	-------------------------------------
	
	1. On the Windows Start menu, click Run.
	
	2. In the Open box, type the following:
	
	  "<drive>:\vsetup" (without the quotation marks)
	
	  where <drive> is the floppy disk drive that contains the disk.
	
	3. Click OK.
	
	4. Click to select the "PowerPoint Viewer" and "Translator To Open PowerPoint 95
	  Files in PowerPoint 4.0" check boxes.
	
	5. Make sure the installation path points to the folder that contains
	  PowerPnt.exe.
	
	6. Follow the instructions on the screen.
	
	Method 2: Reinstall PowerPoint Viewer
	-------------------------------------
	
	Use the following steps if the files are corrupt or missing, or if they were
	deleted:
	
	1. On the Start menu, point to Settings, and then click Control Panel.
	
	2. Double-click the Add/Remove Programs icon.
	
	3. In the list of installed programs, click Microsoft PowerPoint 7.0 or
	  Microsoft Office.
	
	4. Click Add/Remove.
	
	5. Click Reinstall.
	
	6. Click Continue.
	
	Method 3: Reregister PowerPoint Viewer
	--------------------------------------
	
	If both files are present on your computer, and if the files are the correct
	size, reregister PowerPoint Viewer:
	
	1. On the Windows Start menu, click Run.
	
	2. Insert the first disk of the PowerPoint or Office setup disks or the compact
	  disc in the appropriate disk drive.
	
	3. In the Open box, type the following, and then click OK.
	
	  "<drive>:\setup /y" (without the quotation marks)
	
	  where <drive> is the disk drive that contains the disk or CD-ROM.
	
	  Select the same options you chose during the original installation. Although
	  the setup program seems like it is installing the program for the first time,
	  setup will not ask for any disks (unless you select a component that you did
	  not originally install) and it does not copy files to the hard disk. Instead,
	  it reregisters all of the PowerPoint or Office components.
	
	
	Method 4: Check/Configure Virtual Memory Settings
	-------------------------------------------------
	
	1. Right-click the My Computer icon, and then click Properties.
	
	2. Click the Performance tab.
	
	3. Click Virtual Memory.
	
	4. If the swap file is not set to a hard disk with sufficient hard disk space
	  (at least 5-10 megabytes), free up some space. Or, if you have more than one
	  hard disk, set the swap file to the hard disk that has the most available
	  free space.
	
	MORE INFORMATION
	================
	
	Note that if the file has already been saved as a PowerPoint 7.0 file, you must
	type a different file name to save it in PowerPoint 4.0 format. If you do not,
	you will receive an error similar to the following:
	
	  The file C:\Path\File.ppt is currently in use. PowerPoint cannot modify it at
	  this time.
	
	The Pp7trans.dll file translates the PowerPoint 95 presentation into PowerPoint
	4.0 format. Because Pp7trans.dll is a 16-bit file, PowerPoint 7.0 cannot
	communicate directly with it. Instead, PowerPoint uses the PowerPoint Viewer
	(Pptview.dll) to communicate with Pp7trans.dll.
	
	Pp7trans.dll must be located in the PowerPoint directory where the PowerPnt.exe
	file resides or the correct path information must be in the [MS PowerPoint
	Translators] section of the PowerPnt.ini file, which is located in the Windows
	folder. If a PowerPnt.ini file does not exist, the file will be created when the
	Pp7trans.dll file is installed. At the same time, the following statements,
	which will include the correct path information, are written to the PowerPnt.ini
	file:
	
	  [MS PowerPoint Translators]
	  PP7TRANS1=,C:\OFFICE95\POWERPNT\PP7TRANS.dll,PP7
	  PP7TRANS2=PowerPoint 7.0 Presentations,C:\OFFICE95\POWERPNT
	     \pp7trans.dll,PPT
	  PP7TRANS3=PowerPoint 7.0 Templates,C:\OFFICE95\POWERPNT
	     \pp7trans.dll,POT
	
	NOTE: If you installed PowerPoint to a directory other than Office95\PowerPnt,
	your PowerPnt.ini file will show a different path. If the Pp7trans.dll file is
	located in the same directory as the PowerPnt.exe, these lines are not necessary
	in the PowerPnt.ini file; nevertheless, setup adds these statements. If the path
	is incorrectly written in any of these statements, you will receive the error
	described in the "Symptoms" section of this article.
	
	Additional query words: 7.00 down revision downrev PPT 95 backwards compatibility backward
	
	======================================================================
	Keywords          : kberrmsg kbinterop kbdta kbconversion 
	Technology        : kbPowerPtSearch kbPowerPt700 kbZNotKeyword2 kbPowerPt700Search
	Version           : WINDOWS:7.0
	Hardware          : x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
