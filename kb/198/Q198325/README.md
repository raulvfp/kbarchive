---
layout: page
title: "Q198325: WD97: Bullets in Custom Bullet Style Change to Numbered"
permalink: /kb/198/Q198325/
---

## Q198325: WD97: Bullets in Custom Bullet Style Change to Numbered

{% raw %}

	Article: Q198325
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta word97
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you save a document that contains a custom style with a bullet as a Word
	6.0/95 (*.doc), the custom style changes to numbered when you reopen the
	document.
	
	For example:
	
	- When you click the Style list, the bullet for the custom style has changed to
	  "0" (the number zero).
	
	-or-
	
	- When you click Style on the Format menu, the description for the bullet style
	  indicates Numbered.
	
	-or-
	
	- When you reapply the custom style, the bullet changes to a number.
	
	NOTE: This problem occurs when you save using the Word 6.0/95 Binary converter as
	installed with Word 97 Service Release 1, with the Office 97 SR-1 Patch.
	
	RESOLUTION
	==========
	
	To prevent this problem from occurring, do one of the following:
	
	- In Word 97, save the file as a Word document, and then use the Word 97-2000
	  Import Converter to open the file in Word 6.0 or Word 7.0.
	
	  For additional information, please see the following article in the Microsoft
	  Knowledge Base:
	
	  Q162214 WD: How to Obtain the Word 97-2000 Import Converter
	
	-or-
	
	- In Word 97, save the file as Rich Text Format (*.rtf).
	
	-or-
	
	- In Word 97 only, save the file as Word 97 & 6.0/95 - RTF (*.doc).
	
	  NOTE: This save option is only available if you have installed the Microsoft
	  Office 97 SR-1 Enterprise Update CD. This save option is not available if you
	  have updated Word 97 using the Office 97 SR-1 Patch.
	
	  For additional information, please see the following article in the Microsoft
	  Knowledge Base:
	
	  
	
	  Q172475 OFF97: How to Obtain and Install MS Office 97 SR-1
	
	
	WORKAROUND
	==========
	
	Modify the bullet style by using one of the following methods.
	
	Method 1: Use the Style Window
	------------------------------
	
	1. Select the text that has the bullet style applied.
	
	2. Click the Style list and click to select the bullet style.
	
	  NOTE: The bullet style shows a 0 (zero) for the bullet.
	
	3. In the Modify Style dialog box, click to select Update the style to reflect
	  recent changes?, and then click OK.
	
	  NOTE: If you click to select Reapply the formatting of the style to the
	  selection?, numbering will be retained and the bullet format will be lost.
	
	Method 2: Use the Style Command on the Format Menu
	--------------------------------------------------
	
	1. Select the text that has the bullet style applied.
	
	2. On the Format menu, click Style.
	
	3. In the Style dialog box, under Styles, click to select the custom style, and
	  then click Modify.
	
	4. In the Modify Style dialog box, click Format, and then click Numbering.
	
	5. In the bullet gallery on the Bulleted tab, click to select the bullet you
	  want, and then click OK.
	
	6. Click OK to close the Modify Style dialog box.
	
	7. Do one of the following:
	   - Click Apply to apply your changes of the style to the selected text.
	
	  -or-     - Click Close to save your changes and close the Style dialog box.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	Additional query words: word97 8.0
	
	======================================================================
	Keywords          : kbdta word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
