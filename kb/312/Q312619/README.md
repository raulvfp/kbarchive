---
layout: page
title: "Q312619: MSN Explorer Not Recognizing New Hotmail Folder Or Folders"
permalink: /kb/312/Q312619/
---

## Q312619: MSN Explorer Not Recognizing New Hotmail Folder Or Folders

{% raw %}

	Article: Q312619
	Product(s): The Microsoft Network
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Network Version 7.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You can add new folders through your Hotmail account on http://www.hotmail.com.
	You can access the new folder(s) from http://www.hotmail.com Web site and from
	Microsoft Outlook 2002, but you do not see any new folders you create on
	http://www.hotmail.com when you sign in to your MSN Explorer account and click
	the E-mail button.
	
	CAUSE
	=====
	
	The MSN Explorer software does not recognize new folders created through the
	Hotmail Web site. Existing MSN Explorer folders are not updated to synchronize
	with new folders created at the Hotmail Web site.
	
	RESOLUTION
	==========
	
	To resolve this issue
	
	1. Quit MSN Explorer and sign out of any Hotmail account you may have open.
	
	2. Click Start, point to Search, and then click Find Files or Folders.
	
	3. Click Tools, and then click Folder Options.
	
	4. Click View tab, and then select Show Hidden Files and Folders.
	
	5. In the Search for files or folder named box, type hotmail.ini; in the
	  Containing Text box, type your e-mail address.
	
	6. Right-click the Hotmail.ini entry in the search window, and then click Open
	  Containing Folder.
	
	7. Right-click folders.dbx, and then click Delete.
	
	8. Restart MSN Explorer, and then click the E-mail button. Your folders will
	  synchronize. The problem should be fixed.
	
	Additional query words: kbimu; MSN Explorer
	
	======================================================================
	Keywords          :  
	Technology        : kbMSNSearch kbMSN700
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
