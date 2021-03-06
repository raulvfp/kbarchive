---
layout: page
title: "Q162847: Troubleshooting PPTP Connectivity Issues in Windows NT 4.0"
permalink: /kb/162/Q162847/
---

## Q162847: Troubleshooting PPTP Connectivity Issues in Windows NT 4.0

{% raw %}

	Article: Q162847
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): dun kbDialUp
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to troubleshoot connectivity issues in Windows NT 4.0
	with the Point-to-Point Tunneling Protocol (PPTP). You may want to see the PPTP
	information available on the Microsoft Web site (www.microsoft.com) before you
	follow the steps in this article.
	
	MORE INFORMATION
	================
	
	Installing PPTP
	---------------
	
	Installation involves installing and configuring PPTP on both a client and a
	server computer.
	
	Client Setup:
	
	1. In Control Panel, double-click Network.
	
	2. Click the Protocols tab.
	
	3. Click Add, and then click Point-to-Point Tunneling Protocol.
	
	4. When you are prompted for how many Virtual Private Networks (VPN) to enable,
	  click 1.
	
	5. Click OK. When you are prompted to supply the Window NT 4.0 installation
	  media, do so.
	
	6. In RAS Setup, add the new Virtual Private Network (VPN) port by clicking Add
	  and double-clicking the VPN port.
	
	7. Configure the protocols to be used over the VPN port by clicking Network.
	
	8. Click OK, click Continue, and then click Close. When you are prompted to
	  restart the computer, do so.
	
	Server Setup:
	
	Follow the procedure outlined above to install PPTP on the server. Set up as many
	VPN ports as will be required to support dial-in clients.
	
	You can also configure the protocols available to each VPN port and specify
	whether the port will have access to only this computer or the entire network.
	
	Setting Up and Testing Internet Connectivity
	--------------------------------------------
	
	PPTP relies on the Remote Access Service (RAS). Therefore, RAS should be
	installed, configured, and tested prior to installing PPTP. The Remote Access
	Service can be installed using the Network tool in Control Panel. The TCP/IP
	protocol is also required by PPTP and should be installed prior to PPTP. A
	Dial-Up Networking phone book entry for your Internet service provider (ISP)
	should be created and tested. Verify that you can successfully connect to your
	ISP and obtain full Internet access.
	
	For information about setting up RAS, Dial-Up Networking, and the TCP/IP protocol
	to connect to the Internet, refer to Help in Windows NT.
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  ARTICLE-ID: Q161516
	  TITLE : Troubleshooting Modem Problems Under Windows NT 4.0
	
	  ARTICLE-ID: Q161986
	  TITLE : Troubleshooting Internet Service Provider Login Problems
	
	Testing Connectivity to the PPTP Server
	---------------------------------------
	
	Once the PPTP client and the PPTP server are connected to their ISPs, test the
	connectivity between the two.
	
	- Obtain the IP address of the PPTP server. This can be obtained with the
	  IPCONFIG tool. On the PPTP server, start a command prompt inside Windows NT.
	  Type the following command:
	
	  c:\>ipconfig /all
	
	  This displays the IP address of the NDISWANx driver.
	
	- Try communicating with the IP address of the PPTP server from the PPTP
	  client. From a command prompt on the PPTP client, type the following
	  command:
	
	  c:\>ping <IP address of the PPTP server>
	
	  You should receive four responses from the server. If you receive a "Request
	  timed out" message, the PPTP client is not able to communicate with the PPTP
	  server.
	
	Cannot Connect to PPTP Server
	-----------------------------
	
	The error message you receive will help determine what part of the PPTP
	connection you should troubleshoot.
	
	When PPTP filtering is enabled you may receive one of the following error
	messages:
	
	  Error 678: There is no answer
	
	If you receive this error message, RAS Connection Manager and Remote Access
	Server may not be started and may be set for manual startup. Start both and
	change RAS connection manager startup to automatic.
	
	  Error 650: The Remote Access Server is not responding
	
	If you receive this error message, disable PPTP filtering and then attempt to
	ping the PPTP server. To disable PPTP filtering, type the following command on
	the PPTP server:
	
	NET STOP RASPPTPF
	
	You should now be able to ping the PPTP server over the Internet. If you still
	receive one of these error messages, the problem may not be a PPTP problem.
	Until you get replies from the server, you will need to troubleshoot this issue
	as a normal connectivity problem.
	
	If pinging the PPTP server across the Internet successfully returns with replies,
	the ISP or internal corporate network may not allow Generic Routing
	Encapsulation (GRE) packets or PPTP packets to go across the firewall or
	router.
	
	GRE packets are commonly used internally as messages between routers. For
	example, an ISP may use GRE to distribute routing messages between its sites.
	For security or other reasons, this ability may be turned off to the outside
	Internet.
	
	You can resolve this problem by ensuring that Protocol 47 is open at the router
	or firewall. This protocol is required for PPTP to work correctly.
	
	In addition to GRE Protocol 47, TCP port 1723 must be enabled at all routers or
	firewalls between the PPTP client and server.
	
	An example of a GRE-blocked PPTP call in a trace is shown below. In this case,
	the ISP uses GRE internally, but does not allow the protocol to be sent to any
	outside interfaces.
	
	1- 5.364   00 E8 TCP       ....S., len:
	
	2- 5.614   E8 00 TCP       .A..S., len:
	
	3- 5.614   00 E8 TCP       .A ., len: 0, seq: 168021101-168021101,
	  ack:    460753,
	
	4- 5.630   00 E8 TCP       .AP..., len: 156, seq: 168021101-168021256,
	  ack:    460753,
	
	5- 6.130   E8 00 TCP       .AP..., len:  156, seq:    460753-460908,
	  ack:   168021257, win:
	
	6- 6.145   00 E8 TCP       .AP..., len:  168, seq: 168021257-168021424,
	  ack:    460909,
	
	7- 6.520   E8 00 TCP       .AP..., len:   32, seq:    460909-460940,
	  ack:    168021425, win:
	
	8- 6.536   00 E8 TCP       .AP..., len:   24, seq: 168021425-168021448,
	  ack:    460941,
	
	9- 6.536   20 20 LCP       Config Req Packet, Ident = 0x00, Length = 17
	
	10- 6.536  00 E8 LCP       Config Req Packet, Ident = 0x00, Length = 17
	
	11- 6.833  E8 00 ICMP      Destination Unreachable: 198.140.211.122
	  See frame 10
	
	12- 6.942  E8 00 TCP       .A...., len:    0, seq:    460941-460941,
	  ack:   168021449, win:
	
	In frame 11, there is a reference that states the destination cannot be reached
	in frame 10. Looking closely at frame 10, you can see that this packet is
	actually a GRE packet:
	
	+ FRAME: Base frame properties
	+ ETHERNET: ETYPE = 0x0800 : Protocol = IP:  DOD Internet Protocol
	+ IP: ID = 0xECB3; Proto = 0x2F; Len: 53
	+ GRE: ..KS............ Length: 21, Call ID: 0  <<<--Shows that this is a
	                                                    GRE packet.
	+ PPP: Link Control Protocol Frame (0xC021)
	+ LCP: Config Req Packet, Ident = 0x00, Length = 17
	
	The IP address in the IP portion of this frame shows the IP address of the device
	that will not allow GRE packets past its interface.
	
	NOTE: Some ISPs or corporate firewalls will not allow incoming or outgoing GRE
	packets. In this case, you will see the same "Destination Host Unreachable"
	packets in the trace, but there will not be any packets that drill down to GRE.
	
	Timeouts Using PPTP
	-------------------
	
	If you receive error 718, "the server has not responded," you may want to
	increase the number of attempts PPTP makes to transmit data.
	
	You can make this change by editing the following registry entry.
	
	WARNING: Using Registry Editor incorrectly can cause serious, system-wide
	problems that may require you to reinstall Windows NT to correct them. Microsoft
	cannot guarantee that any problems resulting from the use of Registry Editor can
	be solved. Use this tool at your own risk.
	
	1. Run Registry Editor (Regedt32.exe).
	
	2. Go to the following key in the registry:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters
	
	3. On the Edit menu, click Add Value and use the following entry (if the entry
	  already exists, just double-click it to edit the value):
	
	     Value Name:    PPTPTcpMaxDataRetransmissions
	     Data Type:     REG_DWORD
	     Value range:   0 - 0xFFFFFFFF
	     Default value: 9h
	
	  By default, this value is 9h. You may want to increase this value to 18h. It
	  is not recommended to increase this value beyond 27h.
	
	If you are using the NetBEUI protocol to connect to a PPTP server, you may need
	to install Windows NT 4.0 Service Pack 3. For additional information, please see
	the following article in the Microsoft Knowledge Base:
	
	  ARTICLE-ID: Q163129
	  TITLE : RAS Client Fails to Connect to Service Pack 2 Using NetBEUI
	
	Dialing the IP Address and Logging on to PPTP Server
	----------------------------------------------------
	
	After each computer can connect to its ISP and ping the PPTP server, test logging
	on to the PPTP server.
	
	- Set up a Dial-Up Networking phone book entry to dial the IP address of the
	  PPTP server. When you set up the phone book entry, enter the server's IP
	  address in place of a phone number. Dial using RASPPTPM.
	
	- If Dial-Up Networking dials but does not connect to the PPTP server, try
	  restarting the Remote Access Server service. To do so, follow these steps:
	
	  1. In Control Panel, double-click Services.
	
	  2. Locate the Remote Access Server service. Stop the service and then start
	     the service.
	
	Confirming Dial-In Permissions
	------------------------------
	
	PPTP requires that the connecting user account have dial-in permissions. Use the
	Remote Access Admin tool to verify that the user account has the appropriate
	dial-in permissions.
	
	If a domain is present, the user may need domain permissions to connect to
	certain resources on the network.
	
	Troubleshooting Protocol Issues
	-------------------------------
	
	PPTP can use the NetBEUI, IPX/SPX-compatible, and TCP/IP protocols. The NetBEUI
	protocol requires the least amount of configuration. Connecting to the PPTP
	server requires that the client and server have a network protocol in common.
	Once connected, the PPTP server can act as NetBIOS gateway to the rest of the
	local area network.
	
	When you are using the TCP/IP protocol, each client needs a unique IP address. IP
	addresses can be statically assigned to clients, supplied from a pool of IP
	addresses, or from a DHCP server.
	
	The Ping tool can be used in troubleshooting connectivity issues with TCP/IP. For
	additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  ARTICLE-ID: Q102908
	  TITLE : How to Troubleshoot TCP/IP Connectivity with Windows NT
	
	Browsing Issues
	---------------
	
	Avoid browsing Network Neighborhood over a slow connection. Try connecting to the
	network resource directly. To do so, follow these steps:
	
	1. Click the Start button, and then click Run.
	
	2. Type the following line, and then click OK:
	
	  \\<server>\<share>
	
	If you can connect with this method, the PPTP session is working properly and the
	issue is related to browsing.
	
	For additional information about PPTP, see the following articles in the
	Microsoft Knowledge Base:
	
	  ARTICLE-ID: Q162230
	  TITLE : Fragmentation and Performance Issues with PPTP Connections
	
	  ARTICLE-ID: Q154674
	  TITLE : PPTP Registry Entries
	
	  ARTICLE-ID: Q164052
	  TITLE : PPTP and Interoperability with Other Local Machine Services
	
	  ARTICLE-ID: Q164601
	  TITLE : How to Enable PPTP Port for Network Monitor
	
	  ARTICLE-ID: Q158387
	  TITLE : RAS Server Cannot Use DHCP to Assign Addresses w/ PPTP Filtering
	
	Additional query words: prodnt ntfaqipr
	
	======================================================================
	Keywords          : dun kbDialUp 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	
	=============================================================================
	

{% endraw %}
