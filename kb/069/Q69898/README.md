---
layout: page
title: "Q69898: Overcoming &quot;C4071 No Function Prototype Given&quot; Warning"
permalink: /kb/069/Q69898/
---

## Q69898: Overcoming &quot;C4071 No Function Prototype Given&quot; Warning

{% raw %}

	Article: Q69898
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.0,3.1
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 05-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) versions 3.0, 3.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Code that is compiled using the Microsoft C compiler's warning level 3 (/W3) or
	higher and that calls functions through FARPROC pointers causes the Microsoft C
	compiler to report warning C4071, "No Function Prototype Given."
	
	CAUSE
	=====
	
	Pointers to functions are commonly used when an application explicitly loads
	dynamic-link libraries (DLLs) through the Windows LoadLibrary function. Function
	pointers declared with FARPROC do not inherit function prototype information.
	
	RESOLUTION
	==========
	
	Modify the function pointers declarations to include function prototype
	information.
	
	MORE INFORMATION
	================
	
	The following code sample uses the generic FARPROC far-pointer-to-function data
	type. Compiling the code with Microsoft C at warning level 3 or higher results
	in a C4071 warning:
	
	  FARPROC lpfnErrorProc;
	  lpfnErrorProc = GetProcAddress(hModule, MAKEINTRESOURCE(1));
	  (*lpfnErrorProc)(hWnd, (LPSTR)"Error Message");
	
	However, the following code sample defines custom far-pointer-to- function data
	types which provide information about the function arguments. This code does not
	produce the warning:
	
	     // typedef declarations
	     typedef VOID FAR PASCAL FNERRORPROC(HWND, LPSTR);
	     typedef FNERRORPROC FAR *LPFNERRORPROC;
	
	     // variable declaration
	     LPFNERRORPROC  lpfnErrorProc;
	
	     // variable assignment and indirect function call
	     lpfnErrorProc = GetProcAddress(hModule, MAKEINTRESOURCE(1));
	     (*lpfnErrorProc)(hWnd, (LPSTR)"Error Message");
	
	Additional query words: 3.00 3.10
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK300 kbWinSDK310
	Version           : WINDOWS:3.0,3.1
	
	=============================================================================
	

{% endraw %}
