---
layout: page
title: "Q129726: TCP/IP Requires Ethernet_II Frame Type for ODI Driver"
permalink: /kb/129/Q129726/
---

## Q129726: TCP/IP Requires Ethernet_II Frame Type for ODI Driver

{% raw %}

	Article: Q129726
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	You can use the Ping tool to ping your own computer, but you cannot access the
	network using the TCP/IP protocol. You may receive the following error message
	when you try to access the network:
	
	  Request timed out
	
	CAUSE
	=====
	
	This problem can occur when you are using a Novell NetWare ODI driver and the
	Ethernet_II frame type is not listed in the proper NET.CFG file.
	
	RESOLUTION
	==========
	
	To correct this problem, add Ethernet_II to the NET.CFG file. Make sure you edit
	the correct NET.CFG file--NET.CFG is usually read from the same directory as
	LSL.COM. Note that you should not make Ethernet_II the first frame type listed
	in the file.
	
	To add Ethernet_II to the NET.CFG file, follow these steps:
	
	1. Use any text editor (such as WordPad) to open the NET.CFG file.
	
	2. Add "ETHERNET_II" (without quotation marks) so that it is the last frame type
	  listed in the "LINK DRIVER <MLID>" section. For example, after you add
	  "ETHERNET_II" the section might look like:
	
	     LINK DRIVER <MLID>
	        FRAME ETHERNET_802.2
	        FRAME ETHERNET_802.3
	        FRAME ETHERNET_SNAP
	        FRAME ETHERNET_II
	
	3. Save and close the NET.CFG file.
	
	4. Restart your computer.
	
	======================================================================
	Keywords          :  
	Technology        : kbWin95search kbZNotKeyword3
	
	=============================================================================
	

{% endraw %}
