---
layout: page
title: "Q114136: BUG: FoxPro Math-Precision Problems with SET DECIMALS"
permalink: /kb/114/Q114136/
---

## Q114136: BUG: FoxPro Math-Precision Problems with SET DECIMALS

{% raw %}

	Article: Q114136
	Product(s): Microsoft FoxPro
	Version(s): MS-DOS:2.0,2.5x,2.6x; WINDOWS:2.5x,2.6x,3.0,3.0b,5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbvfp500aBUG kbvfp250bug kbvfp250aBUG kbvfp250bBUGkbbuglist
	Last Modified: 09-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 5.0a, 6.0 
	- Microsoft FoxPro for Windows, versions 2.5x, 2.6x 
	- Microsoft FoxPro for MS-DOS, versions 2.0, 2.5x, 2.6x 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	SET DECIMALS TO 2 changes the result when a numeric expression that evaluates to
	a decimal value is used in a comparison. For example, type the following in the
	Command window:
	
	     SET DECIMAL TO 18
	     ? 12/8888888 = 0     && FoxPro returns FALSE
	   
	     SET DECIMALS TO 2
	     ? 12/8888888 = 0     && FoxPro returns TRUE
	
	Under dBASE IV, both of these expressions will return FALSE.
	
	In FoxPro version 2.6a, a similar decimal-precision problem occurs when any whole
	number is used in math problems. For example:
	
	     SET DECIMALS TO 18
	     ?12/8888888       && dBASE returns 0.00000135... but FoxPro returns 0
	   
	     ?12/88888888      && dBASE returns 0.0000000000... but FoxPro returns 0
	   
	     ?12.0/8888888     && dBASE returns 0.00000135... but FoxPro returns 0
	
	However the behavior of FoxPro versions 2.5x, 2.6 and Visual FoxPro is closer to
	that of dBase. For example:
	
	     SET DECIMALS TO 18
	     ?12/8888888       && FoxPro returns 0.000001350000135000
	   
	     ?12/88888888      && FoxPro returns 0
	   
	     ?12.0/8888888     && FoxPro returns 0.000001350000135000
	
	RESOLUTION
	==========
	
	If you need greater precision in FoxPro, set the SET DECIMALS command to a
	higher value. For greater precision with constants, replace the constants with
	memory variables, so that FoxPro performs the calculation at run time.
	
	If you must use constants, express them in the precision that is desired. For
	example, use this expression
	
	     ?12.0000000/88888888  && FoxPro returns 0.00000135...
	
	rather than this one:
	
	     ?12/88888888  && FoxPro returns 0.0000000000...
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article.
	
	MORE INFORMATION
	================
	
	NOTE: FoxPro returns a zero when the first significant digit is in the seventh
	position to the right of the decimal; for example, 0.0000001.
	
	
	Additional query words: math set decimal kbFP250 kbFP260 kbvfp300 kbvfp500 kbvfp600
	
	======================================================================
	Keywords          : kbvfp500aBUG kbvfp250bug kbvfp250aBUG kbvfp250bBUG kbbuglist
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro200DOS kbVFP300 kbVFP300b kbVFP500 kbVFP600 kbVFP500a
	Version           : MS-DOS:2.0,2.5x,2.6x; WINDOWS:2.5x,2.6x,3.0,3.0b,5.0,5.0a,6.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
