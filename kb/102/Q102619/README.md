---
layout: page
title: "Q102619: FIX: Member Conversion Function Calling Convention Incorrect"
permalink: /kb/102/Q102619/
---

## Q102619: FIX: Member Conversion Function Calling Convention Incorrect

{% raw %}

	Article: Q102619
	Product(s): Microsoft C Compiler
	Version(s): 1.0,1.5
	Operating System(s): 
	Keyword(s): kbCompiler kbCPPonly kbVCkbbuglist kbfixlist
	Last Modified: 26-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft C/C++ Compiler (CL.EXE), included with:
	   - Microsoft Visual C++, versions 1.0, 1.5 
	   - *EDITOR Please do not choose this product*Microsoft Visual C++ 32-bit Edition* use 241, 265, 225, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	
	After compiling an application with Microsoft C/C++ for MS-DOS, an attempt to
	link the application fails and Microsoft LINK generates the following message:
	
	  error L2029: 'public: __near __pascal CMyclass::operator`int const __near*'
	  (void)const __near' : unresolved external
	
	After compiling an application with Microsoft C/C++ 32-bit Edition, an attempt to
	link the application fails and Microsoft LINK generates the following messages:
	
	  warning LNK4016: unresolved external symbol "??BCMyclass@@QBGPBHXZ (public:
	  __stdcall CMyclass::operator`int const *' (void)const )" error LNK1120: 1
	  unresolved externals
	
	CAUSE
	=====
	
	Microsoft C/C++ compiler version 8.0 and 8.0c for MS-DOS and Windows always uses
	the __cdecl calling convention for functions declared as follows:
	
	     <classname>::operator const <type-specifier> *() const
	
	However, if the compiler command line includes the /Gc compiler option switch,
	the function has the __pascal calling convention. Normally, every member
	function of a class uses the __pascal calling convention without regard to the
	presence of the /Gc compiler option switch.
	
	For example, if you build an application with the Microsoft Foundation Class
	Library and refer to the function CString::operator const char *() const, an
	L2029 error occurs if you specify the /Gc compiler option switch. Because the
	Class Library was built without the /Gc option, the conversion function in the
	library has the __cdecl calling convention. If you build your application with
	the /Gc option switch, it attempts to call the conversion function with the
	__pascal calling convention.
	
	A similar problem occurs in Microsoft C/C++ 32-bit Edition if you specify the /Gz
	compiler option switch. Normally, each class member function uses the thiscall
	calling convention without regard to the presence of the /Gz compiler option
	switch. However, if the compiler command line specifies the /Gz compiler option
	switch, the conversion function uses the __stdcall calling convention.
	
	RESOLUTION
	==========
	
	In Microsoft C/C++ version 8.0 for MS-DOS and Windows, modify the compiler
	command line to remove the /Gc compiler option switch. Doing so compiles the
	conversion function with the __cdecl calling convention. In Microsoft C/C++
	version 8.0 (32-bit), modify the compiler command line to remove the /Gz
	compiler option switch. Doing so compiles the conversion function with the
	thiscall calling convention.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the products listed at the beginning
	of this article. This bug was corrected in Visual C++ version 2.0.
	
	MORE INFORMATION
	================
	
	The code example below demonstrates this problem. Recall that because member
	functions use the __pascal or thiscall calling convention, compiling MAIN.CPP
	with the /Gc or /Gz switches specified or not should not make any difference.
	However, the example shows that a problem does occur.
	
	The code below demonstrates the problem. Recall that member functions use the
	__pascal or thiscall calling convention, and therefore there should be no
	difference between using /Gc or /Gz with MAIN.CPP and not using /Gc or /Gz.
	However, the sample shows that there is a problem.
	
	Sample Code
	-----------
	
	  // TEST.H
	
	  class CMyclass
	  {
	     int * m_pinteger;
	  public:
	     operator const int *() const;
	     operator int();
	  };
	
	  // MAIN.CPP
	
	  /*
	   * Compiler options needed: /Gc for C/C++ for MS-DOS and Windows
	   *                          /Gz for C/C++ for Windows NT
	   */ 
	
	  #include "test.h"
	  void __cdecl main(void)
	  {
	     CMyclass obj;
	     const int *y = obj;
	     const int z = obj;
	  }
	
	  // OTHER.CPP
	
	  /*
	   * Compiler options needed: None (omit /Gc and /Gz)
	   */ 
	
	  #include "test.h"
	
	  CMyclass::operator const int *()const
	  {
	     return m_pinteger;
	  }
	
	  CMyclass::operator int()
	  {
	     return *m_pinteger;
	  }
	
	Additional query words: 1.00 1.50 8.00 8.00c
	
	======================================================================
	Keywords          : kbCompiler kbCPPonly kbVC kbbuglist kbfixlist
	Technology        : kbVCsearch kbAudDeveloper kbCVCComp
	Version           : :1.0,1.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
