---
layout: page
title: "Q196208: INFO: DCOM98 Release Notes"
permalink: /kb/196/Q196208/
---

## Q196208: INFO: DCOM98 Release Notes

{% raw %}

	Article: Q196208
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbsetup kbtophit kbDCOM kbOSWinNT kbRegistry kbVBp600 kbVS600 kbOSWin95 kbGrpDSVB
	Last Modified: 20-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	DCOM98 is installed by the Visual Basic installation program. Visual Basic and
	some applications created in Visual Basic require DCOM98 to be installed in
	order for some components to run properly. DCOM98 extends support for DCOM
	(Distributed Component Object Model) for Microsoft Windows 98 and Microsoft
	Windows 95. DCOM98 is not required for Windows NT and Windows 2000 systems; DCOM
	is an intrinsic part of the Windows NT and Windows 2000 operating systems.
	
	This article contains the DCOM98 Release Notes.
	
	MORE INFORMATION
	================
	
	The release notes are only available after DCOM98 has been installed. After
	DCOM98 is installed, the release notes may be found at the following location:
	
	  \Windows\System\Dcom98\relnotes.txt
	
	DCOM98 is also available on Disk 1 of the Visual Basic installation CD-ROM in the
	DCOM98 folder. For more information about the two files in this folder, please
	see the Release Notes below.
	
	DCOM98 Release Notes:
	
	DCOM98 extends support for DCOM for Microsoft Windows 98 and Microsoft Windows
	95. Please note the following instructions, guidelines, and features new to this
	release of COM and OLE functionality for Windows 95 and Windows 98.
	
	Distributed COM (DCOM) extends the Component Object Model (COM) infrastructure,
	transparently and naturally adding support for reliable, secure, and efficient
	communication between COM components, such as ActiveX Controls, scripts, and
	Java applets residing on different computers in a LAN, a WAN, or on the
	Internet. With DCOM, your application can be distributed across locations that
	make the most sense to your customer and to the application.
	
	For more in-depth information, please read the DCOM Technical overview, available
	on the Microsoft COM Home Page at:
	
	  http://www.microsoft.com/com/
	
	Contents
	--------
	
	I. Installation Notes
	
	a. Downloading and Extracting DCOM98
	
	b. International Version
	
	c. Before You Install DCOM98
	
	d. Uninstalling DCOM98
	
	II. Release Notes
	
	a. What's New in DCOM98
	
	b. Bug Fixes in DCOM98
	
	c. Known Issues
	
	d. DCOM98 File List
	
	III. Developer Notes
	
	a. What's New in DCOM98
	
	b. Bug Fixes in DCOM98 Affecting Developers
	
	c. Known Issues Affecting Developers
	
	d. Differences from DCOM on Windows NT
	
	e. Redistributing DCOM98
	
	f. Support & Resources
	
	I. INSTALLATION NOTES
	---------------------
	
	A. Downloading and Extracting DCOM98:
	
	If you have downloaded this release of DCOM98 from a Web site, you should read
	the release notes completely before you extract and install DCOM98.
	
	After downloading DCOM98, you will have one or two compressed executable files on
	your hard drive:
	
	- DCOM98.EXE contains the COM system DLLs
	
	- DCM98CFG.EXE contains the DCOM Configuration utility
	
	To extract either file and begin the installation process, type the file name at
	the Command Prompt or double-click the file from Windows Explorer. After running
	DCOM98.EXE, you will be prompted to reboot your system to complete the
	installation. Your existing OLE and COM system components will be saved to allow
	you to uninstall DCOM98 if necessary.
	
	If you run these programs on any version of Windows NT, no system components will
	be overwritten. You may be asked to reboot your system in order for changes to
	take effect; this is not necessary, as nothing as been changed.
	
	B. International Version:
	
	DCOM98 can be installed over any localized version of Windows 95 or Windows 98.
	DCOM98 does not include the OLE Common Dialogs (OLEDLG.DLL), which is the only
	portion of DCOM98 requiring localization.
	
	Note that the end-user license agreement (EULA), release notes, and setup prompts
	have not been localized. When you run DCOM98.EXE on a localized version of
	Windows, standard Windows buttons will be localized, but the remaining prompts
	will not.
	
	In addition, the DCOM Configuration utility, DCM98CFG, is only provided in
	English in this Web release. The program will work correctly on localized
	versions of Windows 95 and Windows 98. However, the instructions will only
	appear in English.
	
	C. Before You Install DCOM98:
	
	The DCOM98 installation program updates your system DLLs. We recommend that you
	save all open documents and close all programs before installing DCOM98.
	
	D. Uninstalling DCOM98:
	
	NOTE: We recommend caution when uninstalling DCOM98 because other applications
	may depend on the functionality it provides. To make it less likely that DCOM98
	would be removed inadvertently, the "DCOM" entry has been removed from the
	"Add/Remove Programs" applet. However, it may still be uninstalled through the
	command line.
	
	If you are certain that you want to uninstall DCOM98, from a command line, cd to
	windows\system\dcom98\oldole. Type "uninstall" and follow the instructions
	provided. You will have to reboot to complete the uninstall. When you uninstall,
	the uninstalled files are not deleted automatically, but you may safely delete
	them if you choose to. Note that if a version of Microsoft Internet Explorer
	that depends on DCOM is installed on a Win95 machine, you will not be able to
	uninstall DCOM unless you've uninstalled Internet Explorer first.
	
	II. RELEASE NOTES
	-----------------
	
	A. What's New in DCOM98:
	
	This section lists the major new features of DCOM98 that are visible to end-users
	and administrators. Additional features for developers are described in the
	Developer Notes below.
	
	Replacing DCOM98 with Older Version Prohibited:
	
	In previous releases of DCOM95, you could replace a newer version of DCOM95 with
	an older version of DCOM95. DCOM98 now checks version numbers on installation
	and does not allow you to install an older version on top of a newer version.
	This change will avoid problems with incompatible versions of DLLs.
	
	Visual Studio 6.0 Process Monitoring Support:
	
	In support of Visual Studio 6.0, DCOM98 provides monitoring information for
	developers to help them understand the behavior, performance, and structure of
	their application. If you are using Visual Studio Analyzer, you should always
	use DCOM98.
	
	New Directory Created by Setup:
	
	Setup creates a directory called DCOM98 under your system directory. The EULA,
	etc. are stored there. Setup also creates a directory under that called OLDOLE,
	into which the old DCOM95 or OLE binaries are backed up. These files get used if
	you later uninstall.
	
	COM Internet Services:
	
	The COM Internet Services (CIS) enable clients and servers to be connected over
	the internet using COM. The COM Internet Services consist of:
	
	- a new DCOM protocol, Tunneled TCP
	
	- a new moniker type, OBJREF moniker
	
	- a new CISCNFG utility
	
	For Windows 95 or Windows 98 CIS client support, install DCOM98; install
	DCOM98CFG as described above. Then use the CISCNFG tool (which is installed when
	you install the DCOM configuration utility) to change the registry key that
	defines which protocol to use for remote processes. From a command line, type:
	
	  ciscnfg <protocol>
	
	where <protocol> is:
	
	  rpc to use RPC
	
	  http to use HTTP
	
	  tcp_http to try TCP first, and, if the server times out, try HTTP.
	
	Typing "ciscnfg" with no argument provides usage information.
	
	No SDK updates are required to use the Tunneled TCP protocol. There are a few
	updates for OBJREF monikers.
	
	CreateObjrefMoniker:
	
	Creates an OBJREF moniker based on a pointer to an object:
	
	  WINOLEAPI CreateObjrefMoniker(
	  LPUNKNOWN pUnk, //Pointer to the object
	  LPMONIKER *ppMk //Address of pointer to OBJREF moniker
	  );
	
	Parameters:
	
	pUnk: Pointer to the IUnknown interface on the object that the moniker is to
	represent.
	
	ppMk: Address of a pointer to the IMoniker interface on the OBJREF moniker
	created.
	
	Return Values:
	
	This function supports the standard return values E_OUTOFMEMORY and E_UNEXPECTED,
	as well as the following:
	
	S_OK: The OBJREF moniker was successfully created.
	
	Remarks:
	
	Clients use OBJREF monikers to obtain a marshaled pointer to a running object in
	the server's address space.
	
	The server typically calls CreateObjrefMoniker to create an OBJREF moniker and
	then calls IMoniker::GetDisplayName, and finally releases the moniker. The
	display name for an OBJREF moniker is of the form:
	
	     OBJREF:nnnnnnnn
	
	where nnnnnnnn is an arbitrarily long base-64 encoding that encapsulates the
	computer location, process endpoint, and interface pointer ID (IPID) of the
	running object.
	
	The display name can then be transferred to the client as text. For example, the
	display name can reside on an HTML page that the client downloads.
	
	The client can pass the display name to MkParseDisplayName, which creates an
	OBJREF moniker based on the display name. A call to the moniker's
	IMoniker::BindToObject method then obtains a marshaled pointer to the running
	instance on the server.
	
	For example, a server-side COM component contained in an Active Server Page can
	create an OBJREF moniker, obtain its display name, and write the display name to
	the HTML output that is sent to the client browser. A script that runs on the
	client side can use the display name to get access to the running object itself.
	A client-side Visual Basic script, for instance, could store the display name in
	a variable called strMyName and include this line:
	
	     objMyInstance = GetObject(strMyName)
	
	The script engine internally makes the calls to MkParseDisplayName and
	IMoniker::BindToObject, and the script can then use objMyInstance to refer
	directly to the running object.
	
	If the running object uses static IPIDs and the server process always runs on the
	same computer at a well-known endpoint, the display name of the OBJREF moniker
	will always be the same. In that case, the server can store the display name
	instead of calculating it each time it receives a request for the object.
	
	IMoniker - OBJREF Moniker Implementation:
	
	OBJREF monikers represent a reference to an object instance that is running on an
	out-of-process server, either locally or remotely. The moniker identifies the
	object instance and the computer the object is running on.
	
	An OBJREF moniker is similar in many ways to a pointer moniker, except that the
	running object is out-of-process. A client can call IMoniker::BindToObject on an
	OBJREF moniker and use the pointer it obtains to access the running object,
	regardless of its location.
	
	An important distinction from a pointer moniker is that the display name of an
	OBJREF moniker can be embedded in an HTML page, and the running object
	represented by the moniker can be bound by a client script, applet, or ActiveX
	control.
	
	When to Use:
	
	The primary use for an OBJREF moniker is to obtain access to a running object
	instance over the Internet. An active server page or some other means of
	generating dynamic HTML content places the display name of an OBJREF moniker in
	a parameter to an applet or an ActiveX control. The code of the applet or
	control calls CreateObjrefMoniker to create an OBJREF moniker based on the
	display name, and it then calls IMoniker::BindToObject on the resulting OBJREF
	moniker to get access to the running object instance. The active server page
	then marshals a pointer to the running object back to the page's client.
	
	Remarks:
	
	IMoniker::BindToObject - For OBJREF monikers, the pmkToLeft parameter must be
	NULL. Because the OBJREF moniker represents a running object, no activation
	takes place. If the represented object is no longer running, BindToObject fails
	with E_UNEXPECTED.
	
	IMoniker::BindToStorage - This method obtains a marshaled pointer to the
	requested interface on the storage that contains the running object. Because the
	OBJREF moniker represents a running object, no activation takes place. If the
	represented object is no longer running, BindToStorage fails with E_UNEXPECTED.
	
	IMoniker::Reduce - This method returns MK_S_REDUCED_TO_SELF and passes back the
	same moniker.
	
	IMoniker::ComposeWith - If pmkRight is an anti-moniker, the returned moniker is
	NULL. If pmkRight is a composite whose left-most component is an anti-moniker,
	the returned moniker is the composite with the left-most anti- moniker removed.
	If pmkRight is neither an anti-moniker nor a composite moniker whose left-most
	component is an anti-moniker, then the method checks the fOnlyIfNotGeneric
	parameter. If it is FALSE, the method combines the two monikers into a generic
	composite; if it is TRUE, the method sets *ppmkComposite to NULL and returns
	MK_E_NEEDGENERIC.
	
	IMoniker::Enum - This method returns S_OK and sets ppenumMoniker to NULL.
	
	IMoniker::IsEqual - This method returns S_OK if *pmkOther is an OBJREF moniker
	and the paths for both monikers are identical (using a case- insensitive
	comparison). Otherwise, the method returns S_FALSE.
	
	IMoniker::Hash - This method calculates a hash value for the moniker.
	
	IMoniker::IsRunning - Because OBJREF monikers represent a running object
	instance, this method returns TRUE unless the object is known to be no longer
	running because a recent call failed. The method ignores pmkToLeft.
	
	IMoniker::GetTimeOfLastChange - This method returns E_NOTIMPL.
	
	IMoniker::Inverse - This method returns an anti-moniker (such as the results of
	calling CreateAntiMoniker_com_CreateAntiMoniker).
	
	IMoniker::CommonPrefixWith - If the two monikers are equal, this method returns
	MK_S_US and sets *ppmkPrefix to NULL. If the other moniker is not an OBJREF
	moniker, this method passes both monikers to the MonikerCommonPrefixWith
	function. This function correctly handles the case where the other moniker is a
	generic composite. If there is no common prefix, this method returns MK_E_.
	
	IMoniker::RelativePathTo - This method returns E_NOTIMPL.
	
	IMoniker::GetDisplayName - This method obtains the display name for the OBJREF
	moniker. The display name is a 64-bit encoding that encapsulates the machine
	location, process endpoint, and interface pointer ID (IPID) of the running
	object. For future compatibility, the display name is restricted to characters
	that can be specified as part of a URL.
	
	IMoniker::ParseDisplayName - If pmkToLeft is not NULL, this method returns
	MK_E_SYNTAX.
	
	IMoniker::IsSystemMoniker - This method returns S_OK and passes back
	MKSYS_OBJREFMONIKER.
	
	B. Bug Fixes in DCOM98:
	
	This section describes bugs fixed in DCOM98 that affected applications running on
	Windows 95 with DCOM95 1.1 installed. Additional bug fixes are described in the
	Developer Notes section below.
	
	Race Condition When Unloading Multiple Modules:
	
	When multiple modules were unloaded simultaneously, a race condition would occur
	in DCOM95 v1.1. Depending upon the order in which the modules were unloaded, an
	access violation could result. This has been corrected in DCOM98.
	
	Desktop Unresponsive During RPC Protocol Negotiations:
	
	While DCOM95 negotiated RPC protocols, it didn't dispatch messages. In certain
	cases, if the user launched another application during the time that RPC
	protocols were being negotiated, the machine would appear to be unresponsive.
	After 30 seconds, processing of messages would resume. In DCOM98 this has been
	changed, and applications can be launched while RPC protocols are being
	negotiated.
	
	Desktop Unresponsive When New Application Launched:
	
	RPC creates a hidden window that doesn't dispatch messages. When a user launches
	a new application from the desktop, Windows sends a message to all other window
	handles, notifying them of this event, and expecting a reply. The hidden RPC
	window would not reply, and Windows would hang (for 30 seconds in Windows 98;
	forever in Windows 95). DCOM98 fixes this problem, and the RPC window no longer
	makes the desktop unresponsive when new applications are launched.
	
	Multiple IP Addresses Heap Corruption:
	
	In certain situations, if you were running DCOM95 v1.1 on a machine with more
	than one IP address, the IP address buffer would be overrun and the heap would
	be corrupted. This has been fixed in DCOM98.
	
	Only First IP Address Used:
	
	If you were running DCOM95 v1.1 on a machine that had two network adapter cards
	(such as two IP addresses, each assigned to a different address card), DCOM95
	v1.1 would use just one network adapter. In DCOM98, if the first one tried
	doesn't work, the second one will be used.
	
	RPC Now Tries Multiple IP Addresses:
	
	When doing a remote procedure call to a machine with multiple IP addresses,
	subsequent IP addresses will now be tried if connecting to the first one fails.
	
	C. Known Issues:
	
	This section describes known problems in DCOM98 that affect applications running
	on Windows 95 with DCOM98 installed. Additional issues are described in the
	Developer Notes section below.
	
	Corel WordPerfect Suite 7: Installation Causes Invalid Page Fault:
	
	If you install Corel WordPerfect Suite 7 on a Windows 95 system running DCOM98,
	you may get an invalid page fault in PfOd70.pfc during installation. If this
	error appears, just close the error message dialog box. Setup should continue
	successfully.
	
	Microsoft Access95: Database Replication Does Not Work:
	
	If you try to replicate an Access database using Microsoft Access 95 on machines
	with DCOM98 installed, you may get the following error message: "Microsoft
	Access cannot complete this operation because it can't find or initialize the
	dynamic-link library Msjtrclr." This is a problem in Access95. You may work
	around this issue by writing a program that uses the Access object model rather
	than the replica tool, or by using the briefcase for replication. Microsoft
	Access 97 is not affected by this issue.
	
	WordPerfect:
	
	If you have a WordPerfect document containing an embedded Corel spreadsheet, and
	the spreadsheet contains another embedded object (such as a bitmap), you may get
	a warning dialog saying you've lost the network connection when you close the
	innermost object. There may be four or five such warnings. All these warnings
	are benign. Just close them and continue.
	
	D. DCOM98 File List:
	
	This table lists the version numbers of files distributed with DCOM98:
	
	oleaut32.dll     2.30.4261
	secur32.dll      4.10.1999
	compobj.dll      2.3.1
	ole2.dll         2.3.1
	ole32.dll        4.71.2512
	olecnv32.dll     4.71.2512
	olethk32.dll     4.71.2512
	rpcltc1.dll      4.71.2512
	rpcltc5.dll      4.71.2512
	rpcltccm.dll     4.71.2512
	rpclts5.dll      4.71.2512
	rpcltscm.dll     4.71.2512
	rpcns4.dll       4.71.2512
	rpcrt4.dll       4.71.2512
	rpcss.exe        4.71.2512
	storage.dll      2.3.1
	stdole2.tlb      2.30.4261
	stdole32.tlb     2.1
	imagehlp.dll     4.00
	dllhost.exe      4.71.2512
	comcat.dll       5.0
	iprop.dll        4.00
	rpcmqcl.dll      4.71.2512
	rpcmqsvr.dll     4.71.2512
	olepro32.dll     5.0.4261
	asycfilt.dll     2.30.4261
	
	This table lists the version numbers of files distributed with DCM98CFG:
	
	mfc40.dll        4.1.6139
	msvcrt40.dll     4.21.0000
	dcomcnfg.exe     5.00.1601.0
	oledlg.dll       1.0
	ciscnfg.exe      4.71.2424
	
	III. DEVELOPER NOTES
	
	A. What's New in DCOM98:
	
	Support for VB6.0 Data Types - Visual Basic 6.0 allows Visual Basic variants to
	contain user-defined data structures. DCOM98 supports remoting of these
	variants.
	
	B. Bug Fixes in DCOM98 Affecting Developers:
	
	This section lists additional bug fixes in DCOM98 which are not likely to affect
	end-users, but which developers or testers might encounter.
	
	File Monikers Support Additional Path Syntax:
	
	File monikers can now be created out of arguments of the form
	<startdir><relativepath> as in "C:\bug\bug\..\..\food.jpg." In
	DCOM95 v1.1, only relative paths (such as "..\..\food.jpg") or absolute paths
	(such as "C:\test.jpg") were permitted.
	
	GP Fault When Oleaut32.dll Unloaded:
	
	In DCOM95 v1.1, a General Protection fault would occur when Oleaut32.dll was
	unloaded before calling CoUnInitialize. This would most often occur when a
	Visual Basic application created a control statically linked to Oleaut32.dll,
	and then freed the control prior to calling CoUnInitialize. This no longer
	causes a general protection fault in DCOM98.
	
	Visual Basic Type Marshalling and Unmarshalling:
	
	The marshalling and unmarshalling of certain Visual Basic data types has been
	fixed. Array parameters with a size greater than 64K are now allowed. Structures
	defined using aliases to the type are now marshalled and unmarshalled
	correctly.
	
	Atoms Being Deleted Too Many Times in OleUninitialize():
	
	This bug appeared in applications that called OleInitialize and OleUninitialize
	multiple times. During initialization, OLE adds many atoms for DDE RPC. If the
	atoms have already been added by another thread, they are not added again.
	However, during uninitialization, atoms were always deleted and the handles were
	not nullified. Therefore, the next time OleInitialize ran, the old handles would
	still exist, even though the atoms were long gone, and OLE wouldn't add them
	again. This led to all OLE atoms being invalid after multiple calls to
	OleInitialize and OleUninitialize. This problem has been fixed in DCOM98.
	
	ADO Servers Not Shutting Down Properly:
	
	Active Data Objects (ADOs) use point monikers to start a server process. DCOM95
	v1.1 contained a bug involving point moniker reference counting, whereby point
	monikers were created with an initial reference count of 1 (rather than 0).
	Therefore, the reference count of the point moniker would never get to zero, and
	the point moniker would never be freed. This led to ADO servers never shutting
	down, even after the last pointer to it had been released. This has been fixed
	in DCOM98.
	
	CoCreateInstance Works With Own DNS Name:
	
	In DCOM95 v1.1, calling CoCreateInstance with the fully-qualified name of the
	local machine didn't work. This has been fixed in DCOM98, and CoCreateInstance
	now correctly creates an instance on the local machine.
	
	C. Known Issues Affecting Developers:
	
	MTA Clients That Use BSTR Conversion Routines May Block DDE Messages:
	
	OLE Automation BSTR conversion routines (such as BstrFromR4) create hidden
	windows to facilitate the type conversion. These windows do not service the
	Windows message queue. If such a window is created from within a Multi- Threaded
	Apartment client, DDE messages may be blocked. The client thread has no
	obligation to service the message queue under the MTA programming model. If it
	does not, this top-level window causes global broadcast messages to block.
	
	There are two ways to work around this situation: either call the BSTR conversion
	routines from within an STA client, or make the client's MTA thread behave like
	a Single-Threaded Apartment thread. (That is, it must service the message
	queue.) If it is blocking on a win32 handle, it must call the
	MsgWaitForMultipleObjects() API to simultaneously dispatch windows messages.
	
	D. Differences from DCOM on Windows NT:
	
	Security Capabilities of DCOM98:
	
	The core functionality and application programming interfaces (APIs) new to
	Distributed COM are identical in both Windows 95/98 (DCOM98) and Windows NT
	4.0/5.0. However, certain capabilities related to security are different because
	of the different security infrastructures of the operating systems. Using the
	default security settings of the system is recommended; it is also necessary to
	enable "user-level" security on file-system shares (see below).
	
	The following services, which can be used to override default security, are
	available:
	
	- CoInitializeSecurity
	
	- CoQueryAuthenticationService
	
	- CoQueryProxyBlanket
	
	- CoSetProxyBlanket
	
	- CoQueryClientBlanket
	
	- IClientSecurity Interface
	
	- IServerSecurity Interface
	
	However, certain capabilities that are part of DCOM for Windows NT will not be
	available on Windows 95 or Windows 95 because of differences in the security
	infrastructure on Windows 95 and Windows 98.
	
	In particular, the lack of Win32 security APIs, such as the ability to create
	Access Control Lists (ACLs), and the AccessCheck function, as well as the lack
	of a security context associated with thread- and process- tokens, should be
	taken into account. Windows 95 and Windows 98 do not natively support these APIs
	or constructs. Because of this, DCOM98 will not support impersonation
	(specifically, the CoImpersonateClient and CoRevertToSelf helper functions over
	the IServerSecurity interface), which is based on thread- and process-token
	security in Windows NT 4.0. Impersonation is commonly used to automatically
	control access to restrictable system resources such as the file system, other
	processes, and the network. These resources are not restrictable on Windows 95
	or Windows 98.
	
	DCOM98 does, however, offer programmers various helper objects to provide
	access-control-list and access-check functionality, which can be used to
	explicitly control access by remote clients to both system and user-defined
	resources or data. These helper objects are provided by the system object
	CLSID_DCOMAccessControl, which implements the IAccessControl interface.
	
	IAccessControl should be used to manage security permissions programmatically
	wherever portability between Windows 95 or Windows 98 and Windows NT is a
	concern. The CLSID_DCOMAccessControl object is available in all releases of
	DCOM95 and DCOM98 and in Windows NT 4.0 SP2 or later. Please see the Platform
	SDK documentation for more information about IAccessControl.
	
	Launch and Access Security:
	
	"Launch security," or controlling who can launch server-class code, is not
	provided in DCOM98 because launching servers is not supported. Servers/Classes
	must already be running in order for remote clients to connect and make use of
	their services.
	
	DCOM98 does support the ability to connect to already running classes/servers.
	"Access security" is supported via the \APPID\{.}\AccessPermissions registry key
	and adjusted via the DCOMCNFG tool or during installation or setup of the server
	code. Unauthenticated users will be able to use servers if you configure the
	class to support unauthenticated connections (through static configuration tools
	or dynamically via the CoInitializeSecurity function) and you can also build
	arbitrary access-control lists to define which users and groups can access
	specific services.
	
	Authentication Levels:
	
	DCOM98 clients can make DCOM calls using any authentication level. DCOM98 servers
	(or clients receiving callbacks) can only accept DCOM calls using
	RPC_C_AUTHN_LEVEL_NONE or RPC_C_AUTHN_LEVEL_CONNECT authentication levels.
	
	Transports:
	
	DCOM98 only supports TCP connectivity. If you do not have the TCP/IP protocol
	installed, DCOM95 will not be able to support cross-machine COM.
	
	Registry Settings:
	
	The following registry keys found under HKEY_LOCAL_MACHINE\Software\Microsoft\OLE
	are established by DCOM98and enables Distributed COM on this computer:
	
	  EnableDCOM (default value = "Y")
	
	When set to "N," the computer is prevented from connecting to or activating
	objects on remote computers, and remote computers are unable to connect to
	objects on the local computer. Setting this value to "Y" enables either
	connectivity as a client to remote objects (when EnableRemoteConnect='N', see
	below), or full client/server connectivity (when EnableRemoteConnect='Y', see
	below).
	
	  EnableRemoteConnect (default value = "N")
	
	Enables COM servers to act as DCOM servers. When this value is set to "Y,"
	references to interfaces on local objects can be passed to remote clients, and
	remote clients are allowed to connect to running objects. When this value is set
	to "N," this machine is allowed to connect to remote objects but cannot act as a
	server; that is, the computer is prevented from connecting to running objects.
	
	In addition, the following registry key is found under HKEY_CLASSES_ROOT\CLSID:
	
	  {bdc67890-4fc0-11d0-a805-00aa006d2ea4}\InstalledVersion
	
	and contains the version number of DCOM98, in the format "a,b,c,d." This value
	can be used by Internet Component Download to determine whether DCOM98 is
	installed. This value is added to the registry during setup, and should not be
	modified.
	
	Using Windows 95 as a DCOM Server Host:
	
	Windows 95 can be a DCOM server host with the following caveats:
	
	1. There is no launch capability, which means the DCOM server process must
	  already be running for a client to connect to it.
	
	2. If secure connections are needed, then the server (and in the case of
	  callbacks, the client) must have user-level access control with the name of a
	  security provider set.
	
	3. The registry value "EnableRemoteConnect" must be set to "Y."
	
	DCOM98 has been tested most extensively using the Windows NT Domain security
	provider. You may encounter problems using other security providers.
	
	To establish user-level access control, you must have FILESEC.VXD installed. This
	is generally installed on Windows 95 machines by installing File and Print
	Sharing.
	
	To enable user-level access control, launch the Network control panel applet,
	choose the "Access Control" tab, select the box marked "User-level access
	control," and enter the name of your security domain. This may affect the way
	you currently share directories on the network from your computer; see the
	Online documentation for details. If you do not have an "Access Control" tab in
	your network configuration control panel, you need to install a network client
	service. See the "Network clients, setting up" Help topic in the Online Help for
	information on installing a network client.
	
	E. Redistributing DCOM98:
	
	If you depend on DCOM98 functionality, you have two options: redistribute the
	updated system files (DCOM98) with your application, or point users at our
	DCOM98 Web release. Pointing users at the Web release is recommended if your
	application will be downloaded from the Web, because DCOM98 is fairly large and
	many users may already have it.
	
	For further information about redistributing DCOM98, please review the
	redistribution guidelines in DCOMDIST.TXT and the redistribution agreement in
	DCOMLIC.TXT.
	
	F. Support and Resources:
	
	For more information about the Distributed Component Object Model (DCOM), please
	see the following URL:
	
	  http://www.microsoft.com/com/dcom/dcom98/dcom1_3.asp
	
	For more information on your support options for this product, please refer to
	Support Options by Product online at:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsetup kbtophit kbDCOM kbOSWinNT kbRegistry kbVBp600 kbVS600 kbOSWin95 kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600
	Version           : :6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
