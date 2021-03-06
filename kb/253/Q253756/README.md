---
layout: page
title: "Q253756: Availability of Universal Serial Bus Support in Windows 95"
permalink: /kb/253/Q253756/
---

## Q253756: Availability of Universal Serial Bus Support in Windows 95

{% raw %}

	Article: Q253756
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:95
	Operating System(s): 
	Keyword(s): kbenv osr2 win95
	Last Modified: 29-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	- Microsoft Windows 95 OEM Service Release, versions 2.0, 2.1, 2.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes the availability of Universal Serial Bus (USB) support in
	Windows 95.
	
	MORE INFORMATION
	================
	
	USB support for Windows 95 is available in Original Equipment Manufacturer (OEM)
	versions of Windows 95. If you purchased Windows 95 boxed product (the full or
	upgrade version) from a retail store, you have a retail version of Windows 95.
	Retail versions of Windows 95 cannot be upgraded to OEM versions, and there is
	no separate download to enable USB support in any version of Windows 95. If you
	have an OEM version of Windows 95 and you want to enable USB support, contact
	your OEM.
	
	To determine the version of Windows 95 you are running:
	
	1. Click Start, point to Settings, click Control Panel, and then double-click
	  System.
	
	2. Click the General tab.
	
	3. Locate the version number under the System heading, and then see the
	  following table.
	
	+-----------------------------------------------------------------------------------------------------------------------+
	| Release                 | Version                    | File dates       | USB support | Is USB support downloadable?* | 
	+-----------------------------------------------------------------------------------------------------------------------+
	| Windows 95 retail       | 4.00.950                   | 7/11/95          | no          | no                            | 
	+-----------------------------------------------------------------------------------------------------------------------+
	| Windows 95 retail SP1   | 4.00.950A                  | 7/11/95          | no          | no                            | 
	+-----------------------------------------------------------------------------------------------------------------------+
	| OEM Service Release 1   | 4.00.950A                  | 7/11/95          | no          | no                            | 
	+-----------------------------------------------------------------------------------------------------------------------+
	| OEM Service Release 2   | 4.00.1111 (4.00.950B)      | 8/24/96          | no          | no                            | 
	+-----------------------------------------------------------------------------------------------------------------------+
	| OEM Service Release 2.1 | 4.03.1212-1214 (4.00.950B) | 8/24/96-8/27/97  | yes         | n/a                           | 
	+-----------------------------------------------------------------------------------------------------------------------+
	| OEM Service Release 2.5 | 4.03.1214 (4.00.950C)      | 8/24/96-11/18/97 | yes         | n/a                           | 
	+-----------------------------------------------------------------------------------------------------------------------+
	
	*If you have a version of Windows 95 that does not have USB support, and you want
	USB support, Microsoft recommends that you upgrade to Windows 98 Second
	Edition.
	
	
	4. If you are running an OEM version of Windows 95, the Product ID number under
	  the Registered To heading typically contains 20 digits. If digits 6, 7, and 8
	  contain the letters "OEM," your version of Windows 95 is an OEM version. For
	  example, the following sample Product ID number indicates an OEM
	  installation:
	
	  12345-OEM-6789098-76543
	
	Original Equipment Manufacturer (OEM) Version Identification
	------------------------------------------------------------
	
	Windows 95 may have been preinstalled on your computer. These installations are
	referred to as OEM installations. An OEM Service Release (for example, OSR2) is
	an updated version of a product for PC manufacturers (OEMs) to preinstall on new
	PCs. The purpose is to allow OEMs to install an integrated Windows 95 product
	that contains the latest available individual updates and supports recent
	advances in hardware that require core operating system support.
	
	Additional OEM Information
	--------------------------
	
	- In Windows 95 OEM Service Release 2 (OSR2), 2.1 (OSR2.1) and 2.5 (OSR2.5),
	  not all files have the version stamp that is listed in the table. In OSR2.1
	  and OSR2.5, only files that were updated to provide support for the Win32
	  Driver Model (WDM) and USB may have this version stamp (the other files have
	  the same version stamps as the corresponding OSR2 files).
	
	  You can view file version information by right-clicking a file in Windows
	  Explorer, clicking Properties on the menu that appears, and then clicking the
	  Version tab. If there is no Version tab, there is no version information
	  available for that file.
	
	- Updates to Windows 95 OEM OSR2 generally have a version of 4.00.1112 or
	  later.
	
	- To determine whether you are running OSR2.1, check for "USB Supplement to
	  OSR2" in the list of installed programs in the Add/Remove Programs tool in
	  Control Panel, and check for version 4.03.1212 of the Ntkern.vxd file in the
	  Windows\System\Vmm32 folder.
	
	- If you are running OSR2.5 and you uninstall the USB Supplement by using the
	  Add/Remove Programs tool in Control Panel, the version number changes to
	  4.00.950b on the General tab in System properties.
	
	NOTE: All versions of Microsoft Windows 98 include USB support.
	
	Additional query words: OSR1 OSR 2.1 2.5
	
	======================================================================
	Keywords          : kbenv osr2 win95 
	Technology        : kbWin95search kbOPKSearch kbZNotKeyword3 kbWin95OPKOSR25 kbWin95OPKOSR210
	Version           : WINDOWS:95
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
