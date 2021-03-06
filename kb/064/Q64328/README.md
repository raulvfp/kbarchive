---
layout: page
title: "Q64328: Owner-Draw: OdButton.exe - 3-D Push Button"
permalink: /kb/064/Q64328/
---

## Q64328: Owner-Draw: OdButton.exe - 3-D Push Button

{% raw %}

	Article: Q64328
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.0,3.1
	Operating System(s): 
	Keyword(s): kbfile kbsample kbButton kbCtrl kbOSWinNT kbGrpDSUser kbOSWin
	Last Modified: 10-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Win32 Software Development Kit (SDK) 
	- Microsoft Windows Software Development Kit (SDK) versions 3.0, 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	An owner-draw button can be defined and drawn to provide any desired appearance,
	even to mimic the three-dimensional push buttons of Windows version 3.0. With an
	owner-draw button, the application can control the button face color, unlike a
	standard push button, which always has a gray face.
	
	MORE INFORMATION
	================
	
	The following files are available for download from the Microsoft Download
	Center:
	
	OdButton.exe
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	
	The ODBUTTON sample source code can be used as a template for creating other
	applications. The main task involves creating appropriate bitmaps.
	
	Under Windows 2.x, an application can change the color of the button face by
	processing WM_CTLCOLOR messages. This functionality is not available in Windows
	3.0. However, the more powerful owner-draw feature can be used to achieve the
	same effect.
	
	Like a Windows 3.0 standard push button, this sample owner-draw button indicates
	that it has the focus by drawing a dashed, black rectangular border around the
	button text. This is accomplished by using the new Windows 3.0 function,
	DrawFocusRect(). Like the text of the button, the focus rectangle must also be
	shifted right and down two pixels when the button is pressed.
	
	Bitmaps are created in a fixed size, in pixels, regardless of the display
	resolution used. An application can determine which display is in use by reading
	the SYSTEM.INI file. Two alternatives are available to create buttons that are
	an appropriate size on different displays, as follows:
	
	1. Create different pairs of default/pressed bitmaps for each display resolution
	  the application is targeted (for example, Hercules monochrome, CGA, EGA, VGA,
	  super VGA, and 8514).
	
	2. Create separate bitmaps for the borders of the button and for the button
	  faces. During the initialization of the application, make four calls to
	  StretchBlt(). The first call should modify the left and right borders
	  vertically. The second call should change the top and bottom borders
	  horizontally. The third and fourth calls should modify each button face
	  bitmap both horizontally and vertically. Doing separate calls eliminates
	  distortion to the border widths as a display-specific bitmap is created.
	
	Apart from the information discussed above, owner-draw buttons are handled like
	other owner-draw controls. However, Windows does not send the application a
	WM_MEASUREITEM message to define the dimensions of the button control
	dynamically. The dimensions of the owner-draw button are specified in a dialog
	box template or CreateWindow() call, similar to the dimensions of nonowner-draw
	buttons.
	
	Like other owner-draw controls, the application draws the owner-draw button in
	response to a WM_DRAWITEM message. Drawing should take into account the
	selection and focus states of the control, as well as the normal state without
	either selection or focus.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbfile kbsample kbButton kbCtrl kbOSWinNT kbGrpDSUser kbOSWin 
	Technology        : kbWin32SDKSearch kbAudDeveloper kbWin3xSearch kbSDKSearch kbWin32sSearch kbWinSDKSearch kbWinSDK300 kbWinSDK310
	Version           : WINDOWS:3.0,3.1
	
	=============================================================================
	

{% endraw %}
