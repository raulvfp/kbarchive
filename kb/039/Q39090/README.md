---
layout: page
title: "Q39090: Shapes.exe Aligns Logical/Physical Coordinate Systems"
permalink: /kb/039/Q39090/
---

## Q39090: Shapes.exe Aligns Logical/Physical Coordinate Systems

{% raw %}

	Article: Q39090
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): kbfile kbsample kbSDKWin16
	Last Modified: 04-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The text below explains how to use the following functions in the Microsoft
	Windows operating system: SetViewportExt(), SetViewportOrg(), SetWindowExt(),
	and SetWindowOrg(). The explanation is based on the SHAPES sample application
	that was provided with the Microsoft Windows SDK versions 2.x. A version of this
	sample for Windows 3.0 and later is available in the Microsoft Download Center.
	
	MORE INFORMATION
	================
	
	The following file is available for download from the Microsoft Download
	Center:
	
	  Shapes.exe
	  (http://download.microsoft.com/download/platformsdk/file63/3.1/W31/EN-US/Shapes.exe)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	An application uses the SetViewportExt(), SetViewportOrg(), SetWindowExt(), and
	SetWindowOrg() to align the two separate coordinate systems that the Windows
	graphics device interface (GDI) provides. SetWindowOrg() and SetViewportOrg()
	provide a one-to-one mapping of the two specified origin points (one in each
	coordinate system). The SetWindowExt() and SetViewportExt() functions instruct
	GDI how much to stretch (or compress) the coordinate system after mapping the
	two specified points to each other.
	
	The following code, drawn from the SHAPES sample, maps point (-10, 110) in the
	logical coordinate system to point (0, 0) in the client coordinate system. Then
	the code sets the width of the viewport to 120 logical units and the height of
	the viewport to -120 logical units.
	
	     RECT ClientRect;
	
	     GetClientRect(hDC, ClientRect);
	     SetWindowOrg(hDC, -10, 110);
	     SetViewportOrg(hDC, 0, 0);
	     SetWindowExt(hDC, 120, -120);
	     SetViewportExt(hDC,
	
	                    (short)(ClientRect.right - ClientRect.left),
	                    (short)(ClientRect.bottom - ClientRect.top));
	
	Negative coordinate scaling is required because the specified origin point is
	above the displayed image. These concepts are perhaps best illustrated on graph
	paper. Consider the following example. In the logical coordinate system, an
	image of a star starts in the upper-left quadrant of the coordinate system,
	between (-10, 110) and (110, -10). Mark the specified origin (-10, 110) on the
	graph paper. To include the image of the star in the viewport, the viewport
	"extent" must include 120 units to the right (positive x direction) and 120
	units down (negative y direction). The specified viewport extents provide the
	required viewport.
	
	In the example, the left and top members of the ClientRect data structure are
	always zero. The subtraction is unnecessary but included to demonstrate how the
	application aligns the rectangles in the logical and client coordinate systems.
	
	To reduce the size of the star, reduce the size of the viewport by reducing the
	size of the arguments to SetViewportExt(), or increase the amount of logical
	area mapped into the viewport by increasing the arguments to SetWindowExt().
	
	The easiest method of becoming familiar with these functions is to change only
	one argument value at a time, and change it by only a small amount. For example,
	start by changing the preceding code to include the following:
	
	     SetWindowOrg(hDC, -30, 110);
	
	Changing the window origin in this manner trims some of the right side of the
	star from the screen. Change the window origin back to its original location,
	then change other values. You may need to change the viewport coordinates by a
	larger amount than the window coordinates to see the changes.
	
	Changing one coordinate at a time is effective only in the MM_ANISOTROPIC mapping
	mode, which allows the units in the coordinate system to be rectangular rather
	than square. An application can change units on the y-axis without changing the
	x-axis, and vice versa. In contrast, the MM_ISOTROPIC mapping mode enforces
	square units, with an equivalent measure along each axis.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbfile kbsample kbSDKWin16 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK310
	Version           : WINDOWS:3.1
	
	=============================================================================
	

{% endraw %}
