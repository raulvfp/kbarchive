---
layout: page
title: "Q89247: WD97: How Word for Windows Uses Temporary Files"
permalink: /kb/089/Q89247/
---

## Q89247: WD97: How Word for Windows Uses Temporary Files

{% raw %}

	Article: Q89247
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta word97kbfaq
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	This article explains when, where, and how Microsoft Word for Windows creates
	temporary files.
	
	MORE INFORMATION
	================
	
	Definition of a Temporary File
	------------------------------
	
	A program creates a temporary file to temporarily store information. The program
	determines where and when to create temporary files. Temporary files are
	available only for the current session of the program.
	
	Why Does Word Create Temporary Files?
	-------------------------------------
	
	Speed:
	
	Word sometimes copies portions of a file into memory so that it can access the
	information more quickly when you copy and paste or scroll through a document.
	Word references the location of the information instead of actually accessing
	the information, which reduces the time Word spends performing these functions.
	
	Data Integrity:
	
	Word's uses temporary files as a "safety net" to protect against system errors in
	its file saving scheme. By saving to a temporary file first and then renaming
	the file to the proper name, Word ensures the data integrity of your original
	file against problems (such as a power failure or lost network connections) that
	might occur while the file is being written.
	
	Types of temporary files
	------------------------
	
	MS-DOS-Based File:
	
	These are standard MS-DOS files.
	
	Document File Based File:
	
	The difference between this file and a traditional MS-DOS file is that multiple
	programs can read and write to these files without the original owner knowing
	about it. Additionally, document files have inherent properties that allow Word
	to create files and directories within files. At startup, Word creates one
	temporary (direct) document file called ~wrfxxxx.tmp. You can determine that it
	is a document file because the initial size is 1536 bytes. This temporary
	document file is used to store all OLE objects belonging to unnamed documents,
	undo, the Clipboard, and to documents whose native formats are not document
	format (for example, .txt, .rtf, and Word 2.0 documents). Word can open document
	files using two different modes: transacted and direct. These modes are
	discussed later in this article.
	
	Transacted Document Files:
	
	Transacted files allow Word to open a file, write to it, and have other
	programs--such as Microsoft Excel--write to it, but still retain the right to
	restore the file to the state it was in when Word first opened it.
	
	To do this, the document file creates ghost images (typically ~dftxxxx.tmp) of
	all the changes made to the file after it was opened; if Word keeps all the
	changes, the contents of ~dftxxxx.tmp merge with the original file, and then
	saves a complete version of it. On the other hand, if Word discards all changes,
	then ~dftxxxx.tmp is deleted, and the original file does not change. Word opens
	all of the Word native files using transacted files, which create ghost images
	in the Temp directory. When you start Word, Normal.dot is typically opened in
	transacted mode, and a ghost file is created for it called dftxxxx.tmp.
	FastSave, for example, merges these two files when a save occurs.
	
	Direct:
	
	Word uses direct storage when opening the temporary document file and when
	performing either a Save As or a Full Save (non-FastSave save). This type of
	file is a low (if any) consumer of memory and does not create a ghost image when
	created or opened.
	
	Specific Files That Word Creates
	--------------------------------
	
	The following tables list some of the specific temporary files that Word
	creates.
	
	  Files typically created when Word is started                File name
	  ------------------------------------------------------------------------
	  MS-DOS-based file (to reserve 4 file handles) 0 bytes      ~wrf0000.tmp
	  MS-DOS-based scratch file                     0 bytes      ~mfxxxx.tmp
	  Compound file - transacted                    0 bytes      ~dftxxxx.tmp
	  Compound file - direct                        1536 bytes   ~wrf0001.tmp
	                  (unnamed non-Word/OLE files)
	
	  Word recovery files                                        File name
	  -----------------------------------------------------------------------
	  Temporary file for AutoRecovery                         ~wraxxxx.tmp
	  AutoRecovery                                    AutoRecovery save of 
	                                                  <docname>.asd
	
	  Other Word temporary files                                 File name
	  -----------------------------------------------------------------------
	  Copy of another document                                   ~wrcxxxx.tmp
	  Word document                                              ~wrdxxxx.tmp
	  Temp document file                                         ~wrfxxxx.tmp
	  Dictionary                                                 ~wrixxxx.tmp
	  Clipboard                                                  ~wrlxxxx.tmp
	  Macro                                                      ~wrmxxxx.tmp
	  Word OLE document                                          ~wroxxxx.tmp
	  Scratch file                                               ~wrsxxxx.tmp
	  Converted (foreign) document                               ~wrvxxxx.tmp
	
	A Simplified View of the Scheme Used to Save an Edited File
	-----------------------------------------------------------
	
	Create temp file                     Create ~wrdxxxx.tmp
	Write temp file                      Save example data to ~wrdxxxx.tmp
	Delete original file                 Delete EXAMPLE.DOC
	Rename temp to target name           Rename ~wrdxxxx.tmp to Example.doc
	
	Word gains significant performance speed by placing the temporary file in the
	same directory as the saved file. If Word placed the temporary file elsewhere,
	it would have to use the MS-DOS COPY command to move the temporary file from the
	other directory to the saved location. By leaving the temporary file in the same
	directory as the saved document file, Word can use the MS-DOS MOVE command to
	quickly designate the temporary file as the saved document.
	
	When and Where Word Creates Temporary Files
	-------------------------------------------
	
	The location of where Word creates the temporary files is hard-coded information
	and cannot be edited. In general, Word creates temporary files for the following
	types of data.
	
	Embedded Word Objects (Temp Directory):
	When Word acts as an OLE server program, the embedded Word objects are stored as
	temporary files in the Temp directory.
	
	OLE 2.0 requires extra drive storage. When you start OLE programs, Word needs to
	provide copies of the data to the server. It is not unusual for extensive OLE
	2.0 usage in a single session of a program to accumulate a large amount of
	temporary storage on the hard drive.
	
	Scratch File (Temp Directory):
	
	When Word runs out of internal random access memory (RAM), it always creates a
	single temporary scratch file in the Temp directory to hold information. This
	scratch file holds information that is swapped out from the Word internal file
	cache, which is allocated from global system memory. The scratch file varies in
	size from 64 kilobytes (KB) to 3.5 megabytes (MB). You can prevent Word from
	having to write to the scratch file by allocating more RAM for Word to use
	internally.
	
	The default cachesize in Word is 64 KB.
	
	For more information about increasing the cachesize in Word, please see the
	following article in the Microsoft Knowledge Base:
	
	  
	
	  Q157464 WD97: Where Settings Are Stored in the Registry
	
	Recorded Macro (Temp Directory):
	
	When you record a macro, Word creates a temporary file in the Temp directory.
	
	Converted Files (Temp Directory):
	
	The word processor converters supplied with Word create temporary files in Rich
	Text Format (RTF), which Word uses to access specific converters.
	
	Locked Files (Temp Directory):
	
	When you open a file that is locked, either because it is open in another window
	of Word or because another user on the network has it open, you can work with a
	copy of the file. Word places this copy in the Windows Temp directory. Likewise,
	if a template attached to a document is locked, Word automatically makes a copy
	of the template in the Temp directory. The copy of a locked file does not
	automatically update the original owner's file.
	
	Saved Files (Same Directory as the Saved File):
	
	When you click Save on the File menu, the following happens:
	
	  - Word builds a new temporary file using the edited version of the document.
	
	  - Once Word successfully creates the temporary file, Word deletes the previous
	  version of the document.
	
	  - Word renames the temporary file to the same name as the previous version of
	  the document.
	
	Text Pasted Between Files (Same Directory as Source File):
	
	When Word copies and pastes between documents, it may create a temporary file in
	the same directory as the source file--especially if the source file is saved or
	closed. The temporary file represents the information that was referenced by the
	Clipboard prior to saving the file. Word creates this temporary file by renaming
	the old copy of the file to a temporary file name.
	
	Owner File (Same Directory as Source File):
	
	When a previously saved file is opened for editing, printing or review, Word
	creates a temporary file with a .doc file name extension that begins with a
	tilde "~" followed by a dollar sign "$" followed by the remainder of the
	original file name. This temporary file holds the logon name of person opening
	the file and is known as the "owner file." When you attempt to open a file that
	is available on a network and is already open by someone else, this file
	supplies the <user name> for the following error message:
	
	  "This file is already opened by <user name>. Would you like to make a
	  copy of this file for your use?"
	
	  If the Owner File is damaged or missing the error message changes to:
	
	  "This file is already opened by another user. Would you like to make a copy
	  of this file for your use?"
	
	Word automatically deletes this temporary file when the original file is closed
	from memory.
	
	Automatic Save:
	
	Word 97 Auto Recover Save Directory:
	
	  The temporary file created when Word performs an automatic save is stored in
	  the Temp folder, unless there is not a valid Temp folder; Word then saves the
	  temporary file in the same folder where it saves the document.
	
	The Location of Temporary Files When You Close a File
	-----------------------------------------------------
	
	Word may occasionally have to maintain a link to a file after it is closed. This
	occurs when text has been copied to the Clipboard from the file. When you close
	a file, Word attempts the following actions:
	
	- If the selection that was copied to the Clipboard does not contain multiple
	  sections or a picture, or is not large, Word copies the piece of the document
	  to the scratch file.
	
	- If the copied selection does contain pictures or multiple sections, or if the
	  file is on a floppy disk, Word copies the entire file to the Temp directory
	  and moves the pointer there.
	
	
	Additional query words: tmp temp
	
	======================================================================
	Keywords          : kbdta word97 kbfaq
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
