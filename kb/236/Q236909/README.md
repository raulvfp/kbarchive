---
layout: page
title: "Q236909: XWEB: OWA: Current Password Is About to Expire in 0 Days"
permalink: /kb/236/Q236909/
---

## Q236909: XWEB: OWA: Current Password Is About to Expire in 0 Days

{% raw %}

	Article: Q236909
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Outlook Web Access, version 5.5 Service Packs 1, 2, 3 
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you log on to an Exchange Server 5.5 computer using the Outlook Web Access
	(OWA) client, you may receive the following error message:
	
	  Your current password is about to expire in 0 days.
	
	CAUSE
	=====
	
	This can be caused by a corrupted or invalid IUSR_<computername> account.
	
	RESOLUTION
	==========
	
	This problem can be resolved by doing one of the following:
	
	- Change the password. You need to change the password for the
	  IUSR_<computername> account in User Manager for Domains, and then
	  re-type this new password in all the locations that reference this account
	  and password.
	
	-or-
	
	- Create a new account to be used in place of the existing account,
	  IUSR_<computername>. You need to create an account that has all of the
	  same rights and permissions, and that is part of the same groups as the
	  existing account. Then you need to make sure that all other references are
	  updated with the new account information.
	
	Check the following locations after you change a password or create a new account
	using User Manager for Domains:
	
	- Internet Information Server (IIS)
	
	  1. Start the Internet Service Manager.
	
	  2. Open the properties of the server in question, under the tree for Internet
	     Information Server.
	
	  3. Click the Edit button in the Master Properties section.
	
	  4. Click the Directory Security tab.
	
	  5. Click the Edit button in the Anonymous Access and Authentication Control
	     section.
	
	  6. Click the Edit button for Allow Anonymous Access.
	
	  7. Update the user account and password.
	
	     NOTE: You may have to clear the Enable Automatic Password Synchronization
	     check box to update the password. If you do this, make sure to re-enable
	     it before existing the dialog box.
	
	  8. Click OK four times to exit out of all dialog boxes.
	
	- Exchange Server
	
	  1. Start the Exchange Server Administrator program.
	
	  2. From the Configuration container, open the properties for DS Site
	     Configuration.
	
	  3. On the General tab, update the user account and password.
	
	  4. Click OK.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbOutlookSearch kbExchangeSearch kbExchange550 kbZNotKeyword2 kbOWASearch kbOWA550SP1 kbOWA550SP2 kbOWA550SP3
	Version           : WINDOWS:5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
