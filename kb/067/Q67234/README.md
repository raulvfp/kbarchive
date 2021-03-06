---
layout: page
title: "Q67234: QuickHelp Duplicate Search Brings Up Wrong Help"
permalink: /kb/067/Q67234/
---

## Q67234: QuickHelp Duplicate Search Brings Up Wrong Help

{% raw %}

	Article: Q67234
	Product(s): See article
	Version(s): 1.70   | 1.70
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | s_qh buglist1.70 SDK | mspl13_basic
	Last Modified: 17-DEC-1990
	
	In QuickHelp, if you select Duplicate Search from the View menu and
	enter a search string containing a wildcard, all the topics that match
	that string should appear. In some cases, however, all of the
	occurrences are NOT displayed, which causes the help topics to be out
	of sync with the information they bring up. When this problem occurs,
	you may select a topic, and help on a different topic will be
	displayed.
	
	One example of this problem occurs when searching on _dos* with the
	CLANG.HLP help file that comes with Microsoft C version 6.00. Another
	example is found when searching for wm_* in the SDKADV.HLP help file
	that comes with the Windows 3.00 Software Development Kit. In both
	cases, if you go to the end of the list of topics and bring up the
	information, the wrong help will be displayed.
	
	Microsoft has confirmed this to be a problem in QuickHelp version
	1.70. We are researching this problem and will post new information
	here as it becomes available.

{% endraw %}
