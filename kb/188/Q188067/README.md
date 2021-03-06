---
layout: page
title: "Q188067: SNA Server 4.0 Service Pack 1 Readme.txt File"
permalink: /kb/188/Q188067/
---

## Q188067: SNA Server 4.0 Service Pack 1 Readme.txt File

{% raw %}

	Article: Q188067
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:4.0 SP1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 18-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, version 4.0 SP1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains a copy of the information in the Readme.txt file included
	in SNA Server 4.0 Service Pack 1.
	
	MORE INFORMATION
	================
	
	Microsoft SNA Server Version 4.0 Service Pack 1
	Electronic Release Notes
	
	Revision History
	================
	June 22, 1998 - Initial posting
	June 23, 1998 - Updated SNA 4.0 SP1 helpfile in 40SP1TXT.EXE
	June 30, 1998 - Upload MMC, MSDAC components Used By SNA Server
	               Windows 95 and Windows NT client refreshes
	               (MMC_MDAC.EXE) and enhanced installation
	               instructions below.
	
	<A9> Copyright Microsoft Corporation, 1997, 1998
	
	These materials are provided "as-is," for informational purposes only.
	
	Neither Microsoft nor its suppliers makes any warranty, express or implied
	with respect to the content of these materials or the accuracy of any
	information contained herein, including, without limitation, the implied
	warranties of merchantability or fitness for a particular purpose. Because
	some states/jurisdictions do not allow exclusions of implied warranties,
	the above limitation may not apply to you.
	
	Neither Microsoft nor its suppliers shall have any liability for any
	damages whatsoever including consequential incidental, direct, indirect,
	special, and loss profits. Because some states/jurisdictions do not allow
	exclusions of implied warranties, the above limitation may not apply to
	you. In any event, Microsoft's and its suppliers' entire liability in any
	manner arising out of these materials, whether by tort, contract, or
	otherwise shall not exceed the suggested retail price of these materials.
	
	=====================================================================
	
	Ordering the SNA Server 4.0 Service Pack 1 CD
	----------------------------------------------
	
	Microsoft SNA Server 4.0 U.S. Service Pack 1 (SP1) is available in CD media
	format by ordering from Microsoft at (800) 936-3500.
	
	SNA Server 4.0 Service Pack 1 (SP1) includes all bug fixes implemented
	since the initial SNA Server 4.0 release. In addition, the 4.0 SP1 CD
	includes the SNA Workstation 4.0 SP1, updated documentation, collateral,
	sample WEB-installable SNA Server Windows 95 client software, and SDK
	(software development kit) files. SNA Server 4.0 SP1 includes updated SNA
	Server and client software for I386 (Intel) and DEC Alpha platforms.
	
	Downloading SNA Server 4.0 Service Pack 1
	------------------------------------------
	
	Self-extracting executable files containing updated 4.0 SP1 SNA Server and
	client files can be downloaded electronically from www.microsoft.com, which
	points to:
	
	ftp://ftp.microsoft.com/bussys/winnt/sna-public/fixes/sna40/ussp1/ 
	
	The following files comprise the updated SNA Server and client files for
	SNA Server 4.0 SP1:
	
	 40SP1TXT.EXE  - 4.0 SP1 Release Notes and Help File
	 40SP1IS.EXE   - 4.0 SP1 Server Update (Intel) (NOTE 1)
	 40SP1AS.EXE   - 4.0 SP1 Server Update (Alpha) (NOTE 1)
	 40SP1ICU.EXE  - 4.0 SP1 Windows NT Client Update (Intel)
	 40SP1ACU.EXE  - 4.0 SP1 Windows NT Client Update (Alpha)
	 40SP1CLU.EXE  - 4.0 SP1 Windows 3.x Client Update
	 40SP195U.EXE  - 4.0 SP1 Windows 95 Client Update
	 40SP1IHS.EXE  - 4.0 SP1 Host Security Update (Intel)
	 40SP1AHS.EXE  - 4.0 SP1 Host Security Update (Alpha)
	 40SP1ICR.EXE  - 4.0 SP1 Windows NT Client Refresh (Intel) (NOTE 2)
	 40SP1ACR.EXE  - 4.0 SP1 Windows NT Client Refresh (Alpha) (NOTE 2)
	 40SP195R.EXE  - 4.0 SP1 Windows 95 Client Refresh (NOTE 2)
	 40SP1CLR.EXE  - 4.0 SP1 Windows 3.x Client Refresh
	 MMC_MSDAC.EXE - MMC, MSDAC Files Used By Client Refresh (NOTE 2)
	
	For information about changes implemented in 4.0 SP1, see the SNASP.HLP
	file included in 40SP1TXT.EXE, 40SP1IS.EXE or 40SP1AS.EXE.  SNASP.HLP also
	lists new features added in the service pack and articles describing the
	symptoms and causes for problems fixed in the service pack.
	
	NOTE 1: The SNA Server 4.0 SP1 includes updates to the SNA Server, Print
	Service, COM Transaction Integrator, SNA OLE/DB Interface, TN3270 Service,
	TN5250 Service, ODBC drivers, AFTP, and Shared Folders Gateway.
	
	NOTE 2: The SNA Windows 95 and Windows NT client refresh setup programs
	will attempt to invoke the MMC and/or MSDAC installation programs if the
	SNA MMC Snap-In, ODBC-DRDA Driver, COM Transaction Integrator or OLE DB
	Provider are chosen. While these separate installation programs exist on
	the SNA Server 4.0 SP1 CD, they are not included in the electronic download
	images and must be downloaded separately. For instructions, see the
	"Instructions for Decompressing the Client Refresh Files" below.
	
	Instructions for Decompressing the Client Update Files
	------------------------------------------------------
	
	All of the above files are Win32 self-extracting executables.  The SNA
	Server and client update programs automatically extract and run the Update
	program. For these Update programs to run automatically, the server or
	client machine must have the following free disk space:
	
	 Server Update (Intel) - 40SP1IS.EXE:  67 MB
	 Server Update (Alpha) - 40SP1AS.EXE:  84 MB
	 Windows NT Client Update (Intel) - 40SP1ICU.EXE: 50 MB
	 Windows NT Client Update (Alpha) - 40SP1ACU.EXE: 63 MB
	 Windows 95 Client Update         - 40SP195U.EXE: 15 MB
	
	When running Update automatically, please note the following:
	
	- before update is run, all files are automatically extracted to the
	 directory where the TMP, TEMP, or WINROOT environment variable is
	 pointing (trying in that order). So, if the SET command shows that
	 TMP=C:\TMP , and C: does not have sufficient storage to extract the
	 files, change TMP to point to a drive which has sufficient space.
	 For example:
	
	   SET TMP=D:\TEMP
	
	- to extract the files into a separate directory without running update
	 automatically, run the service pack update file using the /x option.
	 For example:
	
	   40SP1IS /x
	
	The SNA Server Windows 3.x client files (40SP1CLU.EXE, 40SP1CLR.EXE) are
	Win32 self extracting executables that cannot be run directly from a
	Windows 3.x machine. The administrator must first run the refresh file and
	choose a directory to place the extracted files. Windows 3.x clients may
	then connect across the network and run the Update program to apply the
	service pack files.
	
	Instructions for Decompressing the Client Refresh Files
	-------------------------------------------------------
	
	The SNA Server client refresh files (40SP1ICR.EXE, 40SP1ACR.EXE,
	40SP195R.EXE, 40SP1CLR.EXE) include the SNA Server client code, which
	already includes all 4.0 SP1 files. These refresh files each extract into a
	user-defined directory, though the setup program is not run automatically.
	If the SNA Windows 95 or Windows NT client setup programs are run and one
	of the following options are chosen:
	
	- SNA MMC Snap-In
	- ODBC-DRDA Driver
	- COM Transaction Integrator
	- OLE DB Provider
	
	then the MMC_MDAC.EXE file must also be downloaded and extracted, since the
	SNA client setup program will attempt to launch external installation
	programs for MMC and MSDAC. While the MMC and MSDAC files are included on
	the SNA 4.0 SP1 CD, they are not included in the SNA client refresh
	electronic download images.
	
	Follow these instructions if one or more of the above features are to be
	chosen within the SNA client setup program:
	
	1) Extract MMC_MDAC.EXE to a user-defined directory. For example:
	
	    D:\REFRESH
	
	  This will create the following subdirectories:
	
	    D:\REFRESH\MMC
	    D:\REFRESH\MSDAC
	
	2) Extract the SNA Windows 95 client refresh (40SP195R.EXE) to
	  a directory which is 2 directories below the MMC_MSDAC
	  subdirectory location. For example, if the MMC and MDAC files
	  were extracted to D:\REFRESH, then the Windows 95 client files
	  should be extracted to:
	
	    D:\REFRESH\WIN95\RETAIL
	
	  The Windows 95 setup program may then be run from the
	  D:\REFRESH\WIN95\RETAIL directory.
	
	3) Extract the SNA Windows NT client refresh (40SP1ACR.EXE or
	  40SP1ICR.EXE) to a directory which is 3 directories below the
	  MMC_MSDAC location.  For example, if the MMC and MDAC files
	  were extracted to D:\REFRESH, then the Windows NT client files
	  should be extracted to:
	
	    D:\REFRESH\WINNT\I386\RETAIL
	
	  * or *
	
	    D:\REFRESH\WINNT\ALPHA\RETAIL
	
	  The Windows NT client setup program may then be run from the
	  appropriate D:\REFRESH\WINNT\<platform>\RETAIL directory
	
	In step #2 and #3 above, the MMC and MSDAC directories must exist at the
	relative subdirectory levels mentioned above. The directory names are not
	relevant.
	
	SNA Server 4.0 SP1 includes the Microsoft Data Access Components for
	Windows 95 and Windows NT, version 1.5c. For more information about the
	Microsoft Data Access Components, see the README.TXT file within the
	<extraction-dir>\MSDAC directory.
	
	Installing the Service Pack Files
	---------------------------------
	Both the SNA Server and SNA client files have been updated in 4.0 SP1.
	Updates may be applied in any order -- to the server and/or to the clients.
	It is recommended that all systems running SNA Server 4.0 (that is, SNA
	Servers and client computers) are updated to 4.0 SP1. It may not be
	necessary to update the client computers to SP1 unless you are experiencing
	a client problem that has been fixed in SP1.
	
	WARNING: This service pack update is intended to be applied on systems
	currently running SNA Server 4.0 server or client software.  These updates
	should NOT be applied over systems running SNA Server 3.x or 2.x releases.
	
	** TO BE APPLIED TO SNA SERVER 4.0 SYSTEMS ONLY!! **
	
	Additional query words: readme release notes servpack
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ400SP1
	Version           : WINDOWS:4.0 SP1
	
	=============================================================================
	

{% endraw %}
