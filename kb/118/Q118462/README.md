---
layout: page
title: "Q118462: Dangerous Creatures: TROUBLE.TXT Contents"
permalink: /kb/118/Q118462/
---

## Q118462: Dangerous Creatures: TROUBLE.TXT Contents

{% raw %}

	Article: Q118462
	Product(s): Microsoft Home Multimedia Titles
	Version(s): WINDOWS:1.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Dangerous Creatures for Windows, version 1.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains a copy of the information in the TROUBLE.TXT file included
	with Microsoft Dangerous Creatures version 1.0.
	
	MORE INFORMATION
	================
	
	=====================================================================
	                               TROUBLE.TXT
	=====================================================================
	
	Having problems running Microsoft Dangerous Creatures?  Read the text
	below.  If you don't find the information you need here, check the
	README file that was installed with Dangerous Creatures.
	
	PERFORMANCE PROBLEMS
	====================
	
	Microsoft Dangerous Creatures uses your computer's system memory to
	display pictures.  If you find that Dangerous Creatures runs slowly or
	if you encounter out-of-memory errors, the program probably doesn't
	have enough memory.  Consider doing the following to improve your
	computer's performance:
	
	* Close all unnecessary applications.
	
	* Determine how much total memory your computer has available.
	  At the system prompt, type "mem" and press ENTER.  You need a
	  minimum of 4MB (4,000,000 bytes) of total memory to use
	  Dangerous Creatures.  If you do not have at least 4MB of
	  memory, you will not be able to run Dangerous Creatures
	  until you add more memory.
	
	* Dangerous Creatures needs a minimum of 5000K free in Windows
	  for best movie performance.  To check the amount of free
	  memory Windows has available, start Windows, and from
	  Program Manager pull down the "Help" menu then choose
	  "About Program Manager."
	
	* If you are running Windows in Enhanced mode, set up a permanent
	  Windows swap file on your hard disk.  A swap file of greater
	  than 4MB (4,000K) is recommended.  See your Windows
	  documentation for more information.
	
	* Defragment ("clean up") your hard disk by running a
	  defragmentation program such as DEFRAG, which comes with
	  MS-DOS version 6 or higher.
	
	* If you are running Dangerous Creatures on a 256 color display try
	  switching to the Windows VGA driver.  For instructions on how to
	  change your Windows display consult your Windows documentation.
	
	CD-ROM PROBLEMS
	==================
	
	NOTE - Do not remove the Dangerous Creatures compact disc from your
	CD-ROM drive while Dangerous Creatures is in the process of playing a
	sound or movie, or is displaying a new picture, or is running in Slide
	Show mode.
	
	If the Dangerous Creatures program cannot find the data files that it
	needs from the Dangerous Creatures compact disc, you'll see a message
	that asks you to select the drive containing the files. To find the
	source of the problem, do the following:
	
	* Make sure the Dangerous Creatures compact disc is correctly
	  inserted into the CD-ROM drive.
	
	* Make sure that the Dangerous Creatures program is looking
	  for the compact disc on the correct drive.  Check to see if
	  the drive letter for your CD-ROM drive has changed.  You can
	  use the Windows File Manager to determine which drive letter
	  is assigned to the CD-ROM drive.  The Select Drive command in
	  the Disk menu will say "CD-ROM" next to the CD-ROM drive letter.
	
	* If you have an external CD-ROM drive, make sure that the drive
	  is connected to your computer, plugged in, and turned on.  If
	  you still see the error message after checking the points
	  above, check the documentation that came with your CD-ROM
	  drive or contact the company that supplied the drive.
	
	* Make sure that your CD-ROM drive is MPC-compatible.
	 MPC-compatible drives meet the following criteria:
	    1. An average seek time of less than one second;
	    2. A transfer rate of 150KB per second while using less than
	        40% of the CPU bandwidth.
	
	Check the documentation that came with your CD-ROM drive to make sure
	it meets these requirements. A CD-ROM drive that does not meet the MPC
	specifications will exhibit slow performance and/or "Audio
	blips/Interruptions" when sound is played.
	
	PRINTING AND COPYING
	=======================
	The screens in Dangerous Creatures are large color pictures. Depending
	on the type of printer you have, printing a picture of the screen may
	take several minutes.  Also, screen resolution and printer resolution
	are often not the same, so the resulting printout may not match the
	quality you see on the screen.
	
	You should be able to print grayscale images from Dangerous Creatures.
	If you have a black and white laser printer you might need to upgrade
	your printer driver.  Call the dealer from whom you bought the printer
	or the printer manufacturer.  It is also possible to print Dangerous
	Creatures screens in color on a color printer.
	
	Some Dot-matrix printers may not print pictures properly with the "Low
	/ Faster" quality setting in the Print Dialog. On these printers
	change the quality setting in the Print Dialog to "High / Slower".
	
	Because the pictures can be quite large, you may have difficulty
	copying or printing in low-memory conditions.  In this case, close all
	other unnecessary running applications and try again.
	
	VIDEO DISPLAY PROBLEMS
	========================
	Dangerous Creatures will run in 16-color or 256-color screen mode.
	The program will automatically detect which mode you are running and
	display pictures accordingly.  If your computer is running in 16-color
	mode, and the video card will support 256 colors, you can run the
	Windows Setup program to change the video driver.  This will enhance
	the image quality of Microsoft Dangerous Creatures.  For more
	information on changing video drivers, check your Windows
	documentation.
	
	ATI PROBLEMS
	=============
	Microsoft Dangerous Creatures is incompatible with some advanced
	features used by some video cards such as the Mach32 chip set running
	the ATI drivers.  For Dangerous Creatures to run on the ATI driver,
	the "256 color palette" control in the "Advanced features" of the "ATI
	Control Panel" needs to be set to ON.  For more information, see the
	documentation for your video card.
	
	PROBLEMS WITH THE DISPLAY IN DANGEROUS CREATURES
	=================================================
	If you encounter problems displaying images or videos when running
	Microsoft Dangerous Creatures, check the currently installed video
	driver:
	
	1. Run the Windows Setup application.
	2. Locate the Display driver item in the application window.
	
	If the Display driver item is VGA:
	  Try running Windows in Standard Mode by typing "WIN /S" from the
	  system prompt.
	  If standard mode Windows works, try starting Windows in enhanced
	  mode with the following command:
	
	         WIN /D:XV
	
	If this solves the problem, make the following modifications to your
	SYSTEM.INI file in the [386Enh] section:
	
	  EMMEXCLUDE=A000-EFFF
	  VIRTUALHDIRQ=OFF
	
	If the Display driver item is NOT VGA:
	
	1. Run the Windows Setup application.
	2. Choose Change System Settings from the Options menu.
	3. Change the Display setting to VGA.
	4. Choose OK and restart Windows.
	5. Run Microsoft Dangerous Creatures and determine if the display
	   problems still occur. If the problem still exists, follow the
	   suggestions described for VGA drivers, above.
	
	If the problem is solved, this indicates that your original video
	driver selection was experiencing problems rendering images in
	Dangerous Creatures.  You might want to consider choosing another
	video driver (if available) provided by your video card manufacturer.
	To do so, run the Windows Setup application.  If the problem persists,
	contact your video card manufacturer for updated video drivers.
	
	AUDIO PROBLEMS
	===============
	Audio problems can have many causes.  Other applications that play
	sounds may interrupt sounds in Dangerous Creatures, because your
	computer cannot play two sounds simultaneously.  This is generally a
	temporary clash that will resolve itself.  However, a few applications
	that play sounds, such as some screen savers, may remove audio
	capability from all other Windows applications.  If you suspect you
	have such an application, deactivate it or do not run it while running
	Dangerous Creatures.
	
	SOUNDS PLAY, BUT NOT VERY WELL
	===============================
	Sounds that are distorted or "fuzzy" have several possible causes.
	The most likely one is simply that your speakers are not of high
	quality.  Low frequency sounds may not reproduce well on some
	equipment.
	
	It is also possible that the software settings on your sound board are
	causing distortion.  For example, if the sound card volume or "WAVE
	file input" is set to near its maximum, it will produce amplification
	distortion, just as it would on a stereo system.  To find out how to
	change your sound board settings, check the documentation that came
	with your sound board.
	
	Your CD-ROM drive should be MPC-compatible.  MPC-compatible drives
	meet the following criteria:
	
	1. An average seek time of less than one second;
	2. A transfer rate of 150KB per second while using less than 40% of
	   the CPU bandwidth.
	
	Check the documentation that came with your CD-ROM drive to make sure
	it meets these requirements.  An incompatible CD-ROM drive may work;
	however, it may produce low-quality audio or cause the sound to be
	interrupted while playing.
	
	SOUND DOESN'T PLAY AT ALL
	==========================
	If you don't hear any sounds, make sure that the volume is set to an
	audible level.
	
	If the volume is set to an audible level and you still hear no sounds
	at all, something may be wrong with your sound board setup.  Check to
	see that the drivers are installed correctly and, if necessary,
	reinstall them.  To determine if the sound drivers are installed,
	check the Drivers section of the Windows Control Panel.  For more
	information on installing your sound drivers, refer to the
	documentation that came with your sound card.  If you have any
	problems, contact your sound board manufacturer for assistance.
	
	Please note that Dangerous Creatures requires an MPC-compatible sound
	board and is not intended to run with drivers which use the PC
	speaker, such as the unsupported "PC Speaker" driver.  Such a driver
	will in most cases not play any sounds, and if the driver setup option
	"Enable Interrupts" is not checked, the system may lock up.  Check the
	"Drivers" configuration in your Windows Control Panel.  If you have
	both a sound board and the PC Speaker driver installed, it is
	recommended that you remove the PC Speaker driver.
	
	MEDIA VISION CARDS
	===================
	A small number of Media Vision sound card drivers (Pro Audio -
	Spectrum cards) may have problems with sound in Dangerous Creatures.
	If you have a Media Vision card and do not hear sounds or are having
	other sound problems, you might require updated drivers.  Contact
	Media Vision for current driver information.
	
	If you are running Microsoft Dangerous Creatures on an EISA machine
	and experience "scratchy" audio, try changing the DMA channel on the
	sound card to DMA 7.
	
	RUNNING UNDER MICROSOFT WINDOWS NT
	====================================
	There is one potential problem with Dangerous Creatures running under
	Windows NT version 3.1.  Because there is no VGA support for Dangerous
	Creatures under Windows NT version 3.1, you need to be using a 256-
	color VGA or better display to use Dangerous Creatures.
	
	DANGEROUS CREATURES VIDEOS
	============================
	The Dangerous Creatures video clips play automatically when opening a
	video popup.  To play the video again after it has finished, click the
	video frame on the screen.
	
	If your system has a 256-color VGA display or better, the Dangerous
	Creatures videos play in a small frame.  However, due to the limited
	resolution of 16-color VGA displays, videos play in full screen mode
	on those displays.  To play videos in a small frame on a 16-color VGA
	display change the following line in the MSDANGER.INI file found in
	your Windows directory.
	
	VideoInWindow=0
	
	to:
	
	VideoInWindow=1
	
	Additional query words: kbhowto multi media multimedia multi-media
	
	======================================================================
	Keywords          :  
	Technology        : kbHomeProdSearch kbZNotKeyword kbDangerousCreatures
	Version           : WINDOWS:1.0
	
	=============================================================================
	

{% endraw %}
