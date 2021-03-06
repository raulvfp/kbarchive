---
layout: page
title: "Q311861: IIS: Error Message When You Try to Open the ISM Locally"
permalink: /kb/311/Q311861/
---

## Q311861: IIS: Error Message When You Try to Open the ISM Locally

{% raw %}

	Article: Q311861
	Product(s): Internet Information Server
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When you try to open the Internet Service Manager snap-in locally on a computer
	that is running Microsoft Windows 2000 server, you may receive the following
	error message:
	
	  Unable to enumerate web sites because the following error occurred: An
	  internal error occurred.
	
	No error appears in the event log when this occurs, and you can connect from
	another computer to this server without error.
	
	CAUSE
	=====
	
	This issue can occur if a registry key exists that modifies the default behavior
	of the cryptography application programming interfaces (APIs). In this case, the
	cryptography APIs cannot create the public and private encryption keysets that
	are necessary to query the metabase.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To resolve this problem, follow these steps:
	
	1. Click Start, click Run, and then type "regedit" (without the quotation marks)
	  to start Registry Editor.
	
	2. Browse to the following registry key, and then click Providers:
	
	  HKEY_USERS\Default\Software\Microsoft\Cryptography\Providers\Type 001
	
	3. On the Registry menu, click Export Registry File, and then type the location
	  in which you want to save this file. You can use this file if you must
	  restore this registry key later.
	
	4. Press DELETE, and then click Yes to confirm that you want to delete the
	  registry key.
	
	5. Restart the server.
	
	
	MORE INFORMATION
	================
	
	
	To obtain a more descriptive error message for this problem, log on to the
	computer with an account that is currently experiencing the problem.
	
	The following is a test to determine if the account can successfully query the
	metabase:
	
	1. Open a command prompt and change to the C:\Inetpub\Adminscripts folder.
	
	2. At the command line, type "cscript adsutil.vbs enum w3svc" (without the
	  quotation marks). If this command is successful, it enumerates the settings
	  for the w3svc key in the metabase. If the command is not successful, you
	  receive the -2146893792 (0x80090020) error code.
	
	REFERENCES
	==========
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q313494 Microsoft Cryptography API May Not Work if the Default CSP Has Been
	  Set Incorrectly
	
	Additional query words: iis 5
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis500
	Version           : :5.0
	Issue type        : kbprb
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
