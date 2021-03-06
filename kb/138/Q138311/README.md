---
layout: page
title: "Q138311: PRB: Mapi Session Control and Exchange May Cause Errors"
permalink: /kb/138/Q138311/
---

## Q138311: PRB: Mapi Session Control and Exchange May Cause Errors

{% raw %}

	Article: Q138311
	Product(s): Microsoft FoxPro
	Version(s): 3.00
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Using the MAPI Session Control that comes with Visual FoxPro 3.0 and Exchange
	that comes with Windows 95 may result in the following error when you attempt to
	log on:
	
	  OLE Idispatch exception code 0 from MSMAPI32: Login has failed
	
	The following error occurs if the LogonUI property is set to false (.F.):
	
	  The profile name is incorrect.
	
	This warning appears if anything other than the profile name is entered into the
	Username property. The Password property is ignored.
	
	CAUSE
	=====
	
	The Mapi.ocx file that ships with Visual FoxPro 3.0 is only compatible with
	Microsoft Mail, not with Exchange. The Mapi.ocx file and Microsoft Mail use an
	earlier version of MAPI, whereas Exchange uses MAPI version 1.0.
	
	WORKAROUND
	==========
	
	To work around this incompatibility, do one of the following:
	
	- Have a session of Exchange currently running; then the error messages will
	  not appear.
	
	- Place the profile name in the Username property. This avoids the warning
	  message of "Invalid Profile name" and the Logon prompt for MS Exchange.
	
	- Use OLE Messaging by using OLE Automation to MAPI.
	
	  For more information about using the OLE Messaging object, please see the
	  September 1995 Microsoft Developer Network (MSDN) Level II CD-ROM compact
	  disc, which contains the MAPI software development kit (SDK) and files
	  necessary to get OLE Messaging to work with Visual FoxPro.
	
	
	
	STATUS
	======
	
	Microsoft is researching this behavior and will post new information here in the
	Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new form, and add MAPI Session Control to the form.
	
	2. Right-click the icon for the MAPI Session Control, and choose properties.
	
	3. Clear the LogonUI check box, and select the NewSession check box.
	
	4. Run the form. At this point, an error message appears.
	
	Additional query words: VFoxWin MSMAPI Mail OCX
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : 3.00
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
