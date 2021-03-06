---
layout: page
title: "Q160914: PRB: The Data File for &lt;file&gt; (&lt;physical file&gt;) Was Not Found"
permalink: /kb/160/Q160914/
---

## Q160914: PRB: The Data File for &lt;file&gt; (&lt;physical file&gt;) Was Not Found

{% raw %}

	Article: Q160914
	Product(s): Microsoft SourceSafe
	Version(s): 4.0,4.0a,5.0,6.0
	Operating System(s): 
	Keyword(s): kb3rdparty kbSSafe400 kbSSafe500 kbSSafe600
	Last Modified: 04-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, versions 5.0, 6.0 
	- Microsoft Visual SourceSafe, 16-bit, for Windows, versions 4.0, 4.0a 
	- Microsoft Visual SourceSafe, 32-bit, for Windows versions 4.0, 4.0a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When running the Analyze utility against a SourceSafe database, the following
	message appears:
	
	  The data file for <real file name > (<physical file name>) was
	  not found
	
	For example:
	
	  The data file for "myfile.txt" (qusaaaaa.b) was not found.
	
	This article discusses some of the steps that can be taken to resolve the
	problem.
	
	CAUSE
	=====
	
	Files under SourceSafe control are stored as a file pair: the data file and the
	log file. In this example, Analyze has found that a log file exists with no
	matching data file: there is a file qusaaaaa in the DATA\Q directory, but no
	matching qusaaaaa.b file. There may be a qusaaaaa.a (note that the extension is
	different from the one in the error message), but this does not change the
	approach to this problem.
	
	NOTE: This article will use the file names in the example error message given
	earlier.
	
	RESOLUTION
	==========
	
	
	Your first step should always be to back up the entire DATA directory. You should
	also make sure you are using the most recent version of Analyze.exe. Please see
	the REFERENCES section of this article for more information.
	
	There are three ways to resolve this error:
	
	1. Delete qusaaaaa from the DATA/Q subdirectory.
	
	2. Add a valid copy of qusaaaaa.b to the DATA/Q subdirectory.
	
	3. Delete Myfile.txt from the SourceSafe database, and then add it back.
	
	In many cases, there is a single copy of Myfile.txt in the database that has been
	deleted and removed permanently. If you are confident that this is the case,
	deleting qusaaaaa will resolve the problem. If you are not sure, see the MORE
	INFORMATION section later for guidelines on what course of action to take.
	
	Adding a valid copy of qusaaaaa.b can be done in two ways:
	
	1. This is the better method. If a user has a local copy of myfile.txt that is
	  identical to the last checked-in version, copy Myfile.txt into the DATA\Q
	  directory, and then rename the copy to qusaaaaa.b. It is important not to
	  leave a file named Myfile.txt in the data directory. You can see who last
	  checked the file in by viewing its History. If that user has a local copy
	  that has not been modified since the check in, this method will work.
	
	  It is also possible that a user may have performed a "Get Latest Version" of
	  Myfile.txt (though there is no way of testing to see if this has happened)
	  and has a local copy of the correct version of the file. If so, this method
	  will also work, but you must remove the read-only flag of qusaaaaa.b after
	  renaming it.
	
	  This method assumes that the SourceSafe user or administrator knows whether
	  the local version has been modified since the last Check Out or Get.
	
	2. If you have a backup of the database, copy the backup version of the file
	  pair into the DATA\Q subdirectory: qusaaaaa (the log file) and the
	  corresponding data file that will have either a .a or .b extension. In this
	  case, any changes made since the backup will be lost.
	
	  If you do not have a backup or a correct version of the file, the only
	  resolution is to delete myfile.txt from SourceSafe and add it back in. In
	  this case, you will lose all history and branching information.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	With Novell version 3.12 or later, on a Windows 95 computer using the Microsoft
	client for NetWare Networks (found under Control Panel .. Network ..
	Configuration), deleting a file from the SourceSafe database will delete only
	the data file, causing this error.
	
	The above configuration is known to cause a problem. It has been seen in other
	configurations, though not consistently reproduced. For the purpose of this
	article, the configuration is not important because it is suggesting ways of
	resolving the error, regardless of the cause.
	
	The following section provides some guidelines to help you determine whether you
	can delete the data file, or whether you need to add it back to the database:
	
	1. Is there a single copy of Myfile.txt, or multiple copies?
	
	2. What project or projects contain Myfile.txt?
	
	3. If there are multiple copies, are they different files in different projects
	  that happen to have the same name, or are they linked (has Myfile.txt been
	  shared or branched)?
	
	4. Has every occurrence of Myfile.txt been deleted from the database? If so, was
	  it purged or destroyed?
	
	Often, a user or the SourceSafe administrator will be able to answer these
	questions and the following steps will be unnecessary. The methods described
	here and the order in which they occur will vary from one case to another.
	
	You can answer the questions above using a combination of the following methods:
	
	1. Issuing this command at the SourceSafe command line interface:
	
	     SS Locate myfile.txt
	
	  will find all occurrences of Myfile.txt that have not been deleted, and those
	  that have been deleted but not removed permanently. If multiple copies of
	  Myfile.txt are found, use the SourceSafe Physical command to identify which
	  project contains which instance of myfile.txt.
	
	2. A recursive History of the top level project will tell what files have been
	  added, deleted, destroyed, purged, or branched.
	
	3. If a file has been shared, viewing the Links for that file will show which
	  projects share the file.
	
	4. If a file has been branched, viewing the Paths for that file will show which
	  projects contain branches of the file.
	
	NOTE: It is preferable to view Links and Paths from the command line interface
	because viewing from the SourceSafe Explorer will return errors. These errors
	can be ignored, but may be confusing.
	
	The log file, qusaaaaa, can be deleted only if all instances of myfile.txt that
	have a link or path to the copy that is causing the error have been removed
	permanently from the database.
	
	If this is not the case, locate a copy of myfile.txt that is identical to the
	last checked-in version. If no suitable copy exists, restore the file pair from
	a backup. Deleting and adding myfile.txt back should only be used in a "worst
	case" situation in which neither of the previous two methods is possible.
	
	REFERENCES
	==========
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q190881 SAMPLE: Analyze6.exe Utility for Visual SourceSafe
	
	Additional query words:
	
	======================================================================
	Keywords          : kb3rdparty kbSSafe400 kbSSafe500 kbSSafe600 
	Technology        : kbSSafeSearch kbAudDeveloper kbSSafe600 kbSSafe400 kbSSafe400a kbSSafe500 kbSSafe16bitSearch kbSSafe32bitSearch
	Version           : :4.0,4.0a,5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
