---
layout: page
title: "Q126557: Error Message: A Device Is Not Functioning"
permalink: /kb/126/Q126557/
---

## Q126557: Error Message: A Device Is Not Functioning

{% raw %}

	Article: Q126557
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 
	Operating System(s): 
	Keyword(s): 3rdpartynet msnets win95 kb3rdPartyNetClient
	Last Modified: 28-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are using the File And Print Sharing network service for Novell NetWare
	and you try to remove a large directory structure (with over 1000 entries) in
	Windows Explorer or File Manager, you receive the following error message:
	
	  A device is not functioning
	
	CAUSE
	=====
	
	The Windows 95 Ncpserver Service maintains an internal search cache that allows
	only 1000 entries. When you try to work with a directory structure with over
	1000 entries, the cache is exceeded and entries beyond 1000 are not seen. This
	causes the 1000th-oldest search handle to be invalid, generating the error
	message stated above.
	
	WORKAROUND
	==========
	
	Use Windows Explorer or File Manager to select the directory tree you want to
	delete and try to delete it. When the error message occurs, select the tree and
	try to delete it again. Repeat this process until the directory is deleted.
	
	STATUS
	======
	
	This behavior is by design.
	
	======================================================================
	Keywords          : 3rdpartynet msnets win95 kb3rdPartyNetClient 
	Technology        : kbWin95search kbZNotKeyword3
	
	=============================================================================
	

{% endraw %}
