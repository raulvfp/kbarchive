---
layout: page
title: "Q66699: LINK Ignores Drive Specification Searching for Libraries"
permalink: /kb/066/Q66699/
---

## Q66699: LINK Ignores Drive Specification Searching for Libraries

{% raw %}

	Article: Q66699
	Product(s): Microsoft Programming Utilities
	Version(s): MS-DOS:5.0x,5.1x,5.3,5.31.009,5.5,5.6; OS/2:5.01.21,5.03,5.05,5.1,5.11,5.13
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 31-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft LINK for MS-DOS, versions 5.0x, 5.1x, 5.3, 5.31.009, 5.5, 5.6 
	- Microsoft LINK for OS/2, versions 5.01.21, 5.03, 5.05, 5.1, 5.11, 5.13 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	A library name can be embedded into an object module (.OBJ) for LINK to use when
	searching to resolve external references. This library name can either be the
	library name itself or the full path to the library. In the case of a full path
	to the library, LINK does not use the drive specifier.
	
	MORE INFORMATION
	================
	
	If a drive specifier is present in a library name embedded in an .OBJ, it is
	intentionally ignored by the linker. This is done to provide compatibility with
	older compilers that automatically attached the drive letter to all library
	records. Therefore, if a library is not located on the default drive, LINK will
	prompt for its location.
	
	For example, with Visual C++ version 1.0 or 1.5, the #pragma comment command is
	used to specify the library. If the following line is used
	
	     #pragma comment (lib, "E:\\MSVC\\LIB\\GRAPHICS.LIB")
	
	the compiler will add a COMENT record to the .OBJ instructing LINK to search the
	MSVC\LIB subdirectory for the library GRAPHICS.LIB. If the current default drive
	happens to be drive C, then LINK will search drive C for the MSVC\LIB directory.
	When the library and/or path is not found, it will prompt for the path to the
	library.
	
	Additional query words: kbinf 5.01.21 5.03 5.05 5.10 5.11 5.13 5.30 5.31.009 5.50 5.60
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbAudDeveloper kbZNotKeyword3 kbLINKSearch kbLINK50xDOSSearch kbLINK510xDOSSearch kbLINK50121DOS kbLINK530DOS kbLINK53109DOS kbLINK550DOS kbLINK560DOS kbLINK503OS2 kbLINK505OS2 kbLINK510OS2 kbLINK511OS2 kbLINK513OS2
	Version           : MS-DOS:5.0x,5.1x,5.3,5.31.009,5.5,5.6; OS/2:5.01.21,5.03,5.05,5.1,5.11,5.13
	
	=============================================================================
	

{% endraw %}
