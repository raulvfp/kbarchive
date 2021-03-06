---
layout: page
title: "Q161868: WD97: Captions in Text Boxes Not Updated Correctly"
permalink: /kb/161/Q161868/
---

## Q161868: WD97: Captions in Text Boxes Not Updated Correctly

{% raw %}

	Article: Q161868
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbualink97
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In a Word document, when you insert or update captions in a text box, the
	captions may not be numbered correctly.
	
	Case 1: When Captions Are Inserted into the Same Text Box
	---------------------------------------------------------
	
	Multiple captions inserted into the same text box have the same caption number.
	
	Case 2: When Captions Are Inserted into Different Text Boxes
	------------------------------------------------------------
	
	Captions inserted in different text boxes are out of sequence with the captions
	in the main document text.
	
	Case 3: When Captions Are Inserted into Separate, Linked, Text Boxes
	--------------------------------------------------------------------
	
	Captions inserted into separate, linked, text boxes use an unexpected caption
	number or have the same caption number.
	
	CAUSE
	=====
	
	Case 1: Captions in the Same Text Box
	-------------------------------------
	
	Word can't correctly update multiple caption fields in the same text box. The
	caption updating is based on the placement of the text box anchor in the main
	text area of the document. Only one caption field can be associated with any one
	text box anchor. Therefore, multiple caption fields in the same text box will be
	given the same caption number.
	
	Case 2: Captions in Multiple Text Boxes
	---------------------------------------
	
	Word updates caption fields based on the placement of the text box anchor. If
	multiple text boxes are anchored to the same paragraph in the main text area of
	the document, Word can't update the caption fields in the desired sequence.
	
	Case 3: Captions in Linked Text Boxes
	-------------------------------------
	
	Each text box has an anchor in the main text area of the document. When text
	boxes are linked, each text box retains its own anchor (there is not just one
	anchor for all of the linked text boxes). Word cannot keep track of the multiple
	anchors, and, therefore, the caption numbers are updated incorrectly.
	
	WORKAROUND
	==========
	
	Case 1: Multiple Captions in a Single Text Box (Caption Numbers the Same)
	-------------------------------------------------------------------------
	
	To work around this problem, place only one caption in a text box. If additional
	captions are required in a text box, create another text box for the next
	caption.
	
	Case 2: Captions Out of Sequence
	--------------------------------
	
	Use the following steps to move the text box anchors to different paragraphs to
	achieve the desired caption numbering sequence:
	
	1. On the View menu, click Options.
	
	2. Click the View tab.
	
	3. Click the "Object Anchors" and "All" check boxes to select them, and then
	  click OK.
	
	4. Select the text box.
	
	  Gray hatch marks and white square handles will appear around the outside edges
	  of the text box. Also, an anchor will appear at a paragraph mark in the body
	  of the document.
	
	5. Drag the anchor to a different paragraph mark.
	
	Case 3: Captions in Linked Text Boxes
	-------------------------------------
	
	To work around this problem, use any of the following options:
	
	- Do not use captions in linked text boxes.
	
	  -or-
	
	- Use the following steps to unlink the text boxes:
	
	  1. Select the first text box in the sequence.
	
	  2. Right-click the selected text box.
	
	  3. On the shortcut menu, click "Break Forward Link."
	
	  Repeat this procedure for each text box containing a caption if you are
	  working with multiple linked text boxes.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the products listed at the
	beginning of this article.
	
	
	MORE INFORMATION
	================
	
	For more information about the features discussed in this article, click the
	Office Assistant, and use the following table to locate the specific subject you
	want to know more about.
	
	                        Type this in the          And click to
	For information about    Office Assistant balloon  view this topic
	------------------------------------------------------------------
	
	Creating text boxes      How do I make a text      Use a text box
	                        box?
	
	Linking text boxes       How do I link a text      Flow text to
	                        box?                      another part of
	                                                  my document with
	                                                  linked text boxes
	
	Breaking a text box      How do I break a text     Break a text box
	link                     box link?                 link
	
	Inserting a caption      How do I insert a         Add captions to
	                        caption?                  tables, figures,
	                                                  equations, or
	                                                  other items
	
	NOTE: If the Assistant is hidden, click the Office Assistant button on the
	Standard toolbar. If Word Help is not installed on your computer, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q120802 Office: How to Add/Remove a Single Office Program or Component
	
	Additional query words: 8.0 word8 word97
	
	======================================================================
	Keywords          : kbualink97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	
	=============================================================================
	

{% endraw %}
