---
layout: page
title: "Q250059: FIX: Accessing Print Drivers When Issuing SYS(1037) Causes Error"
permalink: /kb/250/Q250059/
---

## Q250059: FIX: Accessing Print Drivers When Issuing SYS(1037) Causes Error

{% raw %}

	Article: Q250059
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbprint kbPrinting kbReportWriter kbvfp600 kbXBase kbVS600sp3bug kbGrpDSFox kbDSupport
	Last Modified: 11-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0, on platform(s):
	   - the operating system: Microsoft Windows NT 
	   - the operating system: Microsoft Windows 2000 
	   - the operating system: Microsoft Windows 98 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In Microsoft Visual FoxPro Service Pack 3, issuing SYS(1037) followed by either
	GETPRINTER() under Microsoft Windows NT or Windows 2000, or by selecting Cancel
	from the Page Setup dialog box and then the CREATE REPORT FROM command under
	Windows 98 causes FoxPro to close with the following error:
	
	  Fatal Exception: Exception Code = C0000005
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug was corrected in the latest service pack for
	Visual Studio 6.0.
	
	For additional information about Visual Studio service packs, click the article
	numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That a Visual Studio Service Pack Is Installed
	
	You can download the latest Visual Studio service pack from the following
	Microsoft Web site:
	
	  Visual Studio Product Updates
	  (http://msdn.microsoft.com/vstudio/downloads/updates.asp)
	
	MORE INFORMATION
	================
	
	This problem is specific to the previously mentioned commands and operating
	systems and has not been reproduced on Windows 95. Nor does it happen with the
	original release of Visual FoxPro 6.0.
	
	For all the methods listed below to reproduce this problem, make sure you have
	one or more printers set up in the Printers control panel. The printer (or
	printers) can be on a network, local port, or even directed to the File port.
	The printer driver that you use does not appear to make a difference.
	
	Steps to Reproduce Behavior
	---------------------------
	
	Under Windows NT or Windows 2000 (two methods listed):
	
	- GETPRINTER() with SYS(1037):
	
	  1. In the Command window, enter:
	
	  ? SYS(1037)
	
	and press the ENTER key. Press either OK or Cancel to close Page Setup.
	
	  2. Next, enter:
	
	  ? GETPRINTER()
	
	and press the ENTER key.
	
	- GETPRINTER() with Page Setup:
	
	  1. From the File menu, choose the Page Setup command. Click OK or Cancel to
	     close Page Setup.
	
	  2. In the Command window, enter:
	
	  ? GETPRINTER()
	
	and press the ENTER key.
	
	Under Windows 98:
	
	Copy the following code to a .prg file and run it on a Windows 98 machine with
	Visual FoxPro 6.0 Service Pack 3:
	
	  a = SYS(1037)
	  CREATE TABLE dummy2 (dummy C(1))
	  USE IN dummy2
	  CREATE REPORT test FROM dummy2
	  ERASE DUMMY2.dbf
	  ERASE test.frx
	  ERASE test.frt 
	
	Click Cancel when the Page Setup dialog box appears.
	
	Notice that with all the methods above, FoxPro generates the following error and
	then closes.
	
	  Fatal Exception: Exception Code = C0000005
	
	
	Additional query words: sp4
	
	======================================================================
	Keywords          : kbprint kbPrinting kbReportWriter kbvfp600 kbXBase kbVS600sp3bug kbGrpDSFox kbDSupport kbVS600sp4fix kbVS600sp5fix 
	Technology        : kbVFPsearch kbAudDeveloper
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
