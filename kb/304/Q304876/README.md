---
layout: page
title: "Q304876: NNTP Service in Windows NT 4.0 Contains Memory Leak"
permalink: /kb/304/Q304876/
---

## Q304876: NNTP Service in Windows NT 4.0 Contains Memory Leak

{% raw %}

	Article: Q304876
	Product(s): Microsoft Windows NT
	Version(s): 4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4,4.0 SP5,4.0 SP6a
	Operating System(s): 
	Keyword(s): kbenv kbtool kbWinNT400PreSP7Fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4, 4.0 SP5, 4.0 SP6a 
	- Microsoft Windows NT Server, Enterprise Edition versions 4.0, 4.0 SP4, 4.0 SP5, 4.0 SP6a 
	-------------------------------------------------------------------------------
	
	For additional information about a similar problem that can occur in Microsoft Windows 2000, click the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q303984 NNTP Service in Windows 2000 Contains Memory Leak
	
	SYMPTOMS
	========
	
	The Network News Transfer Protocol (NNTP) service in Windows NT 4.0 contains a
	memory leak in a routine that processes news postings. Each time such a posting
	is processed that contains a particular construction, the memory leak causes a
	small amount of memory to no longer be available for use. If an attacker sent a
	large number of posts, the server memory could be depleted to the point at which
	normal service would be disrupted. An affected server could be restored to
	normal service by rebooting.
	
	Mitigating Factors:
	
	- Windows NT 4.0 does not contain a native NNTP service. NNTP is only available
	  on the system if the Windows NT 4.0 Option Pack has been installed.
	
	- The default configuration of NNTP is not affected by this vulnerability, as
	  no newsgroups are configured by default.
	
	- This vulnerability would not enable an attacker to usurp any administrative
	  control or compromise data on the computer.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems that are determined to be at risk of attack. Please evaluate your
	computer's physical accessibility, network and Internet connectivity, and other
	factors to determine the degree of risk to your computer. Please see the
	associated Microsoft Security Bulletin
	(http://www.microsoft.com/technet/treeview/default.asp?url=/technet/security/bulletin/MS01-043.asp)
	to help make this determination. This fix may receive additional testing at a
	later time, to further ensure product quality. If your computer is sufficiently
	at risk, Microsoft recommends that you apply this fix now.
	
	To resolve this problem immediately, download the fix as instructed below or
	contact Microsoft Product Support Services to obtain the fix. For a complete
	list of Microsoft Product Support Services phone numbers and information on
	support costs, please go to the following address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The following file is available for download from the Microsoft Download Center:
	
	  DownloadDownload Q304876engi386.exe now
	  (http://www.microsoft.com/Downloads/Release.asp?ReleaseID=31955)
	
	Release Date: August 14, 2001
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. After it is posted, the file is housed on
	secure servers that prevent any unauthorized changes to the file.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date         Time   Version      Size     File name
	  -----------------------------------------------------
	  27-Jul-2001  12:39  5.5.1877.77  761,616  Nntpsvc.dll
	
	
	
	STATUS
	======
	
	Microsoft has confirmed that this problem could result in some degree of
	security vulnerability in Microsoft Windows NT 4.0.
	
	MORE INFORMATION
	================
	
	For more information about this vulnerability, please see the following
	Microsoft Web site:
	
	  http://www.microsoft.com/technet/treeview/default.asp?url=/technet/security/bulletin/MS01-043.asp
	
	Additional query words: security_patch
	
	======================================================================
	Keywords          : kbenv kbtool kbWinNT400PreSP7Fix 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400sp5 kbWinNTSEnt400sp4 kbWinNTSEnt400 kbWinNTS400sp6 kbWinNTS400sp5 kbWinNTS400sp4 kbWinNTS400sp3 kbWinNTS400sp2 kbWinNTS400sp1 kbWinNTS400search kbWinNTS400 kbWinNTSEnt400SP6a
	Version           : :4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4,4.0 SP5,4.0 SP6a
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
