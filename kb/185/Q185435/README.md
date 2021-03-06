---
layout: page
title: "Q185435: How to Establish AFTP Connectivity to an AS/400 or Mainframe"
permalink: /kb/185/Q185435/
---

## Q185435: How to Establish AFTP Connectivity to an AS/400 or Mainframe

{% raw %}

	Article: Q185435
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0,3.0 SP1,3.0 SP2,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 18-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0 SP1, 3.0 SP2, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	How to Establish AFTP Connectivity to an AS/400 or Mainframe
	------------------------------------------------------------
	
	An AFTP (APPC File Transfer Protocol) connection can be established using
	Microsoft SNA Server versions 3.0 and above to an AS/400 or Mainframe running
	IBM's AFTP protocol found in the APPC Applications Suite. (AFTP is a necessary
	component on the Mainframe or AS/400, or there is no possibility of the
	Microsoft SNA AFTP Service communicating with the AS/400 through AFTP.) The AFTP
	Service allows users to use standard FTP clients or to use the AFTP client
	software (included as part of the Microsoft SNA client) to transfer files back
	and forth to an AS/400 or Mainframe. AFTP access to an AS/400 or Mainframe can
	be established by implementation of the steps below.
	
	Configuring the SNA AFTP Service on the SNA Server
	--------------------------------------------------
	
	1. Configure a good connection to the Mainframe or AS/400.
	
	  NOTE: To configure a good connection to an AS/400, please refer to the
	  following Microsoft Knowledge Base article for Token Ring or Ethernet
	  access:
	
	  Q112158 Configuring SNA Server to Talk to AS/400 Over 802.2
	
	  Or if the connection is through SDLC, please see the following Microsoft
	  Knowledge Base article:
	
	  Q112159 Configuring SNA Server to Talk to AS/400 Over SDLC
	
	  If you are connecting to a Mainframe through a 3174 gateway through 802.2,
	  please see the following Microsoft Knowledge Base article:
	
	  Q107567 Configuring SNA Server through a 3174 Gateway via 802.2
	
	2. At this point, the SNA Server should have a good Link Service, Connection,
	  Local APPC LU, and Remote APPC LU.
	
	3. Install the AFTP Service if it has not previously been installed. (This can
	  be verified by using the Control Panel Services tool and checking to see if
	  AFTP Server is in the list of services; or by typing "net start" at an MS-DOS
	  command prompt, which will display all services running on the local
	  computer.) If the AFTP Service has been installed, skip steps 4 and 5.
	
	4. If the AFTP Service is not installed, click the Start button, point to
	  Programs, point to SNA Server, and click Setup.
	
	5. Click Add/Remove. Select the "SNA Server Components and Services" line, and
	  click Change Option. Select the "AFTP Service" check box, and the click OK.
	  Click Continue and SNA Server will install the AFTP Service and prompt you to
	  restart your computer.
	
	Configuring FTP-AFTP Access
	---------------------------
	
	If the SNA AFTP Server is going to be used as an FTP-AFTP Gateway and allowing
	standard FTP clients to communicate to the Mainframe or AS/400, then perform the
	following steps on the SNA AFTP Server:
	
	1. Stop the FTP publishing service. With Windows NT Server 4.0, the service can
	  be stopped from the Internet Service Manager. In previous versions of Windows
	  NT Server, use the Control Panel Services tool.
	
	2. Back up the Ftpsvc2.dll file. The native Windows NT Server FTP service will
	  be replaced by an FTP service that is supplied with SNA Server. The original
	  file is generally in the <NTroot>\System32\Inetserv directory. If you
	  have customized your Windows NT Server and Microsoft Internet Information
	  Server (IIS) configuration, use the Find File tool to locate the original FTP
	  service.
	
	3. Copy the Ftpsvc2.dll file supplied with SNA Server from the
	  <snaroot>\System directory to the <NTRoot>\System32\Inetserv
	  directory.
	
	4. Restart the computer.
	
	When the system is restarted, the new Ftpsvc2.dll will be used and it has the
	ability to direct incoming FTP requests to the appropriate service, FTP or AFTP,
	depending upon the user logon. The new ftpsvc2.dll retains all the original FTP
	functionality of the previous file as well as adding in the AFTP proxy
	capability.
	
	NOTE: If you are using IIS 4.0 and encounter error 0127 when trying to start the
	FTP Publishing Service, it will be necessary to obtain hotfix 10250.
	
	Using the FTP-AFTP Proxy Gateway Service
	----------------------------------------
	
	1. Go to an MS-DOS command prompt and type the following command:
	
	  "FTP <SNA ServerName>" (without the quotation marks)
	
	2. To start an FTP-AFTP session on a host, type:
	
	  "User: <Username>@<SNADestination>
	  Password: <Password>" (without the quotation marks)
	
	  The username and password are your host user name and its associated password.
	
	The SNADestination is a valid AFTP address for an SNA host system. This can be a
	CPI-C symbolic destination name defined by the system administrator in SNA
	Server Manager, or can be the name of an APPC Remote LU Alias, or the fully
	qualified APPC Remote LU Name in the form NetName.LUName.
	
	For example:
	
	  User: yourname@appn.as400
	
	This is an example of using the Fully Qualified Remote LU Name.
	
	  -or-
	
	  User: yourname@aftpd
	
	This is an example of using a CPIC Symbolic Destination Name.
	
	NOTE: A number of commands in the AFTP client are not supported by an FTP client,
	for example recfm for controlling the host record format for uploaded files.
	These commands can be implemented in FTP through the use of the quote facility
	or the Site command, depending on your client. Choose the method supported by
	your FTP client.
	
	NOTE: If you use a login account from a trusted domain, you must disable
	anonymous logins on the FTP server. For more information, please see the
	following Microsoft Knowledge Base article:
	
	  Q123417 Err Msg: 530 User <User Name> Cannot Log In
	
	
	Configuring an AFTP Client to AFTP Server Connection
	----------------------------------------------------
	
	When you use Microsoft SNA Server for AFTP access, the SNA AFTP Server must be
	configured with either a CPIC Symbolic Destination Name or have the Local and
	Remote LU partnered when using the AFTP client. The AFTP client is a CPI-C
	application and cannot specify a Local LU alias. Security and permissions for
	the AFTP server must also be configured. When the user issues the open command,
	he or she can open to the remote LU (either its alias or the fully qualified
	remote LU name). By default, the AFTP client uses the mode #BATCH and the
	invokable TP name AFTPD. These defaults can be changed by using the modename and
	tpname commands.
	
	Configuring a CPIC Symbolic Destination Name for AFTP
	-----------------------------------------------------
	
	1. In the SNA Manager, click the Insert menu, point to APPC, and then click
	  "CPIC Symbolic Name." The Properties dialog box is displayed.
	
	2. Click the General tab, in the Name box, type AFTPD, in the Mode Name box type
	  "#BATCH", and under Conversation Security, click None.
	
	3. Click the Partner Information tab.
	
	4. Under Application TP, type AFTPD.
	
	5. Under Partner LU Name, click Alias and type the Remote LU Alias of the
	  AS/400.
	
	6. Leave all other settings at the default value, and then click OK.
	
	7. Save the configuration.
	
	Configuring AFTP Client-AFTP Server Access Security
	---------------------------------------------------
	
	Before attempting to make the connection, the AFTP client will prompt you for a
	user ID and password. This user ID is used by the AFTP server for file
	permissions (different users have different permissions), as well as for APPC
	conversation security. A user who types the user ID Anonymous is not prompted
	for a password. No APPC conversation security is specified on the ALLOCATE
	flowing from the AFTP client, and the AFTP server treats this as "no user ID."
	
	NOTE: For more information on security and AFTP, refer to the online help
	documentation or part 5 of the SNA Administration Guide.
	
	The Aftpserv.ini file is used to set user permissions in order to provide users
	access to specific directories.
	
	Configuring the Aftpserv.ini File
	---------------------------------
	
	1. Click the Start button, point to Programs, point to Accessories, and then
	  click Notepad.
	
	2. Open Snaroot\System\Aftpserv.ini.
	
	3. To control access, you may specify users, directories, and permissions for
	  AFTP clients. The Aftpserv.ini file is loaded on startup of the AFTP server
	  and any additions to the permissions will take effect at that time. Be sure
	  to type the semicolon (;) following the last line.
	
	  "provide_access
	  users(userx userx)
	  directory(directory name)
	  permissions(such as, read write);" (without the quotation marks)
	
	4. Save the file and exit Notepad.
	
	5. At the AFTP server, start the AFTP Service; either in the Control Panel
	  Services tool, or at an MS-DOS command prompt, type the following command:
	
	  "net start aftpd" (without the quotation marks)
	
	Installing and Using the AFTP Client Software
	---------------------------------------------
	
	1. When you install the SNA Client software, select the AFTP Client check box in
	  the Options List.
	
	2. Type aftp from an MS-DOS command prompt. This will initialize the Microsoft
	  AFTP client.
	
	3. From the AFTP prompt, type the following:
	
	  "open aftpd" (without the quotation marks)
	
	4. There will be a prompt for a user ID and password. These should match what is
	  used in the Aftpserv.ini file or whatever security context is set on the
	  Mainframe or AS/400 for access.
	
	5. The connection should now be established and AFTP commands can be carried
	  out. For a list of valid AFTP commands, consult the SNA online documentation.
	
	Obtaining and Configuring AFTP on the AS/400
	--------------------------------------------
	
	NOTE: The following information can be found on the online documentation for
	AFTP, obtained from IBM. Microsoft makes no claims for the accuracy of this
	documentation and cannot guarantee or imply reliability, serviceability,
	performance, or functionality of the AFTP program running on the AS/400 or
	Mainframe systems.
	
	Obtaining AFTP
	--------------
	
	AFTP was made available for OS/400 V3R1 on June 13, 1995. Because it uses system
	APIs new to V3R1, it is not supported on prior releases of OS/400.
	
	AFTP is available for free two ways:
	
	1. From the AS/400 FORUM, available via PerformanceEdge. PerformanceEdge is
	  available to all customers who are under warranty, or who have a maintenance
	  agreement with IBM. Other customers may purchase PerformanceEdge.
	
	2. AFTP is available internally to all IBMers via the AS4TOOLS disk. The
	  customer can ask his/her IBM CE or SE to get a copy from AS4TOOLS. The SE/CE
	  may distribute the copy freely to customers.
	
	AS/400 AFTP Online Documentation
	--------------------------------
	
	AS/400 APPC File Transfer Protocol
	
	APPC File Transfer Protocol (AFTP) is an advanced program-to-program
	Communications (APPC) application protocol that provides file transfer services
	to application programs and end-users. With AFTP, you can copy text and binary
	files between your computer and any computer running the AFTP server.
	
	Disclaimer
	
	This material has not been thoroughly tested under all conditions. IBM,
	therefore, cannot guarantee or imply reliability, serviceability, performance or
	function of these programs. All programs contained herein are provided to you
	"AS IS". THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR
	PURPOSE ARE EXPRESSLY DISCLAIMED.
	
	AS/400 AFTP Client and Server Functions
	
	 !          - client system call
	 ?          - shows help
	 ascii      - set data transmission to ASCII
	 alloc      - dynamically set allocation size.  On AS/400 this
	              will set the initial number of records in each
	              member of the file.
	 binary     - set data transmission to binary
	 block      - set file block size (not available on AS/400)
	 bye        - exits AFTP
	 cd         - changes directory(library)
	 close      - close a session with remote system
	 date       - sets date used on transfer
	 delete     - delete a file on server system
	 dir        - display long directory listing from remote system
	 disconnect - see close
	 ebcdic     - set data transmission to EBCDIC(only for AS/400
	              server)
	 exit       - exit from AFTP environment
	 get        - copy 1 or more file from remote system
	 help       - shows help
	 lcd        - changes local working directory(library)
	 lpwd       - shows local working directory(library)
	 ls         - display short directory listing from remote system
	 lsd        - display short directory listing from remote system,
	              subdirectories only (On AS/400 this command will
	              list libraries when invoked from QSYS)
	 lrecl      - sets file logical record length
	 mkdir      - create a new directory(library) on server system
	 modename   - change mode name used for APPC conversation.
	 open       - open a connection to destination system
	 prompt     - toggle prompt displayed on get and put
	 put        - copy 1 or more file to remote system
	 pwd        - shows remote working directory(library)
	 quit       - alias of exit command
	 receive    - alias of get command
	 recfm      - set the record format (not available on AS/400)
	 rename     - move file on server to new name or path
	 rmdir      - remove directory(library) on server system
	 send       - alias of put command
	 status     - display current transfer characteristics
	 system     - display information about server system
	 tpname     - dynamically sets the Transaction Program name
	 trace      - starts AFTP and AFTPD tracing
	 type       - view current data type
	
	Specify HELP COMMANDS in the AFTP environment for subcommand invocation
	specifics.
	
	AS/400 Server Setup
	
	After restoring the AFTP library on the AS/400 server system, the following must
	be done. The AFTP library must be placed in the User Library List. Update the
	QUSRLIBL system value. The subsystem which will handle the AFTPD invocations
	must be restarted to pick up the new library list entry. If your subsystem, APPC
	controller and APPC device configurations are not already defined, these may
	need to be configured. See the OS/400 Communications Configuration Reference for
	configuration information.
	
	AS/400 Client Setup
	
	After restoring the AFTP library on the AS/400 Client system, the following
	should be done. CPI-C side information should be defined. Use the CRTCSI command
	to do this for each destination server. Set TPNAME on this command to "AFTPD".
	If your subsystem, APPC controller and APPC device configurations are not
	already defined, these may need to be configured. See the OS/400 Communications
	Configuration Reference for configuration information. You also may want to
	place the AFTP library in the User Library List.
	
	AS/400 AFTP Invocation
	
	There are 3 possible ways to invoke AFTP for the AS/400. The first is to call
	AFTP using just system destination name.
	
	CALL AFTP system_destination
	
	This will use the CPI-C side information system destination providing it is
	configured and found. If not the system_destination will be used as a remote LU
	name.
	
	The second is to call AFTP using -f option.
	
	CALL AFTP PARM(system_destination '-f' 'file_name')
	
	This will use a file of AFTP commands which will be input to the AFTP
	application. The file_name must be specified using the following format:
	
	  'file(member)' if the member name is different that the file name,
	
	  or
	
	  'file' if the member name is the same as the file name.
	
	NOTE: The user ID and Password must be specified in the file either after the
	open command if system destination was not specified on the AFTP call, or as the
	first 2 entries in the file if the system destination was specified on the AFTP
	call.
	
	The third is to call AFTP using no options.
	
	CALL AFTP
	
	This will put you in the AFTP environment. You can then specify your mode name
	and use the OPEN command to start a conversation to a server system.
	
	AS/400 AFTP naming convention.
	
	The AS/400 uses a library structure, so the naming convention that AFTP uses is
	library/file.member. Save files do not have member names associated with the
	file.
	
	When listing libraries on the AS/400, the output list will include all the files
	and members that are part of the library. The DIR command will include the files
	and members.
	
	To list a library that is not the current directory, a slash must be provided
	after the library specification. For example, to list the XXXX library you must
	specify "ls XXXX/". If the "/" is not specified AFTP will try to list the XXXX
	file in the current directory. This rule applies for multiple PUTS, GETS and
	DELETES also.
	
	 For the PUT, GET, DELETE, and RENAME commands you must specify the
	 complete qualified name.
	    get filename.mbrname          or
	    get library/filename.mbrname
	
	 For multiple GETS, PUTS, and DELETES you can use;
	    get filename.*                or
	    get filename.xxx*
	
	Please note AS/400 AFTP will not recognize any file having a "." as part of its
	name. AS/400 AFTP assumes anything after the "." is part of the member name.
	
	Please note AS/400 AFTP will not recognize any file having a "." as part of its
	name. AS/400 AFTP assumes anything after the "." is part of the member name.
	
	AS/400 AFTP Notes and Limitations
	
	-- Server user ID and password must be capitalized.
	-- The LSD command will only work for the QSYS library. To see all
	libraries on the server AS/400, use the LSD command on the QSYS
	library.
	-- AS/400 files will always be overwritten.
	-- To display a file from a remote system specify "-" as the local
	system name on the get command( get file.mbr - ).
	-- If a file does not exist on the AS/400 previous to transfer, a
	physical file(*DATA) will be created with record length of 512
	for binary transfers, and 80 for ebcdic and ascii transfers.
	-- If you would like a physical file to be created with
	a different record length, use the lrecl command.
	-- The ALLOC command can be used to specify the maximum # of records
	in a physical file.
	-- During the RENAME of a member, the filename (file.mbr) must be
	the same name in the source and target.
	
	-- Retrieve previous command (PF9) does not work for AFTP client.
	-- Server will not delete a DB file with existing members.
	-- Server will not remove directory (library) with existing files.
	-- Server may not support anonymous userid.
	-- A file with greater than 78 record length will not completely
	display when using the "get file -" command invocation.
	-- Save files must be transferred using the binary data type.
	-- Logical files may not be transferred using the binary data type.
	-- Empty DDM file members will not be transferred.
	-- Date function will not be use when adding members to the AS/400.
	The NEW date will always be used.
	-- EBCDIC should only be used between AS/400 systems.
	-- AS/400 does not support BELL, RECFM, and BLOCK commands.
	-- AS/400 has no ANAME support.
	
	AS/400 AFTP Programs and Library Files
	
	AFTP                     - AFTP client program
	AFTPD                    - AFTP server program
	AFTPAPI                  - AFTP service program
	AFTPMSGF.AFTPMSGF        - AFTP message file. Holds all messages for AFTP
	                           client and server.
	AFTPINI.AFTPINI          - AFTP initialization file.  Holds all mapping
	                           information for AFTP client and server. See
	file for mapping definition and examples.
	QTXTSRC.AFTP             - AFTP documentation.
	
	AFTPERR.AFTPERR          - AFTP error log.  Updated when an error occurs
	for AFTP client and server.
	AFTPTRC.AFTPTRC          - AFTP trace file; created when trace is turned
	on.
	AFTPACT.AFTPACT          - AFTP audit file. Update when RMDIR, MKDIR,
	DELETE,RENAME, GET, and PUT commands are serviced by AFTP server.
	
	AFTPERR, AFTPTRC, and AFTPACT will be created by the AFTP or AFTPD programs and
	will be created under the profile that is running the program. These files are
	not updated for users that do not have write permission to the files.
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ400 kbSNAServ300SP1 kbSNAServ300SP2
	Version           : WINDOWS:3.0,3.0 SP1,3.0 SP2,4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
