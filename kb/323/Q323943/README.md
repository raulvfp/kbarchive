---
layout: page
title: "Q323943: &quot;Zoo Tycoon Has Encountered&quot; Err Msg Starting Dinosaur Digs Game"
permalink: /kb/323/Q323943/
---

## Q323943: &quot;Zoo Tycoon Has Encountered&quot; Err Msg Starting Dinosaur Digs Game

{% raw %}

	Article: Q323943
	Product(s): Microsoft Home Games
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Zoo Tycoon: Dinosaur Digs Expansion Pack 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you start a Dinosaur Digs game, you may receive the following error
	message:
	
	  Zoo Tycoon has encountered a problem and needs to close. We are sorry for the
	  inconvenience.
	
	  To see what data this error report contains, click here.
	
	When you view the data in the error report, the report contains an error
	signature similar to the following:
	
	  AppName     AppVer       ModName     ModVer       Offset  
	  zoo.exe     11.5.0.6     zoo.exe     11.5.0.6     001307a2
	
	
	CAUSE
	=====
	
	This issue may occur if terrain blending is turned on, or if the video driver
	for your video adapter is outdated.
	
	This issue is known to occur on computers with AMD K6-2-based processors.
	Computers with AMD K6-2-based processors may not be able to use the terrain
	blending feature.
	
	RESOLUTION
	==========
	
	To troubleshoot and resolve this issue, use the following methods, in the order
	in which they are presented.
	
	Method 1
	--------
	
	Turn off terrain blending. To do so, follow these steps:
	
	1. Start Zoo Tycoon Dinosaur Digs, and then click Play Freeform Game.
	
	2. In the Map List, click a Zoo Tycoon map (for example, click Basic Grass Map
	  (Small)), and then click Play.
	
	  NOTE: In this step, make sure that you select a Zoo Tycoon map and not a
	  Dinosaur Digs map.
	
	3. Click the Game Options button.
	
	4. Click the Sound & Video tab. (This tab is located directly below the File
	  Options tab on the right side of the Game Options dialog box.)
	
	5. Under Terrain Blending, click Don't Blend, and then click the File Options
	  tab.
	
	6. Click Main Menu, and then click No when you are prompted to save your current
	  zoo.
	
	7. Start a Dinosaur Digs game and test whether the issue is resolved. If this
	  procedure resolves the issue, you do not have to follow the remaining steps
	  in this article. If the issue is not resolved, go to Method 2.
	
	If you cannot start Zoo Tycoon Dinosaur Digs, you can turn off terrain blending
	by editing the Zoo.ini file. To do so, follow these steps:
	
	NOTE: Because there are several versions of Microsoft Windows, the following
	steps may be different on your computer. If they are, see your product
	documentation to complete these steps.
	
	1. Click Start, point to All Programs, point to Accessories, and then click
	  Notepad.
	
	2. On the File menu, click Open.
	
	3. In the "Files of type" box, click All Files, in the "Look in" box, browse to
	  the <drive>:\Program Files\Microsoft Games\Zoo Tycoon folder, where
	  <drive> is the drive on which Windows is installed.
	
	4. Locate the Zoo.ini file, click the Zoo.ini file, and then click Open.
	
	5. Locate the following lines in the [advanced] section of the Zoo.ini file,
	  where <n>is a number:
	
	  drag=<n>
	  click=<n>
	  normal=<n>
	  level=<n>
	
	6. Change the values for each of the following lines that you located in step 5
	  to 0. For example:
	
	  drag=0
	  click=0
	  normal=0
	  level=0
	
	7. Click Save on the File menu, and then quit Notepad.
	
	Method 2
	--------
	
	Update the video driver for your video adapter, and then remove and reinstall Zoo
	Tycoon and Dinosaur Digs. To do so, follow these steps.
	
	Step 1: Update the Video Driver:
	
	Install the latest video driver that is available for your video adapter. Contact
	the hardware manufacturer for more information about how to do this or to
	inquire about the availability of the latest drivers for your video adapter.
	
	For information about how to contact your video adapter manufacturer, click the
	appropriate article number in the following list to view the article in the
	Microsoft Knowledge Base:
	
	  Q65416 Hardware and Software Third-Party Vendor Contact List, A-K
	
	  Q60781 Hardware and Software Third-Party Vendor Contact List, L-P
	
	  Q60782 Hardware and Software Third-Party Vendor Contact List, Q-Z
	
	Step 2: Remove Zoo Tycoon and Dinosaur Digs:
	
	After you update the video driver, remove Zoo Tycoon and Dinosaur Digs. To do so,
	follow these steps:
	
	1. Click Start, and then click Control Panel.
	
	2. Click "Add or Remove Programs".
	
	3. In the "Currently installed programs" list, click "Zoo Tycoon - Dinosaur
	  Digs", and then click Change/Remove.
	
	4. Click Uninstall, and then click OK.
	
	5. Click OK when you receive the message that states that Zoo Tycoon Dinosaur
	  Digs was removed successfully.
	
	6. Click Start, and then click Search.
	
	7. In the "All or part of the file name" box, type "zoo tycoon" including the
	  quotation marks.
	
	8. In the "Look in" box, click the drive on which Zoo Tycoon was installed, and
	  then click Search.
	
	9. In the search results window, right-click the "Zoo Tycoon" folder, and then
	  click Delete.
	
	  Click Yes to confirm the deletion.
	
	Step 3: Empty the Temp Folder:
	
	To empty the Temp folder, follow these steps:
	
	1. Click Start, point to All Programs, point to Accessories, point to System
	  Tools, and then click Disk Cleanup.
	
	2. In the Drives box, click C: (the drive on which Windows is installed), and
	  then click OK.
	
	3. Click to select the "Temporary files" check box, and then click OK.
	
	4. Click Yes when you are prompted to confirm the operation.
	
	Step 4: Restart the Computer by Using a Clean-Boot Procedure:
	
	Start Windows by using a minimal set of drivers and services. This process, also
	known as a clean boot, provides as "clean" as an installation environment as
	possible in which to reinstall Zoo Tycoon and Dinosaur Digs. To do so, follow
	the steps that are appropriate to your operating system.
	
	Microsoft Windows XP:
	
	1. Click Start, and then click Run.
	
	2. Type "msconfig" (without the quotation marks) in the Open box, and then click
	  OK.
	
	3. Click the General tab, and then click Selective Startup.
	
	4. Click to clear the following check boxes under Selective Startup:
	
	  Process SYSTEM.INI file
	  Process WIN.INI file
	  Load Startup Items
	
	5. Click the Services tab, click to select the "Hide All Microsoft Services"
	  check box, and then click Disable All.
	
	6. Click OK, and then click Restart to restart the computer.
	
	Microsoft Windows Millennium Edition (Me):
	
	1. Click Start, and then click Run.
	
	2. Type "msconfig" (without the quotation marks) in the Open box, and then click
	  OK.
	
	3. Click the General tab, and then click "Selective startup".
	
	4. Click to clear all of the check boxes under Selective startup.
	
	5. On the Startup tab, click to select the *StateMgr check box.
	
	
	6. Click OK. Click Yes when you receive the message to restart the computer.
	  After the computer restarts, click Start, click Run, type "msconfig" (without
	  the quotation marks) in the Open box, and then click OK.
	
	  IMPORTANT: Look closely at the General tab to verify that the check boxes that
	  you cleared are still cleared. If you see a selected, unavailable check box
	  (it appears dimmed and has a check mark in it), your computer is not truly
	  "clean-booted" and you may need assistance from the manufacturer of the
	  program that is listed next to the selected, unavailable check box.
	
	Microsoft Windows 98:
	
	1. Click Start, point to Programs, point to Accessories, point to System Tools,
	  and then click System Information.
	
	2. On the Tools menu, click System Configuration Utility.
	
	3. Click the General tab, click Selective Startup, and then click to clear the
	  following check boxes:
	
	  Process Config.sys file
	  Process Autoexec.bat file
	  Process Winstart.bat file (if available)
	  Process Win.ini file
	  Load Startup group items
	
	4. Click OK, and then restart the computer.
	
	Step 5: Reinstall Zoo Tycoon:
	
	To reinstall Zoo Tycoon, follow these steps:
	
	1. Insert the Zoo Tycoon CD-ROM into the CD-ROM drive or DVD-ROM drive.
	
	  If Setup does not start automatically, follow these steps:
	
	  a. Click Start, and then click Run.
	
	  b. In the Open box, type the following line, where <cd-rom> is the
	     drive letter of the CD-ROM or DVD-ROM drive.
	
	  <cd-rom>:\setup.exe
	
	  c. Click OK.
	
	2. Follow the instructions that are displayed on the screen to install Zoo
	  Tycoon.
	
	3. On the "Zoo Tycoon has been installed successfully!" page, click Setup Menu,
	  and then click the X at the upper-right corner of the Zoo Tycoon screen to
	  quit Zoo Tycoon.
	
	4. Remove the Zoo Tycoon CD-ROM from the CD-ROM drive or DVD-ROM drive.
	
	Step 6: Reinstall Dinosaur Digs:
	
	To reinstall the Dinosaur Digs Expansion Pack, follow these steps:
	
	1. Insert the Zoo Tycoon Dinosaur Digs Expansion Pack CD-ROM into the CD-ROM
	  drive or DVD-ROM drive.
	
	  If Setup does not start automatically, follow these steps:
	
	  a. Click Start, and then click Run.
	
	  b. In the Open box, type the following line, where <cd-rom> is the
	     drive letter of the CD-ROM or DVD-ROM drive.
	
	  <cd-rom>:\setup.exe
	
	  c. Click OK.
	
	2. Follow the on-screen instructions to install Dinosaur Digs.
	
	Step 7: Restore the Computer to a Normal Startup:
	
	To restore the computer to use a normal startup, follow these steps:
	
	1. Start the System Configuration Utility. To do so, do one of the following, as
	  appropriate to your operating system:
	
	   - In Windows XP and Windows Me, click Start, and then click Run. Type
	     "msconfig" (without the quotation marks) in the Open box, and then click
	     OK.
	
	   - In Windows 98, click Start, point to Programs, point to Accessories, point
	     to System Tools, and then click System Information. On the Tools menu,
	     click System Configuration Utility.
	
	2. Click the General tab, click Normal Startup, and then click OK.
	
	3. Restart the computer.
	
	MORE INFORMATION
	================
	
	For additional information about how to perform a clean-boot in Windows, click
	the article numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q310353 How to Perform a Clean Boot in Windows XP
	
	  Q267288 How to Perform a Clean Boot in Windows Millennium Edition
	
	  Q192926 How to Perform Clean-Boot Troubleshooting for Windows 98
	
	The third-party products that are discussed in this article are manufactured by
	companies that are independent of Microsoft. Microsoft makes no warranty,
	implied or otherwise, regarding the performance or reliability of these
	products.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
