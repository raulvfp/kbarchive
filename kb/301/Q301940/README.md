---
layout: page
title: "Q301940: HOW TO: Migrate Objects from One Domain to Another in Windows NT"
permalink: /kb/301/Q301940/
---

## Q301940: HOW TO: Migrate Objects from One Domain to Another in Windows NT

{% raw %}

	Article: Q301940
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbAudDeveloper kbHOWTOmaster
	Last Modified: 10-APR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	
	IN THIS TASK
	------------
	
	- SUMMARY
	
	   - To Migrate Users and Groups to Another Domain
	- To Create Shares Remotely
	- To Copy File and Share Permissions
	- To Migrate Registry Keys, Services, and Other Objects
	
	   - An Example
	
	SUMMARY
	=======
	
	This article describes how to copy domain objects from one domain to another by
	using the tools that are provided in the Microsoft Windows NT 4.0 Resource Kit
	Supplement.
	
	NOTE: It is recommended that you test the steps that are described in this
	article in a test area before you use them in a production environment.
	
	The Resource Kit tools are:
	
	- The Addusers.exe tool can be used to import and export user and group
	  accounts from one domain to another.
	
	- The Rmtshare.exe tool can be used to remotely create or delete shares.
	
	- The Scopy.exe tool can be used to copy NTFS file and folder permissions from
	  one share to another. (This tool, however, does not copy share permissions.)
	
	- The Permcopy.exe tool can be used to copy share permissions from one share to
	  another.
	
	- The Subinacl.exe tool can be used to obtain security information on files,
	  registry keys, and services, and to transfer this information from user to
	  user, from group to group, and from domain to domain.
	
	For additional information about the Resource Kit tools, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q158388 Useful Resource Kit Utilities for Domain Administrators
	
	To Migrate Users and Groups to Another Domain
	---------------------------------------------
	
	1. You can use the Addusers.exe tool to migrate users and groups to another
	  domain. To transfer existing user and group accounts to a file, use the
	  "addusers \\computer_name|domain_name/d filename" command, where
	  "computer_name|domain_name" is the name of the primary domain controller
	  (PDC) computer that contains the user and group information for the specified
	  domain, and "filename" is the new file that contains the user and group
	  account information.
	
	  When the user and group information is transferred to a file, the information
	  is saved in a comma-delimited format.
	
	  This transfer of user account information does not save user account passwords
	  or any security information to the file. When you use this transfer file to
	  migrate users to another domain, all of the newly created user accounts have
	  a blank password and, by default, all of the newly created users are required
	  to change their passwords at their next logon sessions.
	
	2. To add the users and groups to the new domain, use the "addusers
	  \\computer_name|domain_name/c filename" command, where
	  "computer_name|domain_name" is the name of the PDC computer and the domain
	  where the user accounts are created, and "filename" is the name of the
	  comma-delimited transfer file that contains the user and group information.
	
	  NOTE: The Addusers.exe tool and additional documentation is included in the
	  Windows NT 4.0 Resource Kit, Supplement 3. To view the other parameters that
	  you can use with this tool, at a command prompt, type: "addusers /?", and
	  then press ENTER.
	
	For additional information, click the article numbers below to view the articles
	in the Microsoft Knowledge Base:
	
	  Q199878 Addusers Automates Creation of a Large Number of Users
	
	  Q245009 Batch Add Accounts Without Forcing a Password Change at Next Logon
	
	To Create Shares Remotely
	-------------------------
	
	To create or to delete shares on a remote server by using the Rmtshare.exe tool,
	use a command with the following syntax:
	
	  rmtshare \\server[\sharename[=path [/printer]]] [/grant [user[:perms ]]]
	  [/remove user][/users:number] [/unlimited] [/remark:"text"] /delete
	
	An explanation of the syntax of the preceding command is:
	
	- The "\\server\sharename" syntax refers to both the server and the share that
	  you can create, inspect, modify, or delete.
	
	- The "/grant user:perms" syntax adds the name of a valid user or group on the
	  server that have permissions, or changes the permissions of the user in an
	  access control list. The valid permissions are: r=read, c=change (write),
	  f=full, and n=none. You can type "read", but only the first character is
	  used.
	
	- The "/remove user" syntax removes the specific entry for a user. Then, that
	  user inherits permissions (in contrast to "/grant user:none" that denies any
	  access to the user).
	
	- The "/users:number" syntax is the number of users that have privileges to the
	  server and share.
	
	- The "/delete" syntax deletes the share that are specified by the
	  "\\server\sharename" syntax.
	
	NOTE: If a sharename or path contains spaces, enclose either the sharename or
	path in quotes, for example: \\server\"with space"="c:\with space".
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q155449 Batch Process to Create and Grant Access to Home Directories
	
	To Copy File and Share Permissions
	----------------------------------
	
	Two tools are required to copy NTFS and share permissions: The Scopy.exe tool is
	used to copy NTFS file and folder permissions, and the Permcopy.exe tool is used
	to copy share permissions.
	
	To copy files and folders, and retain their NTFS file and folder permissions, use
	the Scopy.exe tool and the "scopy source destination/o /a /s" command, where
	"source" is the path to the source folder and "destination" is the path to the
	destination folder. The /o option copies the owner security information, /a
	copies the auditing information, and /s includes all of the files in the
	subfolders.
	
	The Scopy.exe tool cannot copy files to or from file systems that do not use
	security features, such as, file allocation table (FAT) and high-performance
	file system (HPFS). The Scopy.exe tool copies only NTFS file system security
	information. This tool cannot be used to copy share permissions.
	
	To copy the share permissions from one share to another by using the Permcopy.exe
	tool, use the "permcopy \\source_server\share_name
	\\destination_server\share_name" command, where "source_server\share_name" and
	"destination_server\share_name" are the universal naming convention (UNC) paths
	to the source and destination shares.
	
	NOTE: You cannot use the Permcopy.exe tool to copy the permissions of an
	administrative share (sharename$, such as, C$ or IPC$). If you copy the
	permissions to an administrative share that is located on an x86-based computer,
	the Services.exe program can stop responding.
	
	To Migrate Registry Keys, Services, and Other Objects
	-----------------------------------------------------
	
	The Subinacl.exe tool can be used to obtain security information on files,
	directories, registry keys, and services, and to transfer this information from
	user to user, from group to group, and from domain to domain.
	
	To migrate other domain objects by using the Subinacl.exe tool, use a command
	with the following syntax:
	
	  subinacl /object_type object_name /action=parameter /action=parameter
	
	The object types that can be manipulated by the Subinacl.exe tool include:
	
	- Registry keys and subkeys
	
	- Files
	
	- Directories
	
	- Shares
	
	- Services
	
	- Kernel objects
	
	The actions that can be performed on the preceding objects include:
	
	- Display
	
	- Change ownership
	
	- Replace all access control entries in the object
	
	- Change domain name of the object
	
	- Migrate the object from one domain to another
	
	An Example:
	
	To replace the security identifiers in all access control entries that contain
	"Domain1\Sales" with those of "Domain2\Sales", use the Subinacl.exe tool, and
	the following command:
	
	  subinacl /replace=domain1\sales=domain2\sales
	
	For more information about the syntax and the use of these tools, refer to the
	Rktools.hlp file in Windows NT Server 4.0 Resource Kit Supplement 3.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbAudDeveloper kbHOWTOmaster 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
