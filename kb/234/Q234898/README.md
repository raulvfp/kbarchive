---
layout: page
title: "Q234898: XCLN: How to Manage Outlook 97 with System Policies"
permalink: /kb/234/Q234898/
---

## Q234898: XCLN: How to Manage Outlook 97 with System Policies

{% raw %}

	Article: Q234898
	Product(s): Microsoft Exchange
	Version(s): 8.03,8.04
	Operating System(s): 
	Keyword(s): kbnetworkkbfaq
	Last Modified: 22-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Outlook 97, versions 8.03, 8.04, on platform(s):
	   - the operating system: Microsoft Windows 95 
	   - the operating system: Microsoft Windows 98 
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	System policies for Outlook 97 are a powerful mechanism for increasing control
	and management of Outlook 97 client computers across a network. System policies
	allow network administrators to provide greater consistency among client
	computers and to centralize support and maintenance efforts. Defined in a policy
	file, system policies can be used to enforce user and computer settings by
	overriding default registry values.
	
	NOTE: This article does not discuss how to set up and enforce system policies in
	detail. For an in-depth guide to Microsoft Windows NT 4.0 system policies,
	please refer to the "Implementing Profiles and Policies for Windows NT 4.0"
	white paper located at:
	
	  http://www.microsoft.com/NTServer/management/deployment/planguide/prof_policies.asp
	
	System policies are supported by Microsoft Windows 95, Microsoft Windows 98, and
	Microsoft Windows NT 4.0 Workstation only. The Macintosh and Microsoft Windows
	NT 3.51 Workstation operating systems do not support system policies.
	
	On Windows 95 and Windows NT 4.0, the registry settings are copied to the user's
	registry hive at logon time. A user who is experienced with editing the registry
	can modify the registry manually to avoid any administrator-defined policy for
	the current logon session. To prevent this policy hole, the administrator can
	set a policy on Registry Editor so that the user cannot run Registry Editor.
	This makes the hole smaller but it is still not foolproof because there is no
	way to restrict programmatic access to the registry. Windows 98 is a little more
	robust in that the registry settings are reset from the server on an
	administrator-defined interval (every 10 minutes, for example).
	
	MORE INFORMATION
	================
	
	System policies are defined by a system policy template file that associates
	each policy with the registry keys used by the application for the option that
	the policy represents.
	
	Outlook 97 System Policy Template
	---------------------------------
	
	The System Policy Editor settings specific to Outlook 97 are in the Outlk97.adm
	file. This template can be obtained from the Microsoft Office 97 Resource Kit.
	For Windows 95 and Windows 98 system policies, copy this template to the
	Windows\Inf folder. For Windows NT, copy this template to the Winnt\Inf folder.
	
	NOTE: Outlook 97 clients can also be controlled by using the Outlk98.adm file,
	the system policy template file for Outlook 98. This template also contains
	Outlook 98-specific policy settings that do not work on Outlook 97 clients. For
	additional information about managing Outlook with system policies, click the
	article numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q234896 XCLN: How to Manage Outlook 98 with System Policies
	
	  Q234899 XCLN: How to Manage Outlook 2000 with System Policies
	
	How to Create a New Policy File
	-------------------------------
	
	When you use System Policy Editor to create system policies, you first choose
	which templates you want to use, then create a new policy file, and then you set
	policies for your users. You cannot add templates after you have created the
	policy file.
	
	NOTE: When you create a system policy file for a client computer, you must run
	System Policy Editor on the same operating system that the client computer is
	running. For example, to create a policy file for Windows NT 4.0 clients, you
	must run System Policy Editor on Windows NT 4.0. This limitation results from
	the fact that Windows 95 and Windows 98 operating systems have different
	registries from Windows NT.
	
	To Open the Outlk97.adm Template:
	
	1. Start System Policy Editor, and make sure that all policy files are closed.
	
	2. On the Options menu, click Template for Windows 95 or Windows 98, or Policy
	  Template for Windows NT.
	
	3. For Windows 95 or Windows 98, click Open Template. For Windows NT, click Add.
	
	4. Click the Outlk97.adm file, and then click Open.
	
	5. Click Close to return to System Policy Editor.
	
	6. On the File menu, click New Policy to create a new policy file.
	
	To Add Users, Groups, or Computers to the Policy File:
	
	System policies can apply to all users, to a specific user, or to a group of
	users. They can also apply to a single computer or to all the computers on your
	network.
	
	The Default User icon and the Default Computer icon are included in your policy
	file. To apply a system policy to all the users or all the computers on your
	network, start System Policy Editor, and then double-click the Default User or
	Default Computer icon.
	
	You can also add specific users, computers, or groups to your policy file by
	using the Add User, Add Computer, and Add Group commands on the Edit menu in
	System Policy Editor. When you add a user, computer, or group, a new icon
	appears in System Policy Editor. Use this icon to set policies for the new user,
	computer, or group.
	
	NOTE: The group names or computer names that you specify in System Policy Editor
	must reference user groups or computers that already exist on the network. You
	cannot create new groups or computer names from within System Policy Editor.
	
	After you have selected the users, groups, or computers to whom your policy
	applies, set the policy or policies that you want by using the corresponding
	Properties dialog box in System Policy Editor. Sometimes a user is a member of
	more than one group. To avoid potential conflicts between group policies, you
	can set relative priorities so that group policies are applied in a particular
	order. To set group priorities, on the Option menu, click Group Priority.
	
	Setting the Policy:
	
	In System Policy Editor, when you double-click one of the user, group, or
	computer icons, the Properties dialog box appears, listing the available system
	policies. You scroll through the list of categories in the Properties dialog box
	to find the policy you want. You expand or collapse categories by clicking the
	plus sign (+) or minus sign (-), similar to expanding or collapsing folders in
	Windows Explorer. When you find the policy that you want, set the policy by
	clicking the check box next to the policy name. After you select the policy that
	you want, you must specify additional information under Settings to determine
	what is enforced by the policy.
	
	Saving and Distributing the Policy File:
	
	After you set the policy values that you want, you are ready to save and
	distribute the policy file. For Windows 95 or Windows 98 clients, save the
	policy file as Config.pol. For Windows NT 4.0 clients, save the policy file as
	Ntconfig.pol. Then, quit System Policy Editor.
	
	Next, you need to store the policy file on the network, where it can be
	downloaded to users' computers when they log on.
	
	For networks running Microsoft Windows NT Server, copy the Config.pol file or the
	Ntconfig.pol file to the Netlogon folder of the primary domain controller, as
	defined for your client computers. When your users next log on, the system
	policies are automatically downloaded to their computers, and their registry
	settings are updated with the policy settings.
	
	On Novell NetWare networks, copy the Config.pol file to the Public folder of the
	preferred server, as defined for your client computers.
	
	NOTE: For more information about Outlook 97 system policies, see Appendix C,
	"Registry Keys and Values" of the Microsoft Office 97 Resource Kit.
	
	Additional query words: ol97 8.03 8.04
	
	======================================================================
	Keywords          : kbnetwork kbfaq
	Technology        : kbOutlookSearch kbOutlook97Search kbZNotKeyword3
	Version           : :8.03,8.04
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
