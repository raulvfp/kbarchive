---
layout: page
title: "Q140294: HOWTO: Append Records from Any Delimited File with Memo Data"
permalink: /kb/140/Q140294/
---

## Q140294: HOWTO: Append Records from Any Delimited File with Memo Data

{% raw %}

	Article: Q140294
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:2.5b,2.5c,2.6a; MS-DOS:2.5,2.5a,2.5b,2.6,2.6a; WINDOWS:2.5,2.5a,2.5b,2.6,2.6a
	Operating System(s): 
	Keyword(s): kbcode kbvfp kbvfp600
	Last Modified: 28-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 6.0 
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a, 2.5b, 2.6, 2.6a 
	- Microsoft FoxPro for MS-DOS, versions 2.5, 2.5a, 2.5b, 2.6, 2.6a 
	- Microsoft FoxPro for Macintosh, versions 2.5b, 2.5c, 2.6a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article shows by example how to append records from any delimited ASCII
	text file into a predefined FoxPro table or .dbf file.
	
	The intent of the program listed in this article is twofold. The first is to
	address the inability of the APPEND command to read data into a memo field. The
	second is to provide a wider range of support for source file formats that the
	APPEND command does not support.
	
	MORE INFORMATION
	================
	
	Here's an excerpt from the Visual FoxPro APPEND FROM Help Topic:
	
	  "A delimited file is an ASCII text file in which each record ends with a
	  carriage return and linefeed. Field contents are by default assumed to be
	  separated from each other by commas, and character field values to be
	  additionally delimited by double quotation marks."
	
	The program listed in this article does not require linefeeds after the carriage
	return, nor does it require that character data be delimited by double quotation
	marks. Also, files do not have to be terminated with an end-of-file marker (^Z),
	but the program will work fine if the end-of-file marker is present. This
	flexibility is necessary because many applications do not export their data in a
	format suitable for FoxPro's APPEND FROM command.
	
	Numeric, Float, Double, Integer, Currency, Date, and Memo fields from delimited
	files can be imported if the data is in proper format. The date format defaults
	to mm/dd/yy. Including the century portion of a date is optional. FoxPro will
	import a date, such as 12/25/95, that doesn't include the century assuming the
	date is in the twentieth century.
	
	Date delimiters can be any non-numeric character except the delimiter that
	separates the fields in the delimited file. Dates in other formats can be
	imported if their format matches a date format available in SET DATE. To import
	dates that are not in the default format, issue SET DATE with the proper date
	format before using the program listed in this article (Appendm.prg). To test if
	a date format can be successfully imported, use it with CTOD(). If the date is
	acceptable to CTOD(), the date will import properly.
	
	Character strings with a length in excess of 10,000 characters have been tested
	and work fine when imported into a memo field.
	
	NOTE: Do not use a delimiting character that appears in the actual data.
	
	Sample Code
	-----------
	
	       Appendm.prg
	      
	       Purpose:
	      
	         * Append records from any delimited ASCII text file into a
	         * predefined FoxPro table or .dbf file. The intent of this program
	         * is twofold. The first is to address the inability of the
	         * APPEND command to read in data into a memo field. The second
	         * is to provide a wider range of support for source file formats.
	      
	       Syntax:
	      
	         DO AppendM [WITH <expC1>, <expC2&>[, <expC3>[, <expC4>]]]
	      
	       Parameters:
	      
	        <expC1>
	      
	       *   Specify the full name of the ASCII text file to append from
	       *   with extension. If this parameter is used, then <expC2> and
	       *   optionally <expC3> must be specified also. If this
	       *   parameter is not specified, the user will be prompted for the
	       *   file.
	      
	        <expC2>
	      
	       *  Specify the field-delimiting character. This parameter must
	       *  be used if <expC1> is specified. If <expC1> is not 
	       *  specified, this parameter is ignored.
	             
	           Samples:    ','    = COMMA
	                       CHR(9) = TAB
	
	         <expC3>
	      
	      *  Specify the character field delimiting character. Use the
	      *  null string ("") for none. This parameter is optional if
	      *  <expC1> is specified. If <expC1> is not specified, this
	      *  parameter is ignored.
	      
	        <expC4>
	      
	      *  Specify the name of the table or .dbf file to append to. If the
	      *  extension is not specified, .dbf is assumed. If a table or .dbf
	      *  file is open in the current work area, this parameter will be
	      *  ignored and the open table will be used.
	      
	       Examples:
	      
	      *  For full prompting:
	      
	            DO AppendM
	      
	      *  For a source file with comma-delimited fields and double-quotation-
	      *  mark delimited character fields:
	      
	            DO AppendM WITH 'SRCFILE.TXT', ',', '"'
	      
	      *  For a source file with tab-delimited fields and no character
	      *  field delimiter:
	      
	            DO AppendM WITH 'SRCFILE.TXT', CHR(9)
	      
	      *  For a source file with comma-delimited fields and double-quotation-
	      *  mark delimited character fields with the current work area unused:
	      
	            DO AppendM WITH 'SRCFILE.TXT', ',', '"', 'DESTFILE.DBF'
	      
	       Notes:
	      
	      *  Before using this program, ensure that the target table or
	      * .dbf file is structured to accept the data from the source
	      *  file, and ensure that the source file is in ASCII file format.
	      
	      *  Each record in the source file must be terminated with a
	      *  carriage return (CR). Linefeeds (LF) following a CR are
	      *  also supported. The program will address text files with
	      *  any field delimiters. Character data fields may optionally be
	      *  delimited. An end-of-file marker (^Z) is supported but not
	      *  required.
	                                                                            
	     PARAMETERS cTextFile, cFieldDelim, cChrFldDelim, cTableFile
	                                              
	     IF TYPE( "cTextFile" ) = 'L'
	                                                    
	        cTextFile = ''
	                                                     
	     ENDIF
	     IF TYPE( "cFieldDelim" ) = 'L'
	                                                    
	        cFieldDelim = ''                              
	                        
	     ENDIF
	     IF TYPE( "cChrFldDelim" ) = 'L'
	                                                    
	        cChrFldDelim = ''
	                                                      
	     ENDIF
	     IF TYPE( "cTableFile" ) = 'L'
	                                                    
	        cTableFile = ''
	                                                      
	     ENDIF                      
	                            
	      *  Attempt to get and/or open the table or .dbf file
	      *  If successful, continue; otherwise, Return
	      
	     IF USED()
	                                                   
	        cDBF_File = ALIAS()
	                                                      
	     ELSE
	                                                    
	        IF EMPTY( cTableFile )
	           cDBF_File = GETFILE( 'DBF', 'Append to:')
	        ELSE
	           IF !FILE( cTableFile ) AND !FILE( cTableFile + '.DBF' )
	              cDBF_File = GETFILE( 'DBF', 'Append to:')
	           ELSE
	              cDBF_File = cTableFile
	           ENDIF
	        ENDIF
	        IF !EMPTY( cDBF_File )
	           USE (cDBF_File)
	        ELSE
	           ?? CHR(7)
	           WAIT WINDOW "No Table/DBF Selected to Append To!"
	           RETURN
	        ENDIF
	                                                      
	     ENDIF
	                                                  
	      *  Attempt to get ASCII text file
	      *  If successful, continue; otherwise, Return
	      
	     IF EMPTY( cTextFile )
	                                                    
	        cTXT_File = GETFILE( 'TXT', 'Source:')
	                                                      
	     ELSE
	                                                    
	        IF !FILE( cTextFile )
	           cTXT_File = GETFILE( 'TXT', 'Source:')
	        ELSE
	           cTXT_File = cTextFile
	        ENDIF
	                                                      
	     ENDIF
	     IF EMPTY( cTXT_File )
	                                                   
	        ?? CHR(7)
	        WAIT WINDOW "No Text File Selected to Append From!"
	        RETURN
	                                                      
	     ENDIF
	                            
	      *  Verify Delimiting Characters. If successful,
	      *  continue; otherwise, Return
	      
	     IF EMPTY( cTextFile )
	                                                    
	        DEFINE WINDOW wGetDelims ;
	           FROM 1,1 TO 15,60 ;
	           TITLE "Delimiters" ;
	           NOCLOSE NOFLOAT NOGROW NOMDI NOMINIMIZE NOSHADOW NOZOOM
	        MOVE WINDOW wGetDelims CENTER
	        ACTIVATE WINDOW wGetDelims NOSHOW
	        CLEAR
	        @3,10 SAY "Press the Field Delimiting Character"
	        @5,10 SAY "ie.. COMMA = <,> or TAB = <TAB KEY>"
	        @7,29 say "" COLOR I
	        ACTIVATE WINDOW wGetDelims
	        nFieldDelim = INKEY(0,'S')
	        IF nFieldDelim = 9 or nFieldDelim > 32 and nFieldDelim < 127
	           cFieldDelim = CHR( nFieldDelim )
	        ENDIF
	        @3,5 SAY "Press the Character Field Delimiting Character"
	        @5,6 SAY "Typically DOUBLE-QUOTE, Press ENTER for None"
	        @7,29 say "" COLOR I
	        nChrFldDelim = INKEY(0,'S')
	        CLEAR
	        IF nChrFldDelim > 32 and nChrFldDelim < 127
	           cChrFldDelim =CHR( nChrFldDelim )
	           ELSE
	             cChrFldDelim = ""    && No delimiter
	        ENDIF
	        DEACTIVATE WINDOW wGetDelims NOSHOW
	        RELEASE WINDOW wGetDelims
	                                                      
	     ENDIF
	                                            
	     IF LEN( cFieldDelim ) = 0
	                                                
	        ?? CHR(7)
	        WAIT WINDOW "No Field Delimiting character Specified!"
	        RETURN
	                                                      
	     ENDIF
	                                              
	      *  Attempt to open text file with low-level handle.
	      *  If the test is successful, continue; otherwise,
	      *  report reason for failure.
	      
	     nFileHandle = FOPEN( cTXT_File )
	     IF nFileHandle < 0
	                        
	                              
	        DO ErrHand WITH FERROR(), cTXT_File
	        RETURN .F.
	                                
	                        
	     ENDIF
	      
	      *  Create an array of database structure.
	      *  Determine number of records in array for
	      *  loop counting.
	      
	     =AFIELDS( aStructure )
	     nRows = ALEN( aStructure, 1 )
	                                                 
	      *  Begin DO WHILE loop and continue until end of
	      *  file marker is reached in text file.
	                                               
	     nFileSize = FSEEK( nFileHandle, 0, 2 )
	     = FSEEK( nFileHandle, 0, 0 )
	     nBytesRead = 0
	     RecsApnd = 0
	     lChrFldDelimFlag = LEN(cChrFldDelim ) # 0
	     WAIT WINDOW ' Records Appended: ' + LTRIM( STR( RecsApnd )) + ;
	                        
	                              
	       CHR(13) + ' Percent Completed: ' + ;
	       LTRIM( STR( nBytesRead/nFileSize 100)) NOWAIT
	                                
	                        
	     DO WHILE !FEOF( nFileHandle )
	                        
	                              
	        APPEND BLANK
	        FOR i = 1 TO nRows
	           cFieldData = ReadField( cFieldDelim, cChrFldDelim )
	           DO CASE
	              CASE aStructure[i,2] $ "NY"
	                REPLACE &aStructure[i,1] WITH VAL( cFieldData )
	              CASE aStructure[i,2] = "D"
	                 REPLACE &aStructure[i,1] WITH CTOD( cFieldData )
	               OTHERWISE
	                 REPLACE &aStructure[i,1] WITH cFieldData
	           ENDCASE
	             WAIT WINDOW ' Records Appended: ' + LTRIM( STR( RecsApnd )) + ;
	             CHR(13) + ' Percent Completed: ' +;
	             LTRIM( STR( nBytesRead/nFileSize 100 )) NOWAIT
	        ENDFOR
	        RecsApnd = RecsApnd + 1
	                                
	                        
	     ENDDO
	     =FCLOSE( nFileHandle )
	     WAIT WINDOW ' Records Appended: ' + LTRIM( STR( RecsApnd )) + ;
	                        
	                              
	       CHR(13) + ' Percent Completed: ' + ;
	       LTRIM( STR( nBytesRead/nFileSize 100)) NOWAIT
	                                             
	     RETURN
	                        
	     FUNCTION ReadField
	     PARAMETER cFieldDelim, cChrFldDelim
	     cAccumText = ""
	     lFldDelimFlag = .F.
	     DO WHILE !lFldDelimFlag AND !FEOF( nFileHandle )
	        cSingle = FREAD( nFileHandle, 1 )
	        nBytesRead = nBytesRead + 1
	        IF cSingle = cFieldDelim OR cSingle = CHR(13) OR ;
	           IIF( lChrFldDelimFlag, cSingle = cChrFldDelim, .F. )
	                              
	           IF cSingle = CHR(13)
	              cSingle = FREAD( nFileHandle, 1 )
	              nBytesRead = nBytesRead + 1
	              IF cSingle = CHR(10)
	                 cSingle = FREAD( nFileHandle, 1 )
	                 nBytesRead = nBytesRead + 1
	                 IF !(cSingle = CHR(26) OR ASC(cSingle) = 0)
	                    =FSEEK( nFileHandle, -1, 1 )
	                    nBytesRead = nBytesRead - 1
	                 ENDIF
	              ELSE
	                 IF !(cSingle = CHR(26) OR ASC(cSingle) = 0)
	                   =FSEEK( nFileHandle, -1, 1 )
	                   nBytesRead = nBytesRead - 1
	                 ENDIF
	              ENDIF
	              lFldDelimFlag = .T.
	           ENDIF
	           IF cSingle = cFieldDelim
	              lFldDelimFlag = .T.
	           ENDIF
	           cSingle = ""
	        ELSE
	           cAccumText = cAccumText + cSingle
	        ENDIF
	                                              
	     ENDDO
	     RETURN cAccumText
	                          
	     PROCEDURE ErrHand
	     PARAMETERS nError, cFileName
	     DO CASE
	     CASE nError = 2
	                                                   
	        cReason = "File not found: " + cFileName
	                                                      
	     CASE nError = 4
	                                                    
	        cReason = "Unable to open ' + cFileName + '. Too many files open"
	                        
	     CASE nError = 5
	                                                    
	        cReason = "File access denied: " + cFileName
	                                                      
	     CASE nError = 6
	                                                    
	        cReason = "Error: Invalid file handle given"
	                                                      
	     CASE nError = 8
	                                                    
	        cReason = "Error: Out of memory"
	                                                      
	     CASE nError = 25
	                        
	        cReason = "Seek error (can't seek before start of file)"
	                                                     
	     CASE nError = 29
	                        
	        cReason = "Error: Disk is full"
	                                                      
	     CASE nError = 31
	                                                    
	        cReason = "Error opening file: " + cFileName
	                                                      
	     ENDCASE
	     ?? CHR(7)
	     WAIT WINDOW cReason
	     RETURN
	                                              
	      EOF Appendm.prg
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbcode kbvfp kbvfp600 
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro250bMac kbFoxPro260aMac kbFoxPro250cMac kbFoxPro250DOS kbFoxPro250aDOS kbFoxPro250bDOS kbFoxPro260DOS kbFoxPro260aDOS kbFoxPro260 kbFoxPro250 kbFoxPro250a kbFoxPro250b kbFoxPro260a kbVFP300 kbVFP600
	Version           : MACINTOSH:2.5b,2.5c,2.6a; MS-DOS:2.5,2.5a,2.5b,2.6,2.6a; WINDOWS:2.5,2.5a,2.5b,2.6,2.6a,3.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
