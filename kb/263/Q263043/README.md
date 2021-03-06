---
layout: page
title: "Q263043: How to remove the MSN 5.x icon from the Windows desktop."
permalink: /kb/263/Q263043/
---

## Q263043: How to remove the MSN 5.x icon from the Windows desktop.

{% raw %}

	Article: Q263043
	Product(s): The Microsoft Network
	Version(s): 2000,5.0,5.1,5.2,5.3,95,98,98 Second Edition
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- MSN versions 5.0, 5.1, 5.2, 5.3 
	- the operating system: Microsoft Windows 95 
	- the operating system: Microsoft Windows 98 
	- the operating system: Microsoft Windows 98 Second Edition 
	- the operating system: Microsoft Windows 2000 
	- the operating system: Microsoft Windows Millennium Edition 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	MSN 5.x is designed to be turned on or turned off. When you turn MSN off, the
	software removes everything but the desktop icon and the setup and installation
	files. Because of this, if you want to use MSN again, all you need to do is
	double-click the desktop icon. The setup screen will display and you will not
	need the CD to reinstall. MSN 5.x is intentionally easy to turn off and turn on.
	If a you have a problem with a corrupted file, turning off and then turning on
	the software may fix the problem.
	
	However, if you want to remove the desktop icon altogether, you can remove it by
	editing the registry files. You must be disconnected from MSN for this procedure
	to work.
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To remove the MSN 5.x icon from your Windows desktop
	
	1. Click Start and click Run.
	
	2. Type regedit and click OK.
	
	3. In the left window open the HKEY_LOCAL_MACHINE folder, open the Software
	  folder, and then open the Microsoft folder.
	
	4. Open the Windows folder, open the CurrentVersion folder, and then open the
	  Explorer folder.
	
	5. Open the Desktop folder and then open the Namespace folder.
	
	6. In the left-hand pane select and delete the following key name
	  88667D10-10F0-11D0-8150-00AA00BF8457.
	
	Note: Neither removing the desktop icon, nor turning off MSN on your computer,
	cancels your MSN account. To cancel your account go to
	http://memberservices.msn.com/us/uscancel.htm.
	
	If you wish to re-install MSN you can use the CD or download the software. It
	will prompt you to re-install.
	
	See also KB Q258985 How to Turn Off The Microsoft Network 5.x
	
	See also Q263042 - How to remove MSN 5.x icon from the Internet Explorer window.
	
	MORE INFORMATION
	================
	
	Caution: This action is not supported by MSN or any MSN support personnel.
	Please use extreme caution. Please note Terms of Use: NOTICE SPECIFIC TO
	DOCUMENTS AVAILABLE ON THIS WEBSITE.
	
	Additional query words: kbimu MSN Internet Access
	
	======================================================================
	Keywords          :  
	Technology        : kbOSWin2000 kbOSWin98 kbOSWin95 kbOSWinME kbOSWin98SE kbOSWinSearch kbMSNSearch kbMSN520 kbMSN530 kbMSN510 kbMSN500
	Version           : :2000,5.0,5.1,5.2,5.3,95,98,98 Second Edition
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
