---
layout: page
title: "Q174790: IIS Hangs When Querying a FoxPro Database w/ ASP or IDC/HTX"
permalink: /kb/174/Q174790/
---

## Q174790: IIS Hangs When Querying a FoxPro Database w/ ASP or IDC/HTX

{% raw %}

	Article: Q174790
	Product(s): Internet Information Server
	Version(s): 2.00 3.00
	Operating System(s): 
	Keyword(s): kberrmsg
	Last Modified: 02-MAY-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server versions 2.0, 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you query a FoxPro database using Active Server Pages (ASP) or the Internet
	Database Connector (IDC/HTX), the Internet Information Server (IIS) appears to
	hang, and the web browser appears not to respond to the web site. The web
	browsers' status bar would read as follows:
	
	  Web site found. Waiting for reply...
	
	However, the web server gives no response.
	
	CAUSE
	=====
	
	This behavior by the IIS server is caused by incorrect permissions being granted
	to the IUSR_machine-name account. The Visual FoxPro ODBC database driver will
	try to create *.tmp in the \Winnt\System32 directory. Because the
	IUSR_machine-name account does not have the Write and Delete permissions to that
	\Winnt\System32, the process will fail causing the IIS server to no longer
	respond.
	
	RESOLUTION
	==========
	
	There are two possible solutions to this problem.
	
	Option 1
	--------
	
	Grant your anonymous user (IUSR_machine-name by default) or the authenticated
	Windows NT user account the following permissions to the these directories:
	
	When you apply these permissions, only apply them to all existing files, unless
	otherwise noted. Please be aware that where the IUSR account is noted you would
	need to add all user accounts that will be authenticated on the IIS server.
	
	1. Grant IUSR Read permission to the Root directory of the drive that ASP is
	  installed on.
	
	2. Grant IUSR Write permission to the Windows NT directory.
	
	3. Grant IUSR Read permission to the System32 directory.
	
	4. Grant IUSR Read permission to the Inetserv directory.
	
	5. Grant IUSR Read permission to the InetPub (or content directory) By default,
	  the next two directories are located in Program Files, Common Files, System
	  and are only needed for ASP/ADO queries.
	
	6. Grant IUSR Read permission to the OLE DB directory.
	
	7. Grant IUSR Read permission to the ADO directory.
	
	8. Grant IUSR Change permissions to the Database file and directory.
	
	Option 2
	--------
	
	FoxPro uses the System's TEMP and TMP environment variables to specify the
	location of temporary files created during FoxPro operations. By default these
	environment variables are defined for users and are not system wide settings. To
	set these environment variables for the System, do the following:
	
	1. Right-click My Computer.
	
	2. Choose Properties and select the Environment tab.
	
	3. Click an entry in the System Variables List box (the one on top).
	
	4. In the Variable and Value Edit control, type the following:
	
	  Variable = TEMP
	  Value = C:\Temp
	
	5. Click the Set button. You will now see TEMP has been added to the list of
	  system variables. Repeat the process for the TMP variable.
	
	6. Log off and restart the computer.
	
	7. Grant IUSR Read permission to the System32 directory.
	
	  NOTE: Because the FoxPro driver no longer needs to create TEMP files in the
	  System32 directory, the IUSR account should only have Read permissions to
	  that directory.)
	
	======================================================================
	Keywords          : kberrmsg 
	Technology        : kbiisSearch kbiis300 kbiis200
	Version           : 2.00 3.00
	Hardware          : ALPHA x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
