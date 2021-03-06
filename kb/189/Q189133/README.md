---
layout: page
title: "Q189133: HOWTO: Make C DLL More Accessible to VB with a Type Library"
permalink: /kb/189/Q189133/
---

## Q189133: HOWTO: Make C DLL More Accessible to VB with a Type Library

{% raw %}

	Article: Q189133
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0,97
	Operating System(s): 
	Keyword(s): 
	Last Modified: 18-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Since its first release, Visual Basic has provided the Declare statement as a
	means for you to take advantage of DLL functions written in other languages,
	such as C. But Declare statements are less than perfect and often require you to
	know as much about the DLL as you do about Visual Basic code. A type library
	creates a more Visual Basic-friendly way of calling exported C functions.
	
	This article demonstrates how to create a type library when you build your DLL,
	and how to reference that library from Visual Basic.
	
	MORE INFORMATION
	================
	
	Type libraries are compound document files (.tlb files) used in Automation. They
	contain important information about the types, objects, modules, and interfaces
	exposed by an Automation server to its clients. Fortunately, a server doesn't
	need to be Automation-aware to take advantage of a type library. In fact, most C
	DLLs are not Automation servers. All that is required is that the C DLL declare
	its functions as members of a module in a type library. An Automation client,
	such as Visual Basic, can read this information and bind to it as it would any
	object. No need for Declare statements or hard to remember constants because
	Visual Basic does all the work.
	
	There are several advantages in creating a type library for your DLL. The most
	important of these is better type safety. But you also get the advantage of
	better performance, because Visual Basic automatically binds to your functions
	using early-binding. In contrast, all Declare statements are late-bound.
	Furthermore, you gain greater control over the way your DLL is presented to
	Visual Basic programmers. The type library allows you to provide Visual
	Basic-friendly names for functions and parameters, along with helpful extras
	like enumerations and User Defined Types (UDTs).
	
	Currently, type libraries are created using scripts written in either the
	Interface Definition Language (IDL) or the Object Description Language (ODL).
	These scripts are then compiled using MkTypLib.EXE or MIDL.EXE that come with
	Visual Studio. Visual C++ takes some of the work out of creating type libraries,
	because any ODL files that you associate with your DLL project will
	automatically be compiled with MIDL when you compile your project.
	
	Step-by-Step Example - Create the DLL and Type Library
	------------------------------------------------------
	
	1. Open Visual C++ 5.0 and select File|New. On the Projects tab, select "Win32
	  Dynamic-Link Library" and name the project "TLBSamp."
	
	2. Select File|New again. On the Files tab, select "C++ Source File," name the
	  file "TLBSamp.c," and press OK.
	
	3. Repeat step 2 again, and this time choose "Text File" as the file type. Name
	  the files "TLBSamp.def" and "TLBSamp.odl" respectively.
	
	4. Next, add the following code to TLBSamp.c:
	
	        #include <windows.h>
	
	        // MyDll_ReverseString -- Reverses the characters of a given string
	        void __stdcall MyDll_ReverseString(LPSTR lpString)
	        {
	           _strrev(lpString);
	        }
	
	        // MyDLL_Rotate -- Returns bit rotation of 32-bit integer value
	        int __stdcall MyDll_Rotate(int nVal, int nDirect, short iNumBits)
	        {
	           int nRet = 0;
	
	           if((iNumBits < 1) || (iNumBits > 31))
	              return nRet;
	
	           switch(nDirect)
	           {
	           case 0:
	              // Rotate nVal left by iNumBits
	              nRet = (((nVal) << (iNumBits)) |
	                      ((nVal) >> (32-(iNumBits))));
	              break;
	           case 1:
	              // Rotate nVal right by iNumBits
	              nRet = (((nVal) >> (iNumBits)) |
	                      ((nVal) << (32-(iNumBits))));
	              break;
	           }
	
	           return nRet;
	        }
	
	5. To make the functions exportable, add the following to TLBSamp.def:
	
	        LIBRARY TLBSamp
	        DESCRIPTION 'Microsoft KB Sample DLL'
	        EXPORTS
	          MyDll_ReverseString
	          MyDll_Rotate
	
	6. Declare your functions in a type library by adding the following to
	  TLBSamp.odl:
	
	        // This is the type library for TLBSamp.dll
	        [
	        // Use GUIDGEN.EXE to create the UUID that uniquely identifies
	        // this library on the user's system. NOTE: This must be done!!
	           uuid(F1B9E420-F306-11d1-996A-92FF02C40D32),
	        // This helpstring defines how the library will appear in the
	        // References dialog of VB.
	           helpstring("KB Sample: Make your C DLL More Accessible"),
	        // Assume standard English locale.
	           lcid(0x0409),
	        // Assign a version number to keep track of changes.
	           version(1.0)
	        ]
	        library TLBSample
	        {
	
	        // Define an Enumeration to use in one of our functions.
	        typedef enum tagRotateDirection
	        {
	           tlbRotateLeft=0,
	           tlbRotateRight=1
	        }RotateDirection;
	
	        // Now define the module that will "declare" your C functions.
	        [
	           helpstring("Sample functions exported by TLibSamp.dll"),
	           version(1.0),
	        // Give the name of your DLL here.
	           dllname("TLBSamp.dll")
	        ]
	        module MyDllFunctions
	        {
	
	           [
	           // Add a description for your function that the developer can
	           // read in the VB Object Browser.
	              helpstring("Returns the reverse of a given string."),
	           // Specify the actual DLL entry point for the function. Notice
	           // the entry field is like the Alias keyword in a VB Declare
	           // statement -- it allows you to specify a more friendly name
	           // for your exported functions.
	              entry("MyDll_ReverseString")
	           ]
	           // The [in], [out], and [in, out] keywords tell the Automation
	           // client which direction parameters need to be passed. Some
	           // calls can be optimized if a function only needs a parameter
	           // to be passed one-way.
	           void __stdcall ReverseString([in, out] LPSTR sMyString);
	
	           [
	              helpstring("Rotates a Long value in the given direction."),
	              entry("MyDll_Rotate")
	           ]
	           // Besides specifying more friendly names, you can specify a more
	           // friendly type for a parameter. Notice the Direction parameter
	           // has been declared with our enumeration. This gives the VB
	           // developer easy access to our constant values.
	           int __stdcall BitRotate([in] int Value,
	                                   [in] RotateDirection Direction,
	                                   [in] short Bits);
	
	        } // End of Module
	        }; // End of Library
	
	7. Compile your DLL and type library by choosing "Rebuild All" from the Build
	  menu. When complete, copy the new DLL (TLBSamp.dll) to your Visual Basic
	  directory for testing.
	
	NOTE: As a matter of convenience, you may wish to include your type library in
	your DLL as a resource. This would free you from having to distribute a separate
	TLB file to your Visual Basic developers.
	
	To add the library as a resource, complete the following steps:
	
	1. Select File|New. On the Files tab, select "Text File," name the file
	  "TLBSamp.rc," and press OK.
	
	2. In the text window that appears add the following line:
	
	  1 typelib TLBSamp.tlb
	
	3. Save the file and recompile your DLL. When complete, copy the new DLL
	  (TLBSamp.dll) to your Visual Basic directory for testing; overwrite the
	  previous file if prompted.
	
	Step-by-Step Example - The Visual Basic Test App
	------------------------------------------------
	
	1. To test your DLL and type library, open Visual Basic 5.0 and create a new
	  standard Project. Form1 is created by default.
	
	2. From the Project menu, select References to call up the References dialog
	  box, and then click Browse to find your new type library (or your DLL if you
	  added the library as a resource). Once you have located it, press OK. Visual
	  Basic will automatically register the library for you the first time you
	  reference it. Make sure that your library ("KB Sample: Make your C DLL More
	  Accessible") has been checked in the references List, and then close the
	  dialog box.
	
	3. Press the F2 key to bring up the Object Browser. Note that your library
	  (TLBSamp) has been added to the Visual Basic project, and that your functions
	  can now be called just as if they were native Visual Basic functions. Visual
	  Basic will even drop down your enumeration list when the developer is typing
	  in the Direction parameter to the BitRotate function.
	
	4. Add a CommandButton to Form1 and add the following code the button's click
	  event:
	
	        Private Sub Command1_Click()
	           Dim n1 As Long, n2 As Long, nTmp As Long
	           Dim sTest As String, sMsg As String
	
	           sTest = "Hello World!"
	           n1 = 100
	
	           ReverseString sTest
	             sMsg = sTest & " | "
	           ReverseString sTest
	             sMsg = sMsg & sTest & vbCrLf
	
	           nTmp = BitRotate(n1, tlbRotateLeft, 2)
	           n2 = BitRotate(nTmp, tlbRotateRight, 2)
	             sMsg = sMsg & Str$(n1) & " : " & Str$(nTmp) & " : " & Str$(n2)
	
	           MsgBox sMsg
	        End Sub
	
	5. Now press the F5 key to run the vb5allB project in the IDE.
	
	  NOTE: If you receive an error message, it may be because Visual Basic cannot
	  find your DLL. Make sure you have copied it to the Visual Basic directory or
	  your system path before you run your test app.
	
	REFERENCES
	==========
	
	For additional information on the structure of ODL or IDL, please see the
	following articles in the Microsoft Developer Network (MSDN) Library:
	
	  TITLE : Type Libraries and the Object Description Language
	  TITLE : Interface Definitions and Type Libraries
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q143258 : How to Create Constants and DLL Declarations in a Type Library
	
	  Q122285 : HOWTO: Add Type Libraries as Resources to .dll and .exe Files
	
	  Q142840 : Visual Basic Requirements for Exported DLL Functions
	
	(c) Microsoft Corporation 1998, All Rights Reserved. Contributions by Richard R.
	Taylor, Microsoft Corporation
	
	
	Additional query words: kbDSupport kbCodeSam kbVBp kbVBp500 kbVC kbVC500 kbVBp600
	
	======================================================================
	Keywords          :  
	Technology        : kbVCsearch kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600 kbVC500 kbVC32bitSearch kbVC500Search
	Version           : WINDOWS:5.0,97
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
