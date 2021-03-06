---
layout: page
title: "Q196429: WD97: Can't Underline Equation Field Below Text Baseline"
permalink: /kb/196/Q196429/
---

## Q196429: WD97: Can't Underline Equation Field Below Text Baseline

{% raw %}

	Article: Q196429
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta kbfield word97
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A fraction, such as a/b, that is created by using the following equation field,
	does not display or print underline formatting:
	
	     {EQ \f(a,b)}
	
	CAUSE
	=====
	
	The field result extends into the baseline.
	
	WORKAROUND
	==========
	
	Use one of the following workarounds to position the equation so that the
	underline formatting will be displayed and will print.
	
	Method 1: Use Equation Editor
	-----------------------------
	
	Create the equation using Equation Editor, and then underline the Equation Editor
	object.
	
	NOTE: If you need to adjust the position of the equation, click to select the
	equation object, and then on the Format menu, click Font. Click to select the
	Character Spacing tab, change the Position box to Raised, and then click OK.
	
	Method 2: Use an Equation Field
	-------------------------------
	
	Create an equation field that places the result above the baseline.
	
	For example, to create the fraction a/b, create the following equation:
	
	     {EQ b\d\ba8()\s\up20({EQ _\d\ba8()\s\up5(a)})}
	
	In this equation, EQ represents the field name, Equation. Notice that the second
	equation, {EQ _\d\ba8()\s\up5(a)}, is nested inside the first equation. This
	second equation creates a fraction, "a" over "_". The "_" is included to provide
	the horizontal bar that separates the numerator from the denominator. The
	denominator is created in the first equation, {EQ b\d\ba8()\s\up20(<nested
	equation>)}.
	
	Within each equation, the \d\ba8() moves the preceding characters, "b" and "_",
	respectively, horizontally to the left by 8 points.
	
	The \s\up20(<nested equation>) and \s\up5(a) superscripts the corresponding
	nested equation or character by 20 points and 5 points, respectively.
	
	Notice that the numerator and denominator positions are in opposite positions
	from their position in the {EQ \f(a,b) equation described in the "Symptoms"
	section of this article.
	
	NOTE: The point sizes used here can be adjusted upward or downward to properly
	adjust your text.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article.
	
	This problem has been corrected in Word 2000.
	
	Additional query words: formula underscore doesn't
	
	======================================================================
	Keywords          : kbdta kbfield word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
