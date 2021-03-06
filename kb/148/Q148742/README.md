---
layout: page
title: "Q148742: Troubleshooting the ISDN Accelerator Pack"
permalink: /kb/148/Q148742/
---

## Q148742: Troubleshooting the ISDN Accelerator Pack

{% raw %}

	Article: Q148742
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95
	Operating System(s): 
	Keyword(s): win95
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article lists tips for troubleshooting connection problems using the ISDN
	Accelerator Pack for Internet Explorer 2.0.
	
	MORE INFORMATION
	================
	
	The ISDN Accelerator Pack for Internet Explorer 2.0 supports the following ISDN
	adapters:
	
	  Manufacturer         Model
	  --------------------------------------------------
	  Digi                 Datafire U
	                       Datafire S/T
	                       Datafire4
	                       PCIMAC
	                       PCIMAC4
	  Eicon Technologies   G. Diehl PCMCIA adapter
	                       G. Diehl ISA internal adapter
	  Elmic Systems        Surf-2-Surf
	  U.S. Robotics        Sportster 128k ISDN internal
	                       adapter
	
	If your ISDN adapter is not listed and is an internal adapter, contact the
	adapter's manufacturer for assistance.
	
	For additional information about external adapters, please see the following
	article in the Microsoft Knowledge Base:
	
	  Q140123 Using ISDN Terminal Adapters in Windows 95
	
	If you are having difficulty connecting to another computer using the ISDN
	Accelerator Pack for Internet Explorer 2.0, perform the following steps to
	troubleshoot the problem:
	
	1. Verify that an ISDN adapter is installed correctly in Windows 95 and that it
	  is a supported device by following these steps:
	
	  a. In Control Panel, double-click Network. On the Configuration tab, verify
	     that your ISDN adapter is in the list of installed network components. If
	     your ISDN adapter is not in the list of installed components, install it
	     using the manufacturer's instructions.
	
	  b. Click your ISDN adapter, and then click Properties.
	
	  c. On the Resources tab, verify the settings for the adapter (such as IRQ and
	     I/O address settings). These settings should match the physical settings
	     on the adapter.
	
	     If you are unable to determine the physical settings on your ISDN adapter,
	     contact the manufacturer for assistance.
	
	2. Install Dial-Up Networking if you have not done so already. For information
	  about installing Dial-Up Networking, please consult your Windows 95
	  documentation, or search for "Dial-Up Networking" in Windows 95 Help.
	
	3. Verify that the correct network protocols have been installed and configured
	  appropriately. To do so, follow these steps:
	
	  a. In Control Panel, double-click Network.
	
	  b. Verify that the following components have been installed:
	
	      - Client for Microsoft Networks
	
	      - Dial-Up Adapter
	
	      - Your ISDN device
	
	      - NDISwan
	
	      - TCP/IP, IPX, or NetBEUI protocol
	
	4. Verify that the ISDN adapter driver is not set to transfer data above the
	  rate of 64K per second. For example, Digi ISDN adapters may be configured to
	  transfer data at rates faster than 64K per second by using Digiboard bonding.
	  This is not a supported configuration. If your driver is configured to
	  transfer data at rates above 64K, disable this feature for testing.
	
	  For information about disabling Digiboard bonding on Digi ISDN adapters,
	  please see the following article in the Microsoft Knowledge Base:
	
	  Q148179 Digi ISDN Adapter Stops Working During 128K Connection
	
	  If you do not have a Digi ISDN adapter and your ISDN adapter driver is
	  configured to transfer data at rates faster than 64K per second, contact the
	  manufacturer of your IDSN adapter for instructions on disabling this feature.
	
	5. If you need to dial a number for an outside line before making a connection,
	  add the number by clicking Dialing Properties in the connectoid and filling
	  in the "To access an outside line, dial" box with the appropriate number.
	
	  NOTE: If you have a modem installed, you should add a comma (,) after the
	  number you use to access an outside line. If you do not include a comma, your
	  modem may not dial correctly. ISDN devices ignore the comma.
	
	6. Verify that the correct service profile identifier (SPID) has been entered in
	  the ISDN Accelerator Pack settings. To do so, compare the SPID entered in the
	  ISDN Accelerator Pack settings with the SPID provided by your telephone
	  company.
	
	  NOTE: If your telephone company has provided a voice SPID and a data SPID, the
	  data SPID should be entered in the Channel 1 field. Some telephone companies
	  may require that you enter only one data SPID. If the SPIDs are voice and
	  data (which is more common), they can be entered in any order.
	
	  If you do not have your full SPID in writing from your telephone company,
	  contact them to verify it.
	
	  For additional information about checking or changing SPIDs, please see the
	  following article in the Microsoft Knowledge Base:
	
	  Q149718 How to Change SPIDs in Windows 95
	
	7. After making a connection, verify that the connection to the ISDN line is
	  correct for the interface type of your ISDN adapter (these types are S/T or
	  U). To verify which type of interface your ISDN adapter uses, refer to the
	  adapter's documentation or contact the manufacturer.
	
	  ISDN adapters using an S/T interface must be connected to an NT1 device and
	  then to the ISDN line. If you are connecting to an NT1 device, verify that
	  the NT1 device has power and that no error lights are active.
	
	  If the Terminal Error light is on, the card cannot synchronize with the
	  telephone digital service. This is usually caused by bad SPIDs, an improperly
	  seated ISDN adapter card, or the computer that the adapter is installed in
	  not being powered on. To troubleshoot the Terminal Error light, verify the
	  SPIDs and then remove and reinsert the ISDN adapter.
	
	  If the Line Error light is on, the line is not functioning correctly. Contact
	  your telephone company to verify that your ISDN line is working.
	
	  ISDN adapters using a U interface cannot use an NT1 device and must be
	  connected directly to the ISDN interface supplied by the telephone company.
	
	8. If the connection is being dropped or is not established at all, try changing
	  the protocols or checking the type of server to which you are connecting. For
	  more information about the connection, create a Ppplog.txt file by viewing
	  the properties of the Dial-Up Adapter in Network properties and clicking Yes
	  in the Record A Log File box on the Advanced tab.
	
	  Also, attempt to connect to more than one ISDN server to rule out a server
	  that is not functioning as the cause.
	
	9. Remove the ISDN adapter and all ISDN files from the computer and then
	  reinstall them according to the manufacturer's instructions.
	
	======================================================================
	Keywords          : win95 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : 95
	
	=============================================================================
	

{% endraw %}
