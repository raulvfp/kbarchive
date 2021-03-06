---
layout: page
title: "Q262979: Cannot Renew Verisign Certificates in IIS 5.0"
permalink: /kb/262/Q262979/
---

## Q262979: Cannot Renew Verisign Certificates in IIS 5.0

{% raw %}

	Article: Q262979
	Product(s): Internet Information Server
	Version(s): 2000,5.0
	Operating System(s): 
	Keyword(s): kbWin2000SP2Fix
	Last Modified: 17-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	- Microsoft Windows 2000 Professional 
	- Microsoft Windows 2000 Server 
	- Microsoft Windows 2000 Advanced Server 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you attempt to renew an SSL certificate from Verisign, the renewal with
	Verisign fails.
	
	CAUSE
	=====
	
	Windows 2000 Professional, Windows 2000 Server, and Windows 2000 Advanced Server
	generate PKCS7-formated renewals, which Verisign does not accept.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows 2000. For
	additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q260910 How to Obtain the Latest Windows 2000 Service Pack
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date       Time      Version       Size    File name    Platform
	  ----------------------------------------------------------------
	  10-02-2000 1:35:53PM 5.0.2195.2399 200,976 Certwiz.ocx  x86
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in Internet Information Services
	5.0. This problem was first corrected in Windows 2000 Service Pack 2.
	
	MORE INFORMATION
	================
	
	This fix changes the behavior in Windows 2000, so that it generates
	PKCS10-formatted renewal requests.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbWin2000SP2Fix 
	Technology        : kbwin2000AdvServ kbwin2000AdvServSearch kbwin2000Serv kbwin2000ServSearch kbwin2000Search kbwin2000ProSearch kbwin2000Pro kbiisSearch kbiis500 kbWinAdvServSearch
	Version           : :2000,5.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
