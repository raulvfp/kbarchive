---
layout: page
title: "Q108717: BUG: Resource Manager Error When Printing Lots of Fonts"
permalink: /kb/108/Q108717/
---

## Q108717: BUG: Resource Manager Error When Printing Lots of Fonts

{% raw %}

	Article: Q108717
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS: 2.5x,2.6x,3.0,3.0b,5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbbuglist
	Last Modified: 17-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 5.0a, 6.0 
	- Microsoft FoxPro for Windows, versions 2.5x, 2.6x 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When FoxPro is printing a large number of fonts under Windows 3.x (16-bit
	Windows), FoxPro displays the following error message:
	
	  Resource Manager Internal Consistency Error
	
	Additionally, Visual FoxPro then displays the following error message:
	
	  Win32s - Error Unhandled Exception detected. Application will be terminated.
	
	NOTE: Visual FoxPro 3.0b for Windows prints a much greater number of fonts than
	Visual FoxPro 3.0 for Windows does before displaying the error message.
	
	CAUSE
	=====
	
	FoxPro is not properly releasing graphics device interface (GDI) resources under
	Windows.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	The following program demonstrates the problem:
	
	  SET TALK OFF
	  CLEAR
	  m.points = 10
	  @ 12,20 SAY 'Enter the point size ' GET m.points PICTURE '99'
	  READ
	  @ 12,0
	  @ 12,30 SAY 'Printing'
	  SET CONSOLE OFF
	  IF afont[FONTS]
	     SET PRINT ON
	     _PLINENO = 56
	     m.counter = 1
	     m.numfonts = ALEN(fonts,1)
	     DO WHILE m.counter <= m.numfonts
	        m.this_font = LTRIM(fonts(m.counter))
	        SET CONSOLE ON
	        @ 12,39 SAY SPACE(20)
	        @ 12,39 SAY m.this_font
	        SET CONSOLE OFF
	        AFONT(sizes,(m.this_font))
	        IF _PLINENO > 52
	           DO rpthead
	        ENDIF
	        ?
	        ? 'This is a 10 point sample of ' + m.this_font
	        IF ALEN(sizes) = 1 .AND. TYPE('sizes(1)') = 'L' .AND. sizes(1) = .T.
	           ?? '. This is a scalable font.'
	        ENDIF
	        ?   'ABCDEFGHIJKLMNOPQRSTUVWXYZ' + ;
	            'abcdefghijklmnopqrstuvwxyz' + ;
	            '1234567890!@#$%^& ; ())' FONT m.this_font,m.points
	        ? 'This is ' + m.this_font + ' bold.'
	        ?   'ABCDEFGHIJKLMNOPQRSTUVWXYZ' + ;
	            'abcdefghijklmnopqrstuvwxyz' + ;
	            '1234567890!@#$%^& ; ())' FONT m.this_font,m.points STYLE 'B'
	        ? 'This is ' + m.this_font + ' italic.'
	        ?   'ABCDEFGHIJKLMNOPQRSTUVWXYZ' + ;
	            'abcdefghijklmnopqrstuvwxyz' + ;
	            '1234567890!@#$%^& ; ())' FONT m.this_font,m.points STYLE 'I'
	        ? 'This is ' + m.this_font + ' underline.'
	        ?   'ABCDEFGHIJKLMNOPQRSTUVWXYZ' + ;
	            'abcdefghijklmnopqrstuvwxyz' + ;
	            '1234567890!@#$%^& ; ())' FONT m.this_font,m.points STYLE 'U'
	        m.counter = m.counter + 1
	     ENDDO
	     EJECT
	     SET PRINT OFF
	     SET CONSOLE OFF
	  ENDIF
	  RETURN
	
	  PROCEDURE rpthead
	  EJECT
	  _PLINENO = 1
	  ?
	  ? 'A LISTING OF YOUR AVAILABLE WINDOWS FONTS' AT 25
	  ? '-----------------------------------------' AT 25
	  ?
	  RETURN
	
	Additional query words: VFoxWin FoxWin 2.50 2.50a 2.50b 2.60 2.60a buglist2.50 buglist2.50a buglist2.50b buglist2.60 buglist3.00 kbvfp300 kbvfp500 kbvfp500a kbvfp600 buglist3.00b errmsg err msg ice
	
	======================================================================
	Keywords          :  kbbuglist
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbVFP300 kbVFP300b kbVFP500 kbVFP600 kbVFP500a
	Version           : WINDOWS: 2.5x,2.6x,3.0,3.0b,5.0,5.0a,6.0
	
	=============================================================================
	

{% endraw %}
