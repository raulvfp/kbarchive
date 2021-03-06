---
layout: page
title: "Q109499: SYSINI.WRI from Windows for Workgroups 3.11 (Part 2 of 3)"
permalink: /kb/109/Q109499/
---

## Q109499: SYSINI.WRI from Windows for Workgroups 3.11 (Part 2 of 3)

{% raw %}

	Article: Q109499
	Product(s): Microsoft Windows 3.x Retail Product
	Version(s): WINDOWS:3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 24-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows for Workgroups version 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following information was taken from the Microsoft Windows for Workgroups
	version 3.11 SYSINI.WRI, and begins with the continuation of [network] section
	settings.
	
	MORE INFORMATION
	================
	
	MaintainServerList=<yes-no-auto>
	
	Default:     Auto
	Purpose:     Specifies whether the browser on your computer acts
	as the browse master or a back-up browse master. If the value for
	this setting is Auto, the browser on your computer will act as
	either, as needed. If the value for this setting is No, the browser
	will never act as a browse master or a back-up browse master. If the
	value for this setting is Yes, the browser will always act as both.
	If you are setting up a computer as a dedicated server for a small
	workgroup of three to four computers, you may want to set this value
	to Yes on the server and to No on the other computers. Otherwise, you
	should never need to change this value.
	____________________________________________________________
	MultiNet=<name>
	
	Default:     None
	Purpose:     Specifies the other networks you have added support for.
	____________________________________________________________
	NoProtocolErrMsg=<0-or-1>
	
	Default:     0
	Purpose:     If your computer is a portable which usually connects
	to your network by using its docking station, then whenever the
	computer is not connected to its docking station, you will receive
	error messages when you start Windows for Workgroups 3.11. Since this
	situation does not really indicate a networking problem, you can use
	this setting to prevent one of the error messages from appearing.
	
	    If value for this setting is 0, the error message controlled
	by this setting will appear. If the value for this setting is 1, the
	error message will never appear.
	____________________________________________________________
	PreferredRedir=<full-or-basic>
	
	Default:     Basic
	Purpose:     Specifies whether the net start command loads the
	full real-mode network drivers, which provide full network
	functionality including browsing, or the basic real-mode network
	drivers, which provide only limited functionality.
	____________________________________________________________
	PrintBufTime=<seconds>
	
	Default:     45
	Purpose:     Specifies the number of seconds of idle printing time
	that Windows for Workgroups should wait before indicating that the
	end of a print job has been reached when printing from an
	MS-DOS?based application. When printing to a network printer from an
	MS-DOS?based application, your documents do not start printing until
	the application finishes processing the print job. If you are using
	an MS-DOS?based application that processes print jobs quickly and you
	want your documents to print sooner, decrease this value. If you are
	using an MS-DOS?based application that takes longer to process print
	jobs or if your documents are not printing continuously, increase
	this value. The time during which an MS-DOS?based application is
	suspended is not counted.
	____________________________________________________________
	PrintSharing=<boolean>
	
	Default:     1
	Purpose:     Turns print sharing on or off. If this setting is
	enabled, you can use the Print Manager to share printers over the
	network. If this setting is disabled, you cannot share printers.
	
	Note:  If your Network Administrator has disabled print sharing, this
	switch will have no effect.
	____________________________________________________________
	Priority=<number>
	
	Default:     80
	Purpose:     Specifies the priority given to running your
	applications and sharing your resources. The lower the number, the
	faster your applications run. The higher the number, the faster your
	resources are shared. The value for this setting must be between 40
	and 9000.
	____________________________________________________________
	Reconnect=<boolean>
	
	Default:     Yes
	Purpose:     Determines whether the Reconnect At Startup check box
	in the Connect Network Drive or Connect Network Printer dialog box is
	selected the next time the dialog box is displayed. If this setting
	is enabled, the check box is selected. If this setting is disabled,
	the check box is not selected. When you select or clear the check
	box, the value for this setting changes in the SYSTEM.INI file to
	reflect its current state.
	____________________________________________________________
	Reshare=<boolean>
	
	Default:     Yes
	Purpose:     Determines whether the Reshare At Startup check box
	in the Share Directory or Share Printer dialog box is selected the
	next time the dialog box is displayed. If this setting is enabled,
	the check box is selected. If this setting is disabled, the check box
	is not selected. When you select or clear the check box, the value
	for this setting changes in the SYSTEM.INI file to reflect its
	current state.
	____________________________________________________________
	Username=<name>
	
	Default:     Your computer name until you log on for the first
	time. Then the default value becomes the logon name you specify in
	the Welcome To Windows For Workgroups dialog box.
	Purpose:     Specifies the default logon name used to log on to
	Windows for Workgroups. The value for this setting changes to the
	logon name you specify when you log on to Windows for Workgroups.
	____________________________________________________________
	WinShare=<path>
	
	Default:     None
	Purpose:     Specifies a remoteWindows directory. This is useful
	if you are running a shared copy of Windows from a network server.
	The network path specified here is the path that contains the shared
	copy of Windows. The WinShare parameter prevents the specified
	network connection from disconnecting while Windows is running.
	____________________________________________________________
	WorkGroup=<name>
	
	Default:     The workgroup you specified during Setup.
	Purpose:     Specifies the workgroup your computer belongs to. If
	this setting is missing from your SYSTEM.INI file, the Windows for
	Workgroups redirector will not load and you will not have full
	networking capabilities.
	____________________________________________________________
	
	[Network Drivers] Section Settings
	
	The [Network Drivers] section contains information used for running
	the real-mode network drivers to connect to the network.
	
	The [Network Drivers] section can contain the following settings:
	____________________________________________________________
	DevDir=<path>
	
	Default:     c:\windows
	Purpose:     Specifies the location of the PROTOCOL.INI file and
	the real-mode drivers necessary to connect to the network. The
	necessary drivers are determined by the netcard= and transport=
	entries in this section.
	____________________________________________________________
	LoadRMDrivers=<yes-or-no>
	
	Default:     None
	Purpose:     Specifies whether the net start command loads real
	mode drivers.
	____________________________________________________________
	NetCard=<list-of-filenames>
	
	Default:     None (Setup sets this value to match your configuration.)
	Purpose:     Specifies the real-mode driver(s) for your network
	adapter. This is loaded by the net initialize command, by the net
	start command (if LoadRMDrivers=yes), or by the net start workstation
	command.
	____________________________________________________________
	Transport=<list-of-filenames>
	
	Default:     None (Setup sets this value to match your configuration.)
	Purpose:     Specifies the network-protocol real-mode-driver
	file(s) that Windows for Workgroups uses. This is loaded by the net
	start command (if LoadRMDrivers=yes), or by the net start workstation
	command.
	____________________________________________________________
	
	[Password List] Section Settings
	
	The [Password List] section contains settings that specify the
	location of the password-list files for each user who logs on to your
	computer. The password-list file contains a list of the passwords you
	use to connect to password-protected resources.
	
	The [Password List] section can contain one or more occurrences of
	the following setting:
	____________________________________________________________
	<username>=<drive><directory><password-list-filename>
	
	Purpose:     Username specifies the logon name of the user; drive
	specifies the drive the password-list file is located on; directory
	specifies the name of the directory in which the password-list file
	is located; and password-list-filename specifies the name of the
	password-list file.
	____________________________________________________________
	
	[NonWindowsApp] Section Settings
	
	The [NonWindowsApp] section contains settings that affect the
	performance of MS-DOS?based applications.
	
	The [NonWindowsApp] section can contain the following settings:
	____________________________________________________________
	CommandEnvSize=<bytes>
	
	Default:     0 for MS-DOS versions earlier than 3.2. Otherwise,
	the default is the value for the /e: option in the shell= command
	line in the CONFIG.SYS file.
	Purpose:     Specifies the size of the COMMAND.COM environment.
	Note that running batch files with the extension .BAT starts
	COMMAND.COM, so this setting also applies to batch files. The value
	for this setting must be either 0 or between 160 and 32768. A value
	of 0 disables this setting. If the value is too small or too large,
	it will be rounded up to 160 or down to 32768. If the value is less
	than the current size of the actual environment, this setting will be
	disabled, as if it were set to 0. If you have specified the
	environment size in a PIF file for COMMAND.COM, the PIF-file setting
	overrides this setting.
	____________________________________________________________
	DisablePositionSave=<0-or-1>
	
	Default:     0
	Purpose:     When this setting is disabled, the position and fonts
	used by an MS-DOS?based application are saved in the DOSAPP.INI file
	when you quit the application. If this setting is enabled, the
	position and fonts used by an MS-DOS?based application whose settings
	have not been previously saved in the DOSAPP.INI file will not be
	saved. If enabled, the setting can be overridden for each
	MS-DOS?based application by selecting the Save Settings On Exit check
	box in the Font Selection dialog box in the application.
	____________________________________________________________
	FontChangeEnable=<0-or-1>
	
	Default:     1 on systems that use Windows version 3.1 or Windows
	for Workgroups grabbers. 0 on systems that use Windows version 3.0
	grabbers.
	Purpose:     Enables you to change fonts when you are running an
	MS-DOS?based application in a window on a system that uses version
	3.0 grabbers (usually used in 3.0 display drivers). Windows version
	3.1 video grabbers (used in 3.1 display drivers) include built-in
	support for changing fonts when you are running an MS-DOS?based
	application in a window. If you are using a 3.0 grabber that has not
	been updated to include the ability to change fonts and you want to
	use this feature, enable this setting. However, with this setting
	enabled, your screen may lose characters and the cursor may change
	size and position slightly.
	____________________________________________________________
	LocalTSRs=<list-of-TSR-applications>
	
	Default:     DOSEDIT, CED
	Purpose:     Specifies which terminate-and-stay-resident (TSR)
	programs work properly if they are copied to each instance of a
	virtual machine. When you start Windows for Workgroups, it detects
	any TSR programs that are currently running. If the TSR is on the
	LocalTSRs list, Windows for Workgroups copies the TSR to each virtual
	machine you run. Many TSRs will not run properly if they are added to
	this list. Make sure your TSR is fully compatible with Windows for
	Workgroups and can be copied to a virtual machine before you add it
	to the list.
	____________________________________________________________
	MouseInDosBox=<0-or-1>
	
	Default:     1 if an MS-DOS mouse driver is loaded that has the
	extension .COM or .SYS and supports the use of a mouse with an
	MS-DOS?based application. Otherwise, the default is 0.
	Purpose:     Specifies whether the mouse is supported when running
	an MS-DOS?based application in a window. Mouse support for an
	MS-DOS?based application running in a window is automatically
	available if you are using a Windows version 3.1 grabber. If you are
	using a Windows version 3.0 grabber and you want mouse support,
	enable this setting. If you do not want mouse support, disable this
	setting.
	____________________________________________________________
	NetAsynchSwitching=<0-or-1>
	
	Default:     0, unless an application is running that supports the
	use of the Task Switcher API by the NetBIOS.
	Purpose:     Specifies whether you can switch away from an
	application after it has made an asynchronous network BIOS call. If
	this setting is disabled, you cannot switch away. Switching away from
	some applications that make these calls might cause your system to
	fail. After Windows for Workgroups detects an asynchronous NetBIOS
	call, you cannot switch away from the application, even if no more of
	these calls are made. Enable this setting only if you are sure that
	the applications you use will not receive network messages while they
	are inactive.
	____________________________________________________________
	ScreenLines=<number>
	
	Default:     25
	Purpose:     Specifies the number of lines that will be displayed
	on the screen when you run an MS-DOS?based application. An
	application that specifies a different screen mode can override this
	setting.
	____________________________________________________________
	SwapDisk=<drive:directory>
	
	Default:     The directory that the TEMP environment variable
	points to; if there is no TEMP variable, the default is the root
	directory of your first hard drive (usually drive C). If you do not
	have a hard disk, the default is the root directory of your first
	floppy disk drive (usually drive A).
	Purpose:     Provides the name of the disk drive and directory to
	which Windows for Workgroups swaps MS-DOS?based applications.
	____________________________________________________________
	
	[standard] Section Settings
	
	Windows for Workgroups 3.11 no longer runs in standard mode. It
	therefore does not use any settings in the [standard] section.
	
	____________________________________________________________
	
	Additional query words: wfw wfwg 3.11
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWFWSearch kbWFW311
	Version           : WINDOWS:3.11
	
	=============================================================================
	

{% endraw %}
