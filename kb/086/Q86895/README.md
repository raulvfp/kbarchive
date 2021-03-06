---
layout: page
title: "Q86895: Possible Problems with Windows 3.0, 3.1 Using Setup /P"
permalink: /kb/086/Q86895/
---

## Q86895: Possible Problems with Windows 3.0, 3.1 Using Setup /P

{% raw %}

	Article: Q86895
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 3.0,3.0a,3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 05-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.0, 3.0a, 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	From within Program Manager, you can use the /P parameter to run the Windows
	Setup, forcing it to rebuild the default Program Manager groups and icons. This
	feature behaves differently in Windows versions 3.0 and 3.1.
	
	You can interfere with this maintenance mode operation.
	
	MORE INFORMATION WINDOWS 3.0
	----------------------------
	
	How Setup /P Works:
	
	For Windows 3.0, Setup /P will rebuild the default groups for Program Manager,
	(Main, Accessories, Games) in a "destructive" manner. That is, when it rebuilds
	the groups, it will do so from scratch; the new groups will NOT include any
	icons that you added to the group. In addition, the window's size and location
	will be overwritten.
	
	Possible Problems:
	
	During the process of rebuilding the groups, the mouse cursor is live. If you
	select a group during the process, an Unrecoverable Application Error (UAE) may
	occur, or the system may stop, except for the mouse cursor.
	
	It is also possible that if you select one of the groups as they are being
	rebuilt, the next icons added in the sequence will be put in the wrong group. If
	a group is selected before it is rebuilt, the next icons to be added will be put
	in the wrong group temporarily, until the additional groups are rebuilt.
	
	To correct these problems, run Setup /P again and do not use the keyboard or
	mouse while the process is running.
	
	MORE INFORMATION WINDOWS 3.1
	----------------------------
	
	How Setup /P Works:
	
	For Windows 3.1, Setup /P will rebuild the default Program Manager Groups, (Main,
	Accessories, Games, Startup), in a non-destructive manner. This process will
	KEEP any icons you have added to the default groups, and it will not alter the
	size or window location of these groups. Setup will restore the original icons
	for any of the default items if they have been changed.
	
	Because this is a "non-destructive" process, you will have to use the following
	procedure to restore the default groups as they would be at installation time:
	
	1. Exit Windows 3.1.
	
	2. Delete the file PROGMAN.INI from the WINDOWS directory.
	
	3. Start Windows again. Program Manager should load without any groups.
	
	4. From the File Menu, choose Run.
	
	5. Type the following text and press ENTER.
	
	  setup /p
	
	This will rebuild the groups back to their default contents.
	
	Possible Problems:
	
	The mouse cursor is active during this rebuilding process. If you select either
	an open group, or a minimized group, the rebuilding process will add the next
	icons in the rebuilding sequence to that group. Whether you exit Windows Saving
	Settings or not, you will still have these groups with non-default icons. Due to
	the "non-destructive" process, use the method above for deleting PROGMAN.INI,
	and returning to the original default groups.
	
	If you select a minimized group (which opens the Control menu) during the
	rebuilding process, after the rebuilding process the hourglass pointer will not
	return to a standard pointer. Moving the mouse will return it to the standard
	mouse pointer.
	
	Additional query words: 3.00 3.00a 3.11 3.10 uae freeze lock hang
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin300 kbWin300a kbWin310 kbWin311
	Version           : :3.0,3.0a,3.1,3.11
	
	=============================================================================
	

{% endraw %}
