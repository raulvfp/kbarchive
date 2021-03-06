---
layout: page
title: "Q271886: XADM: How to Use Mbconn  to Generate Active Directory Accounts"
permalink: /kb/271/Q271886/
---

## Q271886: XADM: How to Use Mbconn  to Generate Active Directory Accounts

{% raw %}

	Article: Q271886
	Product(s): Microsoft Exchange
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange 2000 Server 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to use the Mbconn utility (Mbconn.exe) to generate
	Active Directory accounts for mailboxes in the information store.
	
	MORE INFORMATION
	================
	
	Exchange Server 5.5 and earlier versions of Exchange Server are able to create
	user objects in the folder from an information store database by using the DS/IS
	consistency adjuster. In Exchange 2000, Mbconn.exe provides the same
	functionality.
	
	The Mbconn.exe performs two tasks. First, it uses information found in a given
	mailbox store to create an import file (in .ldf format) which can be used to
	create new accounts in Active Directory. Secondly, you can use Mbconn.exe to
	connect mailboxes to Active Directory accounts.
	
	NOTE: Mbconn.exe is located on the Exchange 2000 CD-ROM in the
	\Support\Utils\i386 folder. It is recommended that you read the Mbconn.chm file
	in the same folder. This file contains additional information about the Mailbox
	Reconnect tool.
	
	To create user accounts from information store objects:
	
	1. Mount the store that contains the mailboxes that you want to extract the
	  account information from.
	
	  NOTE: The mailboxes that do not have associated Active Directory user accounts
	  are displayed with a red X when you open Mailboxes under the Database object.
	  If no mailboxes are displayed with a red X, right-click the Mailboxes object,
	  and then click Run Cleanup Agent. When you do so, any mailboxes that do not
	  have an Active Directory account are marked with a red X. If you recently
	  mounted the store, it may take a few minutes before the Cleanup Agent marks
	  the mailboxes as disconnected.
	
	2. Run Mbconn.exe. When you are prompted by the wizard, enter the server and
	  domain controller name, and the database that you want to connect to.
	
	3. On the Actions menu, click Export Users.
	
	4. In the "Export Users to LDF File" dialog box, click the ellipse (...) next to
	  the Container space to browse to a container in Active Directory where you
	  want to create the user account, and then type the path and file name of the
	  import file (for example, <C:\Import>.ldf).
	
	5. Click the Advanced button, and then click to clear the default properties
	  that you do not want set.
	
	6. Click the Generate button to create the import file.
	
	7. At a command prompt, type "ldifde -i -f c:\import.ldf" (without the quotation
	  marks).
	
	For additional information about the LDIFDE tool, click the article number below
	to view the article in the Microsoft Knowledge Base:
	
	  Q237677 Using LDIFDE to Import/Export Directory Objects to the Active
	  Directory
	
	After all the accounts have been created in Active Directory, run Mbconn.exe
	again to connect the mailboxes to the new accounts.
	
	To connect mailboxes in the information store to user accounts:
	
	1. Run Mbconn.exe. When you are prompted by the wizard, enter the name of the
	  server and the domain controller, and the database that you want to connect
	  to.
	
	2. On the Actions menu, click Preview All.
	
	3. Click the container in Active Directory where the user accounts were imported
	  to. When the preview is finished, a green check mark is displayed next to
	  each item in the database that it is able to match with an Active Directory
	  account. Verify that the preview information is correct.
	
	4. On the Actions menu, click Apply.
	
	The mailboxes are now connected to the Active Directory accounts.
	
	Additional Information About the .ldf File Import Process
	---------------------------------------------------------
	
	- After a partial import, you have to edit the file and remove all the accounts
	  that were successfully created.
	
	  NOTE: The line number that indicates the failure is the first line of the
	  account that failed, and not necessarily the line that has a problem.
	
	- If there are lines that have a blank value, the import procedure is
	  unsuccessful. To fix this issue, either remove the line that has the blank
	  value, or add text at the end of the line.
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange2000Search kbExchange2000Serv
	Version           : :
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
