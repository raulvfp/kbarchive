---
layout: page
title: "Q179422: WD97: MS LineDraw Font Not Usable in Word"
permalink: /kb/179/Q179422/
---

## Q179422: WD97: MS LineDraw Font Not Usable in Word

{% raw %}

	Article: Q179422
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbgraphic
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In Microsoft Word 97, if you open a document from an earlier version of Word or
	from another word processing program that uses the MS LineDraw Font, you cannot
	use this font to draw lines or boxes.
	
	CAUSE
	=====
	
	The MS LineDraw font is included in earlier versions of Microsoft Word, MS- DOS,
	and Microsoft Windows 3.0, and is not intended as a drawing tool.
	
	This font is intended for importing documents that contain line drawings from
	MS-DOS based programs, such as WordPerfect. Word 97 identifies the MS LineDraw
	font as a symbol font, and interprets text in the MS LineDraw font as a series
	of symbols. Therefore, many formatting and proofing features of Word ignore this
	text.
	
	WORKAROUND
	==========
	
	To draw lines or boxes within Word, use the drawing tools and features that ship
	with Word to create lines, outlines, boxes and other shapes. To do this, follow
	these steps:
	
	1. Turn on the Drawing toolbar by pointing to Toolbars on the View menu, and
	  clicking Drawing.
	
	2. Use the Drawing toolbar buttons to draw the shapes you want.
	
	MORE INFORMATION
	================
	
	The Courier New font contains the exact same character set as MS LineDraw. Word
	97 should map the MS LineDraw font to Courier New; however, because there are
	several versions of the Courier New font, Word may or may not map it correctly.
	The Courier New version 2.0 font should allow the correct mapping of the MS
	LineDraw font.
	
	To access the line drawing characters that used to be available in MS LineDraw,
	click Symbol on the Insert menu, and then click (Normal Text) in the Font list.
	
	For additional information about the MS LineDraw font, please see the following
	article in the Microsoft Knowledge Base:
	
	  Q163059 WD97: Some Fonts Are Not Available in Word
	
	For more information about drawing tools in Word 97, click the Office Assistant,
	type "drawing tools," click Search, and then click one of the topics.
	
	NOTE: If the Assistant is hidden, click the Office Assistant button on the
	Standard toolbar. If Word Help is not installed on your computer, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q120802 Office: How to Add/Remove a Single Office Program or Component
	
	Additional query words: outline convert
	
	======================================================================
	Keywords          : kbgraphic 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
