---
layout: page
title: "Q187891: WD97: Spelling Checker Ignores Words in Uppercase Letters"
permalink: /kb/187/Q187891/
---

## Q187891: WD97: Spelling Checker Ignores Words in Uppercase Letters

{% raw %}

	Article: Q187891
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta kbproof word97
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you check the spelling in a document, the spelling checker may not flag
	misspelled words that are typed in capital letters (uppercase), or are formatted
	in All Caps or Small Caps.
	
	Additionally, if the spelling checker catches a misspelled word that is formatted
	with small caps, the words that appear in the Suggestions list are all
	uppercase. If you select one of these listed words and click Change, the
	spelling checker changes the word to full-size uppercase.
	
	CAUSE
	=====
	
	If the Ignore words in UPPERCASE option is selected, Word does not flag
	misspelled words that are typed in capital letters, including words that are
	formatted as small capital letters.
	
	RESOLUTION
	==========
	
	Turn off the Ignore words in UPPERCASE option. To do this, follow these steps:
	
	1. On the Tools menu, click Options.
	
	2. Select the Spelling and Grammar tab.
	
	3. Under Spelling, click to clear the Ignore words In UPPERCASE check box. Click
	  OK.
	
	WORKAROUND
	==========
	
	Manually correct the misspelled word in the Not in dictionary box of the
	Spelling and Grammar dialog box and then select Change.
	
	-or-
	
	After the spelling check is complete, select the unwanted uppercase words and
	change them back to lowercase (SHIFT+F3). The small caps format is still
	applied.
	
	Additional query words: setting capitol upper case stop suggest red wavy line
	
	======================================================================
	Keywords          : kbdta kbproof word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
