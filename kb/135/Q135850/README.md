---
layout: page
title: "Q135850: SMS: No Query Results Returned When SQL Tempdb Is Too Small"
permalink: /kb/135/Q135850/
---

## Q135850: SMS: No Query Results Returned When SQL Tempdb Is Too Small

{% raw %}

	Article: Q135850
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.0,1.1,1.2
	Operating System(s): 
	Keyword(s): kbnetwork kbConfig kbDatabase smsconfig smsdatabase
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 1.2, 1.0, 1.1 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If you run a query that requires more space than is allocated for tempdb, no
	return is displayed and no errors are given.
	
	By default, Systems Management Server sorts the query results before displaying
	them. This sorting is done in tempdb.
	
	WORKAROUND
	==========
	
	To work around this problem, do either of the following:
	
	- If this problem exists for a single large query, try to refine the query so
	  that the query result is smaller.
	
	  -or-
	
	- Increase the size of tempdb.
	
	For more information on device size recommendations and free space requirements,
	see the MORE INFORMATION section of this article.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 1.0, 1.1, and 1.2.
	
	MORE INFORMATION
	================
	
	DEVICE SIZE RECOMMENDATIONS
	---------------------------
	
	- The data and log devices should each be a minimum of 10 MB.
	
	- For each computer, allocate 35 KB of data device space.
	
	- For the site database, the log device should be at least 10 percent of the
	  data device.
	
	- The data device for the tempdb should be at least 20 percent of the data
	  device for the site database.
	
	- For the tempdb database, the log device should be at least 20 percent of the
	  data device.
	
	For example, on a site of 10,000 computers:
	
	- The site data device would be 35 KB x 10,000 computers, resulting in a 350 MB
	  data device and (.10 x 350 MB = 35 MB) 35 MB log device.
	
	- The tempdb data device would be (.20 x 350 MB), for a 70 MB data device and
	  (.20 x 70 MB) for a 14 MB log device.
	
	FREE SPACE REQUIREMENTS IN THE DATABASE
	---------------------------------------
	
	To find the space used in the data device, run the sp_spaceused stored procedure
	against the database. Divide the space reserved by the size of the data device.
	If this is over 90 percent for the site database, expand the database. If this
	is over 60 percent for the tempdb data device, expand the database. The tables
	in tempdb are all temporary, so this needs to be checked at peak usage, when
	several Administrator user interfaces are querying the database. The
	Administrator user interfaces put more of a load on tempdb than the site can, so
	even a few can consume the space recommended above.
	
	You can use Windows NT Performance Monitor to observe the log device usage. If
	any of these get over 60 percent, expand the database.
	
	Additional query words: prodsms perfmon admin
	
	======================================================================
	Keywords          : kbnetwork kbConfig kbDatabase smsconfig smsdatabase 
	Technology        : kbSMSSearch kbSMS100 kbSMS110 kbSMS120
	Version           : winnt:1.0,1.1,1.2
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
