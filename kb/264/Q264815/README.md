---
layout: page
title: "Q264815: Visual InterDev 6.0 Enterprise Developer's Workshop Comments and"
permalink: /kb/264/Q264815/
---

## Q264815: Visual InterDev 6.0 Enterprise Developer's Workshop Comments and

{% raw %}

	Article: Q264815
	Product(s): Microsoft Press
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdocfix kbdocerr
	Last Modified: 09-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- MSPRESS Microsoft Visual InterDev 6.0 Enterprise Developer's Workshop ISBN 0-7356-0568-8 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains comments, corrections, and information about known errors
	relating to the Microsoft Press book Microsoft Visual InterDev 6.0 Enterprise
	Developer's Workshop, ISBN 0-7356-0568-8.
	
	The following topics are covered:
	
	- CD-ROM: Error When Installing NT Option Pack With SP4
	
	- CD-ROM: Incorrect Permissions On Component Folder
	
	- Page 217: Missing Trailing Quote In Code Sample
	
	MORE INFORMATION
	================
	
	CD-ROM: Error When Installing NT Option Pack With SP4
	-----------------------------------------------------
	
	When you install Windows NT Option Pack on a computer that already has Windows NT
	4.0 Service Pack 4 installed, the following message appears:
	
	  Setup detected that Windows NT 4.0 SP4 or greater is installed on your
	  machine. We haven?t tested this product on SP4. Do you wish to proceed?
	
	Click OK to continue the installation. Once the setup program has completed and
	the computer has restarted, you should reinstall Windows NT 4.0 Service Pack 4.
	
	For further information on this error, please refer to the the follwing KB
	article:
	
	  Q195015 Option Pack Installation Conflicts with Service Pack 4
	
	For information on the conflict between Windows NT Service Pack 4 and Client
	Certificates, please refer to the following KB article:
	
	  Q194788 Windows NT Service Pack 4 and Client Certificates
	
	
	CD-ROM: Incorrect Permissions On Component Folder
	-------------------------------------------------
	
	After installing the Rent-A-Prize application and browsing the RentAPrizeHome.asp
	page, you may receive the following error message:
	
	  bsReservation error'800a005b' Object variable or With block variable not set
	  /Rent-A-Prize/Customer/RentAPrizehome.asp, line 69
	
	This is caused by incorrect permissions on the Components folder of the
	Rent-A-Prize application.
	
	The following steps will resolve this issue:
	In the Internet Service Manager MMC snap-in, locate the Components folder in the
	Rent-A-Prize application's folder, right-click the folder and select Properties.
	In the Properties dialog box, change the permissions on the folder from Script
	to Execute.
	
	The original instructions for registering and packaging components can be found
	in Appendix B, on page 550.
	
	
	Page 217: Missing Trailing Quote In Code Sample
	-----------------------------------------------
	
	In the code sample at the top of page 217, the first sText line is missing the
	ending quotation mark (").
	
	This should read:
	
	  sText = "<H1>When writing text to the browser,</H1>"
	
	
	Microsoft Press is committed to providing informative and accurate books. All
	comments and corrections listed above are ready for inclusion in future
	printings of this book. If you have a later printing of this book, it may
	already contain most or all of the above corrections.
	
	Additional query words: 0-7356-0568-8 DevBook InterDev
	
	======================================================================
	Keywords          : kbdocfix kbdocerr 
	Technology        : kbMSPressSearch
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
