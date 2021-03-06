---
layout: page
title: "Q81476: MS-DOS Customers Who Want Windows 3.1 EMM386.EXE"
permalink: /kb/081/Q81476/
---

## Q81476: MS-DOS Customers Who Want Windows 3.1 EMM386.EXE

{% raw %}

	Article: Q81476
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.0,5.0a,6.0,6.2,6.21; WINDOWS:3.0,3.0a,3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 19-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 5.0, 5.0a, 6.0, 6.2, 6.21 
	- Microsoft Windows versions 3.0, 3.0a, 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Microsoft Windows versions 3.1 and 3.11 will run in standard mode when
	EMM386.EXE is providing upper memory blocks (UMBs). Microsoft Windows version
	3.0 will not run in standard mode if EMM386.EXE is providing UMBs.
	
	Changes were made in Windows 3.1 to allow Windows to run in standard mode with
	EMM386. There were no changes made EMM386 to support this.
	
	MORE INFORMATION
	================
	
	Standard mode Windows 3.1 is VCPI-compliant; standard mode Windows 3.0 is not.
	VCPI is an industry protocol to allow 386-based memory managers like EMM386 to
	cooperate with 286-protected mode DOS extenders. For example, Lotus 1-2-3 3.x
	and standard mode Windows have built-in DOS extenders. As the first 386-based
	memory managers were LIMulators, VCPI is actually an extension to the
	Lotus-Intel-Microsoft Expanded Memory Specification (LIM EMS).
	
	Microsoft is aware that some third-party companies have released special versions
	of 80386 memory managers that allow a specific release of Windows to run in
	standard mode. Microsoft, however, chose not to change the memory manager;
	rather, we changed Windows to work with any 80386 memory manager that is VCPI
	compliant.
	
	Examples of VCPI compliant 386 memory managers include EMM386, QEMM, 386MAX,
	BLUEMAX, and CEMM. Check your product's documentation for details. Note that if
	the product provides both XMS and EMS memory, the driver must support XMS 3.0,
	not 2.0.
	
	The products included here, QEMM, 386MAX, BLUEMAX, and CEMM, are manufactured by
	vendors independent of Microsoft; we make no warranty, implied or otherwise,
	regarding these products' performance or reliability.
	
	Additional query words: 3.0a 3.00 3.00a 3.10 5.00 5.00a 6.00 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin300 kbWin300a kbWin310 kbWin311 kbMSDOSSearch kbMSDOS621 kbMSDOS620 kbMSDOS600 kbMSDOS500 kbMSDOS500a
	Version           : MS-DOS:5.0,5.0a,6.0,6.2,6.21; WINDOWS:3.0,3.0a,3.1,3.11
	
	=============================================================================
	

{% endraw %}
