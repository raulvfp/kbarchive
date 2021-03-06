---
layout: page
title: "Q140344: WD97: How to Convert Data in One Column to a Table for Merging"
permalink: /kb/140/Q140344/
---

## Q140344: WD97: How to Convert Data in One Column to a Table for Merging

{% raw %}

	Article: Q140344
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): kbualink97 winword word97 kbmerge
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	When you use Word to merge documents, data cannot be located in a single column,
	as in the following example:
	
	  John Doe
	  123 Main Street
	  Anytown, US 12345
	
	  Jane Smith
	  Microsoft
	  456 Elm Street
	  Sometown, US 67890
	
	Instead, the information must be laid out in a table or in tab-delimited format,
	such as the following:
	
	  Name       Company    Address           City/State    ZIP_Code
	  John Doe              123 Main Street   Anytown, US   12345
	  Jane Smith Microsoft  456 Elm Street    Sometown, US  67890
	
	This article explains how you can change data from being in one column to a
	format that Word can use.
	
	MORE INFORMATION
	================
	
	Data Documents Created in Other Programs
	----------------------------------------
	
	If you created your data document in a different program, find out whether that
	program can save the data in a different layout. For example, if the data came
	from a database program, can it save the file with different field and record
	delimiters? If it can save the data with tab field delimiters and paragraph mark
	record delimiters, you can use the file in Word without any further
	modifications. For information on using a text file as a data document in Word,
	search in Help under merging and using data sources.
	
	WordPerfect Data Documents
	--------------------------
	
	For more information on using WordPerfect data documents with Word, please see
	the following article in the Microsoft Knowledge Base:
	
	  Q72117 WD: How to Convert WordPerfect Merge Data Documents to Word
	
	Convert Text to Table in Word
	-----------------------------
	
	If you created the list of addresses in Word, or if you cannot rearrange the data
	using another program, convert the text to a table, which Word can use for
	merging. To do this, follow these steps:
	
	1. Save the file containing the list of names with a different file name. Modify
	  the version of the file with the new name (this way, if you make a mistake,
	  you can start over with your original document).
	
	2. Rearrange the names in the file. The following steps require that each
	  address is separated with a blank line (see the example in the "Summary"
	  section at the beginning of this article).
	
	  NOTE: This method creates a separate field for each line in each address. If
	  you want the information separated further than this, you must press the TAB
	  key at the appropriate points. For instance, if you have typed a first and
	  last name on the same line, the method below creates one field that contains
	  both first and last names. If you want the first and last names to be in
	  separate fields, you must place the insertion point between each first and
	  last name and press the TAB key.
	
	  Also, this method puts the lines into the first available field for each
	  record, so if the records do not have the same number of lines, shorter
	  records will end up with information in different fields than the longer
	  records. If you want to perform conditional merges, in which a certain type
	  of information is expected in certain fields, you need to edit the data file
	  once you have created the table.
	
	  Part 1: Remove Blank Lines Between Records:
	
	  a. On the Edit menu, click Replace.
	
	  b. Click in the Find What box.
	
	  c. Click Special, and select Paragraph Mark. Do this again, so that the Find
	     What box shows "^p^p" (without the quotation marks).
	
	  d. If the No Formatting button is available (not shaded), click this button
	     to remove any additional Find formatting criteria.
	
	  e. Click in the Replace With box.
	
	  f. Type three percent signs.
	
	  g. If the No Formatting button is available (not shaded), click this button
	     to remove any additional Replace formatting criteria.
	
	  h. Click Replace All.
	
	     The document now shows the beginning of each record next to the end of the
	     preceding record, separated by three percent symbols:
	
	  John Doe
	  123 Main Street
	  Anytown, US 12345%%%Jane Smith
	  Microsoft
	  456 Elm Street
	  Sometown, US 67890
	
	  Part 2: Replace Paragraph Marks with Tab Characters:
	
	  1. Click in the Find What box, and delete the existing text.
	
	  2. Click the Special button and select Paragraph Mark.
	
	     The Find What box now shows ^p.
	
	  3. Click in the Replace With box, and delete the existing text.
	
	  4. Click the Special Button and select Tab Character.
	
	     The With box now shows ^t.
	
	  5. Click Replace All.
	
	     The document shows all records in what appears to be one paragraph:
	
	              John Doe  123 Main Street  Anytown, US  12345%%%Jane
	              Smith     Microsoft        456 Elm Street   Sometown,
	              US  67890
	
	     NOTE: This method produces one extra field when the final paragraph is
	     replaced with a tab. You should delete this final tab.
	
	  Part 3:
	
	  a. Click in the Find What box, and delete the existing text. Type three
	     percent signs.
	
	  b. Click in the Replace With box, and delete the existing text.
	
	  c. Click Special and select Paragraph Mark. Click Replace All.
	
	  d. Click Close to close the Find And Replace dialog box.
	
	  The text is now in the proper format to be converted to a table.
	
	3. On the Edit menu, click Select All.
	
	4. On the Table menu, click Convert Text To Table.
	
	5. In the Separate Text At area, select Tabs.
	
	6. Click OK. The data is now in columns.
	
	7. Click in the first cell of the table. On the Table menu, click Insert Rows.
	
	8. In the first row, type a one-word field name for each column.
	
	9. On the File menu, click Save.
	
	NOTE: As previously mentioned, if the data for a specific field is in different
	columns, you need to move the data for those fields to one column. If a column
	becomes blank, delete it by following these steps:
	
	1. Place the insertion point into the column.
	
	2. On the Table menu, click Delete Columns.
	
	The data document is now ready to merge with a Word main document.
	
	Additional query words: howto grey convert 8.0 8.00
	
	======================================================================
	Keywords          : kbualink97 winword word97 kbmerge 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
