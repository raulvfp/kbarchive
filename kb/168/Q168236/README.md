---
layout: page
title: "Q168236: WD97: Outlook Address Book Not Available in Mail Merge Helper"
permalink: /kb/168/Q168236/
---

## Q168236: WD97: Outlook Address Book Not Available in Mail Merge Helper

{% raw %}

	Article: Q168236
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbsetup kbusage winword word97kbfaq
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you click Get Data in the Mail Merge Helper (on the Tools menu, click Mail
	Merge), you may experience either of the following symptoms:
	
	- The Use Address Book option may be unavailable.
	
	  -or-
	
	- When you click Use Address Book, Outlook Address Book may be unavailable.
	
	CAUSE
	=====
	
	The Address Book converter and tools are not installed. The converter and tools
	are required if you want to read the Microsoft Outlook Address Book.
	
	NOTE: The Address Book converter and tools are installed by default when you run
	a Typical Setup.
	
	WORKAROUND
	==========
	
	To resolve this issue, use the appropriate method for your situation.
	
	Method 1: Run the Microsoft Office 97 Setup Program
	---------------------------------------------------
	
	NOTE: Use this procedure only if you have either Microsoft Office 97 Standard
	Edition or Microsoft Office 97 Professional Edition. If you have Word 97 as a
	stand-alone version, Microsoft Office 97 Small Business Edition, or Microsoft
	Home Essentials 98, you need to use Method 2.
	
	1. In the "Microsoft Office 97 Setup" dialog box, click Add/Remove.
	
	2. Click Microsoft Word. (Do not clear the Microsoft Word check box.)
	
	3. Click Change Option.
	
	4. Click to select the Address Book check box.
	
	5. Click OK and then continue through the Office 97 Setup program dialog boxes
	  until Setup is complete.
	
	
	Method 2: Run the Word 97 Setup Program
	---------------------------------------
	
	NOTE: Use this procedure only when you have the Microsoft Word 97 stand-alone
	version, Microsoft Office 97 Small Business Edition, or Microsoft Home
	Essentials 98.
	
	1. In the Word 97 Setup dialog box, click Add/Remove.
	
	2. Click Office Tools. (Do not clear the Office Tools check box.)
	
	3. Click Change Option.
	
	4. Click to select the Address Book check box.
	
	5. Click OK and then continue through the Word 97 Setup program dialog boxes
	  until Setup is complete.
	
	
	NOTE: These methods do not work if the Outlook Address is not installed correctly
	before you try to use it with Microsoft Word.
	
	For additional information, click the article numbers below to view the articles
	in the Microsoft Knowledge Base:
	
	  Q221178 WD97: Unable to Use Mail Merge with Outlook Address Book
	
	  Q161349 OL97: Contact Information Does Not Appear in Address Book
	
	  Q170538 OL97: How to Mail Merge from Outlook Contacts to Word 97
	
	  Q160521 OL97: Categories Unavailable in Mail Merge to Word
	
	MORE INFORMATION
	================
	
	For more information about what is installed when you run a Typical Setup, click
	the Office Assistant, type "What is installed in a typical setup" (without the
	quotation marks), click Search, and then click to view the topic "What's
	installed with Word 97" (without the quotation marks).
	
	NOTE: If the Assistant is hidden, click the Office Assistant button on the
	Standard toolbar. If Microsoft Help is not installed on your computer, please
	see the following article in the Microsoft Knowledge Base:
	
	  Q120802 Office: How to Add/Remove a Single Office Program or Component
	
	Additional query words: offwinsetup 8.0 install conv convert converter sbe mailmerge
	
	======================================================================
	Keywords          : kbsetup kbusage winword word97 kbfaq
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
