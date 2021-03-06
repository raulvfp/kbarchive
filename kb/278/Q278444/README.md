---
layout: page
title: "Q278444: XCON: MTA Queue Building Up with No Association Opening"
permalink: /kb/278/Q278444/
---

## Q278444: XCON: MTA Queue Building Up with No Association Opening

{% raw %}

	Article: Q278444
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): exc55 kbExchange550preSP5fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	Messages may loop in a site when high-priority messages are sent. Message loops
	result in non-delivery reports (NDRs).
	
	CAUSE
	=====
	
	This problem can occur because of the way that high-priority messages are
	handled. The sequence of events is as follows:
	
	- High-priority messages are submitted on a server with a local X.400 connector
	  to the destination site. A new association is opened for each message; as a
	  result, nine associations are opened between the two sites.
	
	- When the next message arrives, the server tries again to open a new
	  association. The attempt does not work; it is rejected by the remote end
	  because the limit has been reached (the remote server logs a 57 event). If
	  there are other servers in the site that have equal-cost X.400 connectors to
	  the remote site, the message transfer agent (MTA) relays new high-priority
	  messages to a second bridgehead server. A similar process occurs; up to nine
	  associations are made between this second server and the remote site.
	
	- After all these associations are used, messages are relayed to a third
	  server.
	
	- After all the associations have been used on the third server, messages are
	  relayed back to the first. The first server now generates an NDR for the
	  message with a loop detect. The loop is detected by using the internal trace
	  information for each message extension.
	
	- After all the associations are open, even normal priority messages start to
	  loop.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft Exchange Server version 5.5 service pack that contains
	this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: MTA
	
	+----------------------------+
	| Dbserver.sch | 5.5.2654.38 | 
	+----------------------------+
	| Dcprods.cat  | 5.5.2654.38 | 
	+----------------------------+
	| Emsmta.exe   | 5.5.2654.38 | 
	+----------------------------+
	| Ems_rid.dll  | 5.5.2654.38 | 
	+----------------------------+
	| Mtacheck.exe | 5.5.2654.38 | 
	+----------------------------+
	| Infoplog.cfg | 5.5.2654.38 | 
	+----------------------------+
	| Mtamsg.dll   | 5.5.2654.38 | 
	+----------------------------+
	| Mtaperf.dll  | 5.5.2654.38 | 
	+----------------------------+
	| P42.tpl      | 5.5.2654.38 | 
	+----------------------------+
	| P772.tpl     | 5.5.2654.38 | 
	+----------------------------+
	| P2.xv2       | 5.5.2654.38 | 
	+----------------------------+
	| X400om.dll   | 5.5.2654.38 | 
	+----------------------------+
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5.
	
	
	
	Additional query words: looping fails
	
	======================================================================
	Keywords          : exc55 kbExchange550preSP5fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
