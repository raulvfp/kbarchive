---
layout: page
title: "Q92647: WinFax Pro 2.0 and Windows 3.1: Troubleshooting Information"
permalink: /kb/092/Q92647/
---

## Q92647: WinFax Pro 2.0 and Windows 3.1: Troubleshooting Information

{% raw %}

	Article: Q92647
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 26-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	WinFax Pro version 2.0 is a Windows-based application manufactured by Delrina
	Technology that can send and receive faxes. To use WinFax Pro successfully with
	Windows 3.1, use a version of WinFax Pro 2.0 dated November 28, 1991, or later.
	
	This article discusses the following topics:
	
	- Faxes Sent and Received Slowly and Lost Characters
	
	- Faxes Hang System
	
	- After Dark and WinFax Pro
	
	- Intel Satisfaction
	
	- Norton Desktop for Windows
	
	- WinFax Pro Makes Itself the Default Printer
	
	- 14.4 Kilobits-Per-Second (Kbps) Rate Problems
	
	- Unable to Start Multimedia Viewer with WinFax Pro
	
	Information for this article was provided by Delrina Technical Support.
	
	MORE INFORMATION
	================
	
	Faxes Sent and Received Slowly and Lost Characters
	--------------------------------------------------
	
	On 80286 machines, sending or receiving faxes may occur slowly, and some
	characters may be lost. To correct this problem, do the following:
	
	1. Remove terminate-and-stay-resident (TSR) programs from the AUTOEXEC.BAT and
	  CONFIG.SYS files.
	
	2. If you are using Microsoft MS-DOS 5.0, load MS-DOS low by specifying DOS=LOW
	  in the CONFIG.SYS file.
	
	3. Add the following line to the [Standard] section of the SYSTEM.INI file:
	
	  FasterModeSwitch=1
	
	Faxes Hang System
	-----------------
	
	In 386 enhanced mode, if your computer stops responding (hangs) when a fax is
	sent or received, add the following lines to the [386Enh] section of the
	SYSTEM.INI file:
	
	     COMBoostTime=15
	     COMxProtocol=XOFF
	     COMxBuffer=1024
	     COMxAutoAssign=0
	
	Substitute the appropriate COM port for "x."
	
	After Dark and WinFax Pro
	-------------------------
	
	If you are running version 1.0 of Berkeley Systems' After Dark screen saver,
	upgrade to version 2.0 of After Dark.
	
	According to Delrina Technical Support, if you use WinFax Pro version 2.0 with
	After Dark version 1.0, After Dark may interfere with the transmission of
	faxes.
	
	As a temporary workaround, you can turn off the After Dark System IO Monitor:
	
	1. Run the After Dark control panel.
	
	2. Select the When option.
	
	3. Turn off System IO Monitor.
	
	Delrina Technical Support does not recommend running both programs from the Load=
	line of the WIN.INI file. If After Dark 1.0 appears on the Load= line with
	WinFax Pro 2.0, you may not be able to use one of the two applications.
	
	Intel Satisfaction
	------------------
	
	If you are running the Intel Satisfaction Board with CAS Driver version 1.0,
	update the CAS Driver to version 2.0.
	
	Norton Desktop for Windows
	--------------------------
	
	WinFax Pro 2.0 does not run correctly with Norton Desktop for Windows.
	
	WinFax Pro Makes Itself Default Printer
	---------------------------------------
	
	WinFax Pro becomes the default printer when you install it and periodically makes
	itself the default printer after installation. (This problem also occurs with
	Windows 3.0 as well.)
	
	14.4 Kbps Rate Problems
	-----------------------
	
	If you run WinFax Pro with Windows 3.1 and experience problems at a bit rate of
	14.4 Kbps, call Delrina to receive an update to correct this problem. If your
	version of WinFax Pro is an OEM version bundled with a fax modem, contact your
	OEM dealer.
	
	Unable to Start Multimedia Viewer with WinFax
	---------------------------------------------
	
	You may be unable to start Microsoft Multimedia Viewer (VIEWER.EXE) if WinFax is
	running. To work around this problem, rename VIEWER.EXE to VIEW.EXE (or another
	name).
	
	WinFax automatically loads a dynamic-link library (DLL) called VIEWER.DLL that
	allows you to view received faxes. When you double-click the Viewer icon, Viewer
	does not run because it is already in memory and it cannot run multiple
	instances. Double-clicking the Viewer icon momentarily displays an hourglass
	mouse cursor but no program loads.
	
	The products included here are manufactured by vendors independent of Microsoft;
	we make no warranty, implied or otherwise, regarding these products' performance
	or reliability.
	
	Additional query words: 3.10 afterdark win fax 3rdparty bookshelf ndw facsimile
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin310 kbWin311
	Version           : WINDOWS:3.1,3.11
	
	=============================================================================
	

{% endraw %}
