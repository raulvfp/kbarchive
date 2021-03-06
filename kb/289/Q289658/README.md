---
layout: page
title: "Q289658: FeedIgnoreInitial Not Always Honored on HIS 2000 Print Sessions"
permalink: /kb/289/Q289658/
---

## Q289658: FeedIgnoreInitial Not Always Honored on HIS 2000 Print Sessions

{% raw %}

	Article: Q289658
	Product(s): Microsoft SNA Server
	Version(s): 
	Operating System(s): 
	Keyword(s): kbDSupport kbhis2000
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Host Integration Server 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Print jobs printed through the host print service on Host Integration Server
	(HIS) 2000 may print an extra, blank page at the beginning of the print job. The
	blank page is printed when the print job includes a form feed (0x0C) at the
	beginning of the print job even though the FEEDIGNOREINITIAL option is set to
	Yes for the HIS 2000 print session.
	
	CAUSE
	=====
	
	The FeedIgnoreInitial option is not honored by the print service that is
	included with HIS 2000 for one of the following reasons:
	
	- If the print session is configured to use a printer definition table (PDT),
	  the print session sends a Hewlett Packard Printer Control Language (PCL)
	  sequence to the printer. This PCL sequence is treated as real print data
	  being sent to the printer, which causes the FeedIgnoreInitial option to be
	  ignored by the host print service.
	
	-or-
	
	- The HIS 2000 print service honors all EBCDIC characters under "0x40" by
	  default. This causes the FeedIgnoreInitial option to be ignored unless the No
	  Space After FF option is selected in the Print Service Properties dialog box
	  in SNA Manager.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft Host Integration Server 2000 service pack that contains
	this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	+-----------------------------------+
	| File name   | Date       | Time   | 
	+-----------------------------------+
	| Ppd3270.dll | 02/15/2001 | 9:43AM | 
	+-----------------------------------+
	| Winvprt.dll | 02/15/2001 | 9:43AM | 
	+-----------------------------------+
	
	NOTE: Because of file dependencies, the most recent fix that contains the above
	files may also contain additional files.
	
	
	
	WORKAROUND
	==========
	
	If the print session is not using a PDT and an extra blank page is being printed
	at the beginning of the job with FeedIgnoreInitial=Yes, one of the following
	configuration changes should correct the problem:
	
	- Select the No Space After FF option in the Print Service Properies dialog box
	  in SNA Manager.
	
	-or-
	
	- Select the Ignore Characters 3F and Under option in the Print Service
	  Properies dialog box in SNA Manager.
	
	The configuration of either of these options may affect the output of the print
	job, so you should examine the output to make sure the desired affect is
	achieved. The effect of these options can vary depending on the content of the
	actual print data sent by the host application.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Host Integration
	Server 2000.
	
	MORE INFORMATION
	================
	
	The following Microsoft Knowledge Base article describes another problem related
	to the FeedIgnoreInitial option with HIS 2000 (as well as SNA Server 4.0 SP3 and
	SP4):
	
	  Q286157 Blank Page May Be Printed at the Start Of Host Print Jobs
	
	
	The FEEDIGNOREINITIAL configuration option is described in more detail in the
	following Knowledge Base article:
	
	  Q185676 FEEDIGNOREINITIAL Option Not Working in Snaprint
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDSupport kbhis2000 
	Technology        : kbAudDeveloper kbHostIntegServ2000
	Version           : :
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
