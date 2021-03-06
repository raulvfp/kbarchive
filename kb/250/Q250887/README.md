---
layout: page
title: "Q250887: BUG: Bad Code Generated by Global Optimizations w/ Bitwise Shift"
permalink: /kb/250/Q250887/
---

## Q250887: BUG: Bad Code Generated by Global Optimizations w/ Bitwise Shift

{% raw %}

	Article: Q250887
	Product(s): Microsoft C Compiler
	Version(s): 6.0SP3
	Operating System(s): 
	Keyword(s): kbCodeGen kbCompiler kbVC600 kbVS600sp3bug kbDSupport kbGrpDSVCCompiler
	Last Modified: 07-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0sp3 
	- Microsoft Visual C++, 32-bit Professional Edition, version 6.0sp3 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0sp3 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	For builds that use global optimizations (/Og), an if statement may never be
	executed when the bitwise shift operator, >> or <<, is called after
	the if statement.
	
	NOTE: Both the "maximize speed" (/O2) and "minimize size" (/O1) optimizations are
	composite optimization switches that include /Og.
	
	CAUSE
	=====
	
	The optimizer has incorrectly removed a CMP instruction.
	
	RESOLUTION
	==========
	
	To resolve this problem, disable the global optimizations.
	
	Global optimizations can be turned off on a function-by-function basis by using
	the #pragma optimize("g",off) directive.
	
	Global optimizations can also be turned off by adding /Og- to a source file or to
	a project's settings.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	  //test.cpp
	  // Compiler options are cl /GX /Og test.cpp.
	
	  #include <stdio.h>
	
	  //Uncomment the following line to turn off global optimizations:
	  //#pragma optimize("g",off) 
	  void ShiftValues (const char * pEncoded)
	  {
	  	size_t nCount = 0;
	  	size_t nBits = 0;
	  	size_t x = 0;
	  	while (pEncoded[nCount] != '=')
	  	{
	  		nBits += 6;
	  		printf("added 6, nBits now %d\n", nBits);
	  		if (nBits >= 8)
	  		{
	  			printf("%x\n", (0 << (nBits - 8)));
	  			nBits -= 8;
	  			printf("subtracted 8, nBits now %d\n", nBits);
	  		}
	  		nCount++;
	  	}
	  }
	  // Uncomment the following line to turn global optimizations back on:
	  //#pragma optimize("g",on) 
	
	  void main()
	  {
	  	ShiftValues ("AA=");
	  }
	
	  Correct output with global optimizations turn off:<BR/>
	  added 6, nBits now 6
	  added 6, nBits now 12
	  0
	  subtracted 8, nBits now 4
	
	  Incorrect output with global optimizations turn on:
	  added 6, nBits now 6
	  0
	  subtracted 8, nBits now -2
	  added 6, nBits now 4
	  0
	  subtracted 8, nBits now -4
	
	Additional query words:
	
	======================================================================
	Keywords          : kbCodeGen kbCompiler kbVC600 kbVS600sp3bug kbDSupport kbGrpDSVCCompiler 
	Technology        : kbVCsearch kbAudDeveloper kbVC32bitSearch kbVC600SP3
	Version           : :6.0SP3
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
