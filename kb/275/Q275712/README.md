---
layout: page
title: "Q275712: BUG: Custom Build Step Is Not Applied to New Configuration"
permalink: /kb/275/Q275712/
---

## Q275712: BUG: Custom Build Step Is Not Applied to New Configuration

{% raw %}

	Article: Q275712
	Product(s): Microsoft C Compiler
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbide kbVC600 kbVC600bug kbDevStudio kbDSupport kbGrpDSTools
	Last Modified: 07-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you add a new configuration to a Visual C++ project, a file that used a
	custom build step may not inherit the custom build step in the new
	configuration.
	
	RESOLUTION
	==========
	
	If you have closed and reopened the workspace, you must manually copy the custom
	build step from the old configuration to the new configuration.
	
	If you have not closed and reopened the workspace, perform the following steps:
	
	1. Set the active configuration to the new configuration.
	
	2. Right-click the file that uses the custom build step, and click Settings.
	
	3. Note that the Always use custom build step check box is selected even though
	  the custom build step is gone. Clear and reselect this check box. The Custom
	  Build tab reappears with all of the correct steps.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	This problem only occurs when custom build steps are applied to files with a
	default tool (.c*, .idl, .odl and .rc files).
	
	NOTE: A project that is generated with the Visual C++ 5.0 Active Template Library
	(ATL) Component Object Model (COM) AppWizard uses a file level custom build step
	to compile the .idl file.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a Microsoft Foundation Class (MFC) AppWizard Dialog project.
	
	2. On the FileView tab, click to expand the Source Files folder.
	
	3. Right-click the Stdafx.cpp file, and click Settings.
	
	4. In the Project Settings dialog box, click the General tab, and then select
	  the Always use custom build step check box.
	
	5. On the Custom Build tab, in the Command list box, enter "Echo sampletext >
	  stdafx.txt" as the command. In the Output list box, enter "Stdafx.txt". Note
	  the configuration name, and then click OK.
	
	6. On the Build menu, click Configurations, click Add, and give the
	  configuration a name.
	
	7. In the Copy settings from drop-down combo box, select the configuration that
	  you noted in step 5, and then click Close.
	
	8. On the Build menu, click Set Active Configuration, and then select the new
	  configuration.
	
	9. Close and reopen the workspace.
	
	10. Repeat steps 2 and 3.
	
	REFERENCES
	==========
	
	For more information, see the following Microsoft Developer Network (MSDN)
	site:
	
	  http://msdn.microsoft.com/library/devprods/vs6/visualc/vcug/_asug_home_page.3a_.working_with_projects.htm
	
	Additional query words:
	
	======================================================================
	Keywords          : kbide kbVC600 kbVC600bug kbDevStudio kbDSupport kbGrpDSTools 
	Technology        : kbVCsearch kbAudDeveloper kbVC600 kbVC32bitSearch
	Version           : :6.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
