---
layout: page
title: "Q31155: &quot;Unable to Read TOOLS.INI&quot; Message Appears in OS/2 with MEP"
permalink: /kb/031/Q31155/
---

## Q31155: &quot;Unable to Read TOOLS.INI&quot; Message Appears in OS/2 with MEP

{% raw %}

	Article: Q31155
	Product(s): See article
	Version(s): 1.00
	Operating System(s): OS/2
	Keyword(s): ENDUSER | | mspl13_basic
	Last Modified: 8-JUN-1988
	
	MEP.EXE, the OS/2 version of the Microsoft editor, will give the
	following message when the INITIALIZE function is invoked (i.e.,
	SHIFT-F8 in the default keyboard setup):
	
	   "Unable to read TOOLS.INI"
	
	   This message will appear if the editor's name is left as MEP while
	the TOOLS.INI tag for the editor is labeled [M]. The two names must
	match.
	   To correct the problem, either rename the editor to M, or label the
	tag [MEP].
	   The tag can be set to [M MEP] if you wish to use the same TOOLS.INI
	settings for both real-mode and protected-mode versions of the editor.

{% endraw %}
