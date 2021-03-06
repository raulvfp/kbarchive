---
layout: page
title: "Q130511: ScanDisk Fails Repairing Bad Allocated Cluster"
permalink: /kb/130/Q130511/
---

## Q130511: ScanDisk Fails Repairing Bad Allocated Cluster

{% raw %}

	Article: Q130511
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	ScanDisk for Windows (SCANDSKW.EXE) may fail to repair a bad cluster that is in
	use (allocated to a file), and you may receive the following error message:
	
	  ScanDisk was attempting to correct an error, but encountered another error
	  while writing to one of the drive's data area sectors.
	
	  ScanDisk can repair this error and detect other damaged sectors on the disk if
	  you choose to perform a thorough test now. However, the data stored in this
	  and any other damaged sectors may already be lost.
	
	CAUSE
	=====
	
	This error can occur if ScanDisk tries to write the data it could read from a
	bad cluster to a free cluster that is also bad (but has not yet been tested by
	ScanDisk).
	
	RESOLUTION
	==========
	
	To resolve this situation, follow these steps:
	
	1. Run ScanDisk again and choose the Thorough option. Ignore any bad clusters
	  that have files associated with them. Repair any bad clusters with no files
	  associated with them.
	
	2. Run ScanDisk again and choose the Thorough option. Repair any bad clusters
	  with associated files.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Windows 95. We are
	researching this problem and will post new information here in the Microsoft
	Knowledge Base as it becomes available.
	
	
	MORE INFORMATION
	================
	
	On uncompressed drives, ScanDisk tries to repair bad clusters that are allocated
	to files by writing any data that can be read from the bad cluster to a free
	cluster, then repairing the cluster chain and marking the cluster as bad in the
	FAT.
	
	When ScanDisk tries to write the data to a cluster that is also bad, ScanDisk
	should try to find another free cluster to write the data to. ScanDisk should
	fail only if it can find no other free clusters to write the data to. Instead,
	ScanDisk fails to repair the bad cluster and generates the error message stated
	above.
	
	Additional query words: scandisk/w dskmaint.dll
	
	======================================================================
	Keywords          :  
	Technology        : kbWin95search kbZNotKeyword3
	
	=============================================================================
	

{% endraw %}
