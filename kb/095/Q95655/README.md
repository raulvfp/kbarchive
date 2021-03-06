---
layout: page
title: "Q95655: Errors Connecting to Server During Over-the-Network Setup"
permalink: /kb/095/Q95655/
---

## Q95655: Errors Connecting to Server During Over-the-Network Setup

{% raw %}

	Article: Q95655
	Product(s): Microsoft LAN Manager
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 30-JUL-2001
	
	SUMMARY
	=======
	
	You may receiving the following errors when you install or upgrade a Microsoft
	LAN Manager MS-DOS workstation with an over-the-network (OTN) installation
	disk:
	
	Error 1: Access Denied
	----------------------
	
	Cause: The server you are using for the network installation share must have a
	guest account.
	
	Error 2: Bad command or filename
	--------------------------------
	
	Cause: The guest and USER accounts must have read and execute (RX) privileges for
	the C:\LANMAN\NINSTALL directory.
	
	Error 3: Connection refused or syntax error
	-------------------------------------------
	
	Cause: The guest account must not have a password. Any or all of these can be
	caused by an incorrectly configured guest account on the server with the network
	installation share. Ways of correcting this are found in the MORE INFORMATION
	section below.
	
	Because this article deals with several problems arising from one cause, it
	differs in style from the usual PRB article.
	
	MORE INFORMATION
	================
	
	The OTN boot disk uses the LAN Manager basic workstation redirector. The program
	UNIQSTRT (listed in the AUTOEXEC.BAT of the OTN install disk) generates a random
	name so it can start the redirector with "net start workstation unique_name."
	
	A LAN Manager Basic MS-DOS workstation is not actually "logged on" to the domain
	and validated by the NETLOGON service, so no password is required. If you want
	to access a share with a password from an MS-DOS basic workstation, you must
	enter the password when you request access to the share (for example, NET USE
	\\SERVER\SHARE PASSWORD). If you fail to give the correct password for the
	account, you receive the following error:
	
	  connection refused or syntax error
	
	Therefore, if there is a password on the guest account, the OTN installation
	fails when it tries to access the install share on the server.
	
	There are several ways to remove the password on a guest account:
	
	- You can use NET ADMIN (Accounts, Users, Guest Zoom and then put spaces in the
	  password field, then backspace over the entire thing. (It's not elegant, but
	  it works.)
	
	- You can use the NET USER command, as follows:
	
	  net user guest ""
	
	- If you know what the password on your guest account is, you can use the NET
	  PASSWORD command:
	
	  net password oldpassword ""
	
	If there is some reason you want to have a password on your guest account, edit
	the NET USE line in the OTN install disk's AUTOEXEC.BAT as follows:
	
	  net use \\server\ninstall guestpassword
	
	Another problem can occur when you change the default name for the guest account
	using the optional entry "guestacct" in the [server] section of the LANMAN.INI.
	
	When you set up a server in a domain, LAN Manager installs a user account with
	the username guest and no password in the user accounts database. The "password
	required" parameter for the guest account is set to "no" (NET USER GUEST
	/PASSWORDREQ:NO).
	
	When you create any other user account, the default value for the /PASSWORDREQ
	parameter is "yes." If you don't change the password required parameter for your
	new guest account, the rules about password size will apply, and you may not be
	able to remove the password for your guest account. (You can use the Net
	Accounts command to check the minimum password length.)
	
	For example, the command
	
	  net user guest_account_name ""
	
	may return the error message:
	
	  NET2245: The password is shorter than required
	
	To resolve this problem:
	
	- Change the password required flag
	
	  net user visitor /passwordreq:no
	
	-or-
	
	- Change the minimum password length
	
	  net accounts /minpwlen:0
	
	REFERENCES
	==========
	
	Microsoft LAN Manager "Installation and Configuration Guide," Chapter 5:
	Installing and Upgrading MS-DOS Workstations
	
	Microsoft LAN Manager "Administrator's Guide," p. 75 (Guest Account)
	
	Microsoft LAN Manager "Administrator's Reference," pp. 29- 31 (NET ACCOUNTS), pp.
	75-76 (NET PASSWORD), and pp. 135-139 (NET USER)
	
	Additional query words: 2.20 2.2 redir rdr
	
	======================================================================
	Keywords          :  
	
	=============================================================================
	

{% endraw %}
