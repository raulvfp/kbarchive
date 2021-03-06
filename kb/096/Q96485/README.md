---
layout: page
title: "Q96485: MS-DOS Application Does Not Display Directories and Files"
permalink: /kb/096/Q96485/
---

## Q96485: MS-DOS Application Does Not Display Directories and Files

{% raw %}

	Article: Q96485
	Product(s): Microsoft LAN Manager
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 30-JUL-2001
	
	SYMPTOMS
	========
	
	MS-DOS applications such as Office Writer or Harvard Graphics will not display
	certain files and directories on the screen so that you can select them for file
	operations. To access them, you must enter the entire path and filename at the
	prompt.
	
	CAUSE
	=====
	
	When the application and its data files are installed on the server (HPFS386),
	for example in the \HG directory, the network administrator uses Permit Tree to
	copy the permissions (set on \HG) to its subdirectories and files. These
	subdirectories and files are now marked with the archive bit on. Applications,
	such as Office Writer and Harvard Graphics, look at the archive bit as a hidden
	attribute and do not display them on the screen as available.
	
	RESOLUTION
	==========
	
	- Use Netadmin to Revoke Tree, in our example, from the \HG directory. The
	  archive bit will be turned off.
	
	- You can set permissions at the \HG directory level and users can access the
	  subdirectories using the parent permissions.
	
	- If you want to set permissions to the subdirectories explicitly, highlight
	  the subdirectory and choose <View permissions>. Do not use Permit Tree.
	
	- You can also use OS/2 File Manager to check if the archive bit of a
	  subdirectory or file is set.
	
	Additional query words: 2.10
	
	======================================================================
	Keywords          :  
	
	=============================================================================
	

{% endraw %}
