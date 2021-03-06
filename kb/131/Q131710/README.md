---
layout: page
title: "Q131710: FIX: TYPE() Returns &quot;&quot; Instead of &quot;U&quot; For OleBoundControl"
permalink: /kb/131/Q131710/
---

## Q131710: FIX: TYPE() Returns &quot;&quot; Instead of &quot;U&quot; For OleBoundControl

{% raw %}

	Article: Q131710
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:3.0b; WINDOWS:3.0,3.0b,5.0
	Operating System(s): 
	Keyword(s): kbcode kbprogramming kbvfp kbvfp300bBUG kbvfp500aFIX kbvfp500bugkbbuglist kbfixlist
	Last Modified: 15-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0 
	- Microsoft Visual FoxPro for Macintosh, version 3.0b 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you run a form containing an OleBoundControl object and the TYPE() function
	attempts to verify the type of an undefined property of the object, the TYPE()
	function returns an empty string ("") instead of the expected "U" value.
	
	RESOLUTION
	==========
	
	If your application uses the return value of the TYPE() function, test for an
	empty value ("") as a return value for all cases where an object uses the
	OleBoundControl as a BaseClass. For example:
	
	  DO CASE
	     CASE <object>.BaseClass="Oleboundcontrol"
	        IF TYPE('<form>.<object>.UndefProp')="U" ;
	           OR TYPE ('<form>.<object>.UndefProp')=""
	           *Place code here
	        ELSE
	           *Place code here
	        ENDIF
	  ENDCASE
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. This problem has been fixed in Visual FoxPro
	5.0a.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Create a form.
	
	2. On the DataEnvironment menu, click Add Table.
	
	3. In the Add Table dialog box, select Tables, and then select the Employee
	  table located in the SAMPLES\DATA directory.
	
	4. Click the OleBoundControl control on the Form Controls toolbar, and place the
	  control on the form. Then modify the ControlSource property of the control to
	  this:
	
	     ControlSource: Employee.Photo
	
	5. Place a command button on the form, and modify its Click event handler to
	  include this code:
	
	     SKIP
	     Thisform.Refresh
	
	6. Save the form as FRMTEST, and run it.
	
	7. Use the following code in the Debug window (for Visual FoxPro 3.x versions)
	  or the Watch window in the Visual FoxPro 5.0 Debugger to verify the return
	  value of the OleBoundControl control:
	
	     TYPE('Frmtest.OleBoundControl1.BadProp') && Property does not exist
	
	Additional query words:
	
	======================================================================
	Keywords          : kbcode kbprogramming kbvfp kbvfp300bBUG kbvfp500aFIX kbvfp500bug kbbuglist kbfixlist
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbVFP300bMac kbVFP300 kbVFP300b kbVFP500
	Version           : MACINTOSH:3.0b; WINDOWS:3.0,3.0b,5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
