---
layout: page
title: "Q242312: HOWTO: Distribute an ADOCE 2.0 Application to a PsPC Device"
permalink: /kb/242/Q242312/
---

## Q242312: HOWTO: Distribute an ADOCE 2.0 Application to a PsPC Device

{% raw %}

	Article: Q242312
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): kbATM kbToolkit kbVBp600 kbOSWinCEsearch kbGrpDSVB
	Last Modified: 24-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows CE Toolkit for Visual Basic 6.0, version 1.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When creating a setup for a Windows CE Toolkit for a Microsoft Visual Basic 6.0
	(VBCE) application targeting Palm-size PCs, the install wizard does not include
	ADOCE 2.0 in the setup; this results in errors after the installation. This
	article discusses the steps necessary to ensure that the application is
	successfully installed.
	
	MORE INFORMATION
	================
	
	To resolve this problem, the distribution package can be manually changed to
	include the ADOCE 2.0 support files. The steps below make the assumption that
	the VBCE project has already been created and compiled to a .vb file.
	
	Step by Step Example
	--------------------
	
	1. Create the installation package using the Application Install Wizard.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q194837 HOWTO: Distribute a Visual Basic Windows CE Application
	
	2. Copy the necessary support files for ADOCE 2.0 from each of the processor
	  specific directories. For example, copy the files from "Windows CE
	  Tools\wce211\ms palm size pc\adoce\mips39" to "package path\Mips 3000 (4K)
	  v2.11."
	
	3. Modify the INF file as follows to include the ADOCE 2.0 support files. (The
	  INF file for Project1 would be Project1.inf.) Change all the processor
	  specific sections for CESelfRegister, SourceDisksFiles, and the Source list
	  at the end of the file. The following is an example of the Mips3x section:
	
	[DefaultInstall.Mips 3000 (4K) v2.11]
	CopyFiles=Files.Mips 3000 (4K) v2.11
	CESelfRegister=vbscript.dll,pvbhost2.dll,pvbform2.dll, adoce.dll, 
	adocedb.dll, adocereg.dll, adoceres.dll, adosync.dll
	
	[CEDevice.Mips 3000 (4K) v2.11]
	ProcessorType=4000
	
	[SourceDisksNames.Mips 3000 (4K) v2.11]
	3= ,"Mips 3000 (4K) v2.11 Files",,Mips 3000 (4K) v2.11
	
	[SourceDisksFiles.Mips 3000 (4K) v2.11]
	pvbhost2.dll=3
	pvbload.exe=3
	vbscript.dll=3
	vbsen.dll=3
	pvbform2.dll=3
	adoce.dll=3 
	adocedb.dll=3
	adocereg.dll=3
	adoceres.dll=3
	adosync.dll=3
	
	[Files.Mips 3000 (4K) v2.11]
	pvbhost2.dll,,0x80000000
	pvbload.exe
	vbscript.dll,,0x80000000
	vbsen.dll
	pvbform2.dll,,0x80000000
	adoce.dll 
	adocedb.dll
	adocereg.dll
	adoceres.dll
	adosync.dll
	
	4. Repackage the .cab files using cabwiz.exe as described in the readme.txt file
	  in the package directory.
	
	5. Copy the resulting .cab files to the CD1 directory.
	
	6. Test the setup.
	
	The CD1 directory now contains a distribution including the required ADOCE 2.0
	file.
	
	REFERENCES
	==========
	
	For additional information, please click the article numbers below to view the
	articles in the Microsoft Knowledge Base:
	
	  Q238947 FILE: Msadoce2.exe Installs ADO for Windows CE SDK
	
	  Q240435 PATCH: WCELoad.exe Fixes ActiveX Hanging Problem on Palm-size PC
	
	Additional query words: vbce vbce6 wce
	
	======================================================================
	Keywords          : kbATM kbToolkit kbVBp600 kbOSWinCEsearch kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbWinCETKVBSearch kbWinCESearch kbWinCETK100VB600
	Version           : :1.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
