---
layout: page
title: "Q297947: INFO: Use the IADsPropertyValue2 Interface to Return an IADsSecu"
permalink: /kb/297/Q297947/
---

## Q297947: INFO: Use the IADsPropertyValue2 Interface to Return an IADsSecu

{% raw %}

	Article: Q297947
	Product(s): Microsoft C Compiler
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbADSI kbVC600 kbDSupport w2000adsi w2000schema
	Last Modified: 09-APR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Editions, version 6.0, used with:
	   - Microsoft Windows 2000 
	- Microsoft Active Directory Services Interface, Microsoft Active Directory Client 
	- Microsoft Active Directory Services Interface, System Component 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes a method that you can use to manipulate the
	defaultSecurityDescriptor attribute of an Active Directory schema object by
	using the IADsSecurityDescriptor interface that is returned from an Active
	Directory Service Interfaces (ADSI) property cache that is using the
	IADsPropertyValue2 interface.
	
	MORE INFORMATION
	================
	
	Requirements
	------------
	
	This article assumes that you are familiar with the following topics:
	
	- Windows NT security model.
	- Security Identifier (SID) and Security Descriptor (SD).
	- Security Descriptor Definition Languuage (SDDL).
	- How to use the IADsSecurityDescriptor interface to modify a security
	  descriptor.
	
	This article does not address problems that can arise if you add improper
	access-control entries (ACEs) to an object's default security descriptor.
	
	NOTE: the default security descriptor is added to all objects of this class when
	they are created. Use caution when you create or modify an object's default
	security descriptor.
	
	For more information, refer to the MSDN online documentation before you attempt
	to use the sample code that is provided in this article.
	
	Background
	----------
	
	The defaultSecurityDescriptor attribute contains a security descriptor that is
	stored in its SDDL form. To modify this attribute, use one of the following
	methods:
	
	- Use the Win32 security APIs.
	
	- Use Visual C sample code to convert the SDDL SD into an
	  IADsSecurityDescriptor.
	
	  This article provides sample Visual C code that illustrates how to convert the
	  SDDL SD into an IADsSecurityDescriptor by using the Active Directory Service
	  Interfaces (ADSI) property cache IADsPropertyValue2 interface.
	
	Use the Win32 Security APIs
	---------------------------
	
	1. Bind to the Schema object, and then retrieve the SDDL form of the SD.
	
	2. Add the appropriate ownership information to the SDDL string.
	
	  NOTE: for the ADSI property cache to successfully return an
	  IADsSecurityDescriptor interface, include the ownership and group ownership
	  information for the SD in the SDDL string. If the information is missing, you
	  must add it to the SDDL string.
	
	3. Use the ConvertStringSecurityDescriptorToSecurityDescriptor function to
	  obtain a binary SD.
	
	4. Place the binary SD into a VARIANT.
	
	5. Place the VARIANT copy of the SD into the ADSI property cache as an octet
	  string type (array of bytes).
	
	6. Request an NT Security Descriptor type from the ADSI property cache (the
	  cache returns an IDispatch interface).
	
	7. Use the QueryInterface method of the IDispatch interface to obtain an
	  IADsSecurityDescriptor interface.
	
	8. Use the properties and methods of the IADsSecurityDescriptor interface to
	  modify the security descriptor.
	
	9. Place the IDispatch interface for the SD back into the ADSI property cache.
	
	10. Request the octet string form of the SD from the ADSI property cache.
	
	11. Convert the binary SD back into its SDDL form by using the
	  ConvertSecurityDescriptorToStringSecurityDescriptor.
	
	12. Convert the SDDL string into a binary string (BSTR).
	
	13. Place the BSTR into a VARIANT, and then replace the BSTR back onto the
	  Schema object.
	
	Use Visual C Sample Code
	------------------------
	
	NOTE: This sample code requires the Include and the Library files from the
	Platform SDK. The Include and Library files that are released with Visual Studio
	do not contain the IADsPropertyValue2 interface.
	
	1. Start Visual Studio.
	
	2. Create a new Win32 Console Application, and then click OK.
	
	3. On the "Win32 Console Application Step 1 of 1" page, click An Empty Project,
	  and then click Finish.
	
	4. In the "New Project Information" dialog box, click OK.
	
	5. On the File menu, click New, and then select C++ Source File.
	
	6. Name the file, and then click OK.
	
	7. Paste the code from this article into the file that you just created.
	
	8. On the Project menu, click Settings.
	
	9. On the Link tab, add Adsiid.lib and Activeds.lib to the Object/Library
	  Modules edit control, and then click OK.
	
	10. Compile, link, and then run the project.
	
	Sample Visual C Code
	--------------------
	
	  #define _WIN32_WINNT 0x0500
	  #define UNICODE
	  #define _UNICODE
	
	  #include <wchar.h>
	  #include <stdio.h>
	  #include <atlbase.h>
	  #include <objbase.h>
	  #include <activeds.h>
	  #include <winnt.h>
	  #include <sddl.h>
	  #include <string.h>
	
	  HRESULT BytesToVariantArray(PBYTE pValue, //Pointer to bytes to put in a variant array.
	                              ULONG cValueElements,//Size of pValue in bytes.
	                              VARIANT *pVariant //Return variant that contains octet string (VT_UI1|VT_ARRAY).
	                              );
	
	  int main()
	  {
	     HRESULT hr = E_FAIL;
	     PSECURITY_DESCRIPTOR pSD = NULL;
	     IADsSecurityDescriptor *pSecurityDescriptor = NULL;
	     ULONG ulSDLen = 0;
	     IADsPropertyValue *pVal;
	     IADsPropertyValue2 *pVal2;
	     SECURITY_INFORMATION dwSecInfo=0;
	     VARIANT var, varBSTR;
	     BSTR bstrOwner = NULL;
	     long lSDType = ADSTYPE_NT_SECURITY_DESCRIPTOR;
	     SAFEARRAY *pArrayVal = NULL;
	     CComPtr <IADs> pRootDSE;
	     LPTSTR lpszSDBuffer;
	     ULONG cbszSDBuffer = 0;  
	     CoInitialize(NULL); 
	     // 
	     // Find the Schema naming context.
	     // 
	     hr = ADsGetObject(L"LDAP://RootDSE", IID_IADs,(void **) &pRootDSE);
	     if( !SUCCEEDED(hr) )
	     {
	        printf("Could not bind to RootDSE. Received error %08X\n",hr);
	        return 0;
	     }
	     CComBSTR bSchemaPath;
	     VARIANT varData;
	     VariantInit( &varData );
	     pRootDSE->Get(L"schemaNamingContext", &varData);
	     // 
	     // Build a path to the user schema object.
	     // 
	     bSchemaPath = L"LDAP://cn=user,";
	     bSchemaPath.AppendBSTR( varData.bstrVal);
	     // 
	     // Bind to the Schema object to retrieve the default Security Descriptor.
	     // 
	     CComPtr <IADs> pSchemaObj;
	     hr = ADsGetObject(bSchemaPath.m_str,IID_IADs,(void **)&pSchemaObj);
	     if( !SUCCEEDED(hr) )
	     {
	        printf("Unable to open the schema object error %08X\n",hr);
	        return 0;
	     }
	     VariantClear( &varData );
	     pSchemaObj->Get(L"defaultSecurityDescriptor", &varData);
	     printf("The default security descriptor on the schema object is\n%S\n",varData.bstrVal);
	     // 
	     // Convert the string representation (SDDL) of the security descriptor
	     // into a SECURITY_DESCRIPTOR structure.
	     // 
	     // 
	     // Check to see whether the ownership information is on the string that is located in  
	     // the first few characters; search for O: and G: to see whether this information 
	     // is in the SDDL form. If it is not, prefix the information to the string
	     // so that the IADsPropertyValue2 interface can properly convert the 
	     // raw security descriptor into an IADsSecurityDescriptor interface.
	     // 
	     // Set a flag with the appropriate constants to use when the SDDL
	     // string is rebuilt after you display it.
	     // 
	     // Prefix some ownership details.
	     // 
	     CComBSTR bSDDLPre = varData.bstrVal;
	     if( wcsstr(varData.bstrVal, L"O:") )
	     {
	        // 
	        // Owner Info is present. Set the bits into
	        // the SECURITY_INFORMATION structure.
	        // 
	        // Use dwSecInfo to retrieve only those parts
	        // of the security descriptor that were present in its SDDL form.
	        // For the IADsPropertyValue2 interface to return
	        // an IADsSecurityDescriptor interface, add the ownership information
	        // if it is missing (see the previous comment).
	        // 
	        dwSecInfo = dwSecInfo | OWNER_SECURITY_INFORMATION;
	     }
	     else
	     {
	        // 
	        // Ownership information is missing. Add it to the 
	        // the SDDL form of the SD and make the owner default to 
	        // the Domain Administrator.
	        // 
	        CComBSTR bTemp = "O:DA";
	        bTemp.AppendBSTR ( bSDDLPre );
	        bSDDLPre =  bTemp;
	     }
	     // 
	     // Check for Group Ownership information.
	     // 
	     if( wcsstr( varData.bstrVal, L"G:") )
	     {
	        // 
	        // Group ownership information is present.
	        // Add this information to the SECURITY_INFORMATION
	        // structure to retrieve it after the operation is complete.
	        // 
	        dwSecInfo = dwSecInfo | GROUP_SECURITY_INFORMATION;
	     }
	     else
	     {
	        // 
	        // Add the Group ownership information to the
	        // SDDL SD. Add this information after the ownership SID ("O:") 
	        // and before the DACL information ("D:")
	        // This code assumes that the SDDL SD is set up with O: G: D:
	        // 
	        // Default the Group onwnership to the Domain Admins ( G:DA )
	        // 
	        //*******************************
	        // IMPORTANT NOTE:
	        // 
	        // This code assumes that the DACL information is present. If this information is missing,
	        // the code fails.
	        //********************************
	        DWORD len;
	        wchar_t *wsDacl;
	        wchar_t *pSDDL = new wchar_t[bSDDLPre.Length() + 1];
	        wcscpy( pSDDL, bSDDLPre.m_str);
	        // 
	        // Find the start of the DACL string, and then copy all of the code up to that
	        // point into a temporary location.
	        // 
	        wsDacl = wcsstr( pSDDL,L"D:");
	        len = (wsDacl - pSDDL); 
	        wchar_t *pCPY = new wchar_t[ len + 1 ];
	        wcsncpy( pCPY, pSDDL, len );
	        pCPY[len] = (wchar_t) NULL;
	        // 
	        // Build the temporary binary string (BSTR), and then copy it into SDDL variable.
	        // 
	        CComBSTR bTemp = pCPY;
	        bTemp.Append("G:DA");
	        bTemp.Append( wsDacl );
	        delete pCPY;
	        delete pSDDL;
	        bSDDLPre = bTemp;
	     }
	     // 
	     // Check for DACL information.
	     // 
	     if( wcsstr( varData.bstrVal, L"D:") )
	     {
	        // 
	        // DACL information is present.
	        // 
	        dwSecInfo = dwSecInfo | DACL_SECURITY_INFORMATION;
	     }
	     // 
	     // Check for SACL information.
	     // 
	     if( wcsstr( varData.bstrVal, L"S:" ) )
	     {
	        // 
	        // SACL information is present.
	        // 
	        dwSecInfo = dwSecInfo | SACL_SECURITY_INFORMATION;
	     }
	     // 
	     // The SDDL string is built; convert it to a binary SID.
	     // 
	     if ( ! ConvertStringSecurityDescriptorToSecurityDescriptor(
	                                 bSDDLPre.m_str,
	                                 SDDL_REVISION_1, 
	                                 &pSD, 
	                                 &ulSDLen ))
	     {
	        wprintf(L"Error converting string security descriptor: %d\n", GetLastError() );
	        return 0;
	     }
	     // 
	     // Check to see whether there is a valid binary
	     // security descriptor.
	     // 
	     if( IsValidSecurityDescriptor( pSD ) )
	        printf("Binary Security Descriptor is valid....\n\n");
	     else 
	        printf("Binary Security Descriptor is not valid....\n\n");
	     // 
	     // Initialize a VARIANT and place the SECURITY_DESCRIPTOR structure
	     // in as a Byte array.
	     // 
	     VariantInit(&var);
	     hr= BytesToVariantArray( (PBYTE) pSD, //Pointer to bytes to put in a variant array.
	                              ulSDLen,     //Size of pValue in bytes.
	                              &var         //Return variant that contains the octet string (VT_UI1|VT_ARRAY).
	                            ); 
	     // 
	     //  IADsPropertyValue is a CoClass; use this to get the 
	     //  desired IADsPropertyValue2 interface for the conversion.
	     // 
	     hr = CoCreateInstance(CLSID_PropertyValue,
	                           NULL,
	                           CLSCTX_INPROC_SERVER,
	                           IID_IADsPropertyValue,
	                           (void**)&pVal);
	     //   
	     // QI for a IADsPropertyValue2 interface.
	     // 
	     hr = pVal->QueryInterface(IID_IADsPropertyValue2,(void**)&pVal2);
	     // 
	     // Put the VARIANT array into cache as an octet string.
	     // 
	     hr = pVal2->PutObjectProperty(ADSTYPE_OCTET_STRING, var);//ADSTYPE_NT_SECURITY_DESCRIPTOR 
	     if (!SUCCEEDED(hr) )
	     {
	        wprintf(L"Error putting security descriptor into cache: %d\n",GetLastError() );
	        goto Cleanup;
	     }
	        wprintf(L"Put modified security descriptor into cache\n\n");
	
	     // 
	     // Release the variant (this is very important for memory management).
	     // 
	     VariantClear(&var); 
	     // 
	     // Retrieve the VARIANT array from cache as an IADsSecurityDescriptor.
	     // 
	     hr = pVal2->GetObjectProperty(&lSDType, &var);
	     if (!SUCCEEDED(hr) )
	     {
	        wprintf(L"Error getting the IADsSecurityDescriptor from cache: %d\n", GetLastError() );
	        goto Cleanup;
	     }
	        wprintf(L"Read the IADsSecurityDescriptor from cache\n\n");
	
	     // 
	     // QI the IDispatch for an IADsSecurityDescriptor interface.
	     // 
	     hr = V_DISPATCH( &var )->QueryInterface(IID_IADsSecurityDescriptor,(void**)&pSecurityDescriptor);
	     if ( FAILED(hr) ) {
	        wprintf(L"QI for IADsSecurityDescriptor failed: 0x%x\n", hr);
	        goto Cleanup;
	     }
	     // 
	     // To verify, retrieve the owner of the Security Descriptor through the 
	     // IADsSecurityDescriptor::get_Owner method.
	     // 
	     // At this point, the user can modify the Descretionary ACl by using the
	     // IADsAccessControlList and IADsAccessControlEntry interfaces.
	     // 
	     // This also applies to the SACL.
	     // 
	     hr = pSecurityDescriptor->get_Owner(&bstrOwner);
	     if ( FAILED(hr) ) {
	        wprintf(L"Retrieve IADsSecurityDescriptor owner failed: 0x%x\n", hr);
	        goto Cleanup;
	     }
	     wprintf(L"The owner for this security Descriptor is %s\n",bstrOwner);
	     // 
	     // Convert the IADsSecurityDescriptor back into a variant that contains the Raw SD.
	     // 
	     hr = pVal2->PutObjectProperty(ADSTYPE_NT_SECURITY_DESCRIPTOR ,var );
	     if( !SUCCEEDED(hr))
	     {
	        wprintf(L"Error returning IADsSecurityDescriptor to the cache: %d\n", GetLastError());
	        goto Cleanup;
	     }
	        wprintf(L"Returned IADsSecurityDescriptor to the cache\n\n");
	
	     // 
	     // Retrieve it as an octet string.
	     // 
	     lSDType = ADSTYPE_OCTET_STRING;
	     hr = pVal2->GetObjectProperty( &lSDType, &var );
	     if ( FAILED(hr) ) {
	        wprintf(L"Retrieve IADsSecurityDescriptor as Octet String failed: 0x%x\n", hr);
	        goto Cleanup;
	     }
	        wprintf(L"Retrieved IADsSecurityDescriptor as Octet String from cache\n\n");
	
	     // 
	     // Convert it back to its SDDL form based on the dwSecInfo variable
	     // set when the SDDL was parsed earlier.
	     // 
	     SAFEARRAY *pAr;
	     pAr = var.parray;
	     SafeArrayAccessData( pAr, (void HUGEP **)&pSD);
	     if( ! ConvertSecurityDescriptorToStringSecurityDescriptor(
	        pSD,  // SD
	        SDDL_REVISION_1,          // revision level
	        dwSecInfo,            // components
	        &lpszSDBuffer,         // security descriptor string
	        &cbszSDBuffer        // size of security descriptor string
	        ) )
	     {
	        printf("Error converting it back to a string descriptor: %d\n",GetLastError());
	        return 0;
	     }
	     else
	        printf("This is the converted string descriptor(SDDL):\n%S\n\n", lpszSDBuffer);
	     // 
	     // Convert the octet string into a raw SD pointer by dereferencing the array of bytes.
	     // 
	     // This section of code illustrates how to create a variant that contains a BSTR so
	     // that the property can be written back to the AD object.
	     // 
	     varBSTR.bstrVal = SysAllocString(lpszSDBuffer );
	     LocalFree( (HLOCAL)lpszSDBuffer);
	     wprintf(L"-------------------------------------------------------------------------------\n");
	     wprintf(L"The NEW default security descriptor on the schema object is: %s\n\n", varBSTR.bstrVal);
	     V_VT(&varBSTR) = VT_BSTR;
	     
	  Cleanup:
	     pRootDSE.Release();
	     pSchemaObj.Release();
	     if (pVal)
	        pVal->Release();
	     if (pVal2)
	        pVal2->Release();
	     if(pSecurityDescriptor)
	        pSecurityDescriptor->Release();
	     VariantClear(&varBSTR);
	     
	     CoUninitialize();
	     return 0;
	  }
	
	  // 
	  // This function is located in the Platform SDK documentation.
	  // 
	  HRESULT BytesToVariantArray(
	  							PBYTE pValue, //Pointer to bytes to put in a variant array.
	  							ULONG cValueElements,//Size of pValue in bytes.
	  							VARIANT *pVariant //Return variant that contains the octet string (VT_UI1|VT_ARRAY).
	  							)
	  {
	      HRESULT hr = E_FAIL;
	      SAFEARRAY *pArrayVal = NULL;
	      SAFEARRAYBOUND arrayBound;
	      CHAR HUGEP *pArray = NULL;
	  	
	      //Set bound for array
	      arrayBound.lLbound = 0;
	      arrayBound.cElements = cValueElements;
	  	
	      //Create the safe array for the octet string. Unsigned char elements;single dimension;aBound size.
	      pArrayVal = SafeArrayCreate( VT_UI1, 1, &arrayBound );
	  	
	      if (!(pArrayVal == NULL) )
	      {
	          hr = SafeArrayAccessData(pArrayVal, (void HUGEP * FAR *) &pArray );
	          if (SUCCEEDED(hr))
	          {
	              //Copy the bytes to the safe array.
	              memcpy( pArray, pValue, arrayBound.cElements );
	              SafeArrayUnaccessData( pArrayVal );
	              //Set type to array of unsigned char
	              V_VT(pVariant) = VT_ARRAY | VT_UI1;
	              //Assign the safe array to the array member.
	              V_ARRAY(pVariant) = pArrayVal;
	              hr = S_OK;
	          }
	          else
	          {
	              //Clean up if the array cannot be accessed.
	              if ( pArrayVal )
	  				SafeArrayDestroy( pArrayVal );
	          }
	      }
	      else
	      {
	  		hr = E_OUTOFMEMORY;
	      }
	  	
	      return hr;}
	
	REFERENCES
	==========
	
	For additional information, click the article numbers below to view the articles
	in the Microsoft Knowledge Base:
	
	  Q269175 HOWTO: Use Visual C++ to Properly Order ACEs in an ACL
	
	  Q255126 PRB: ADSI Err '-2147016694(8007200a)' and '-2147023591(80070519)
	
	To download the Platform SDK, click the following link:
	
	  Platform SDK Update
	  http://www.microsoft.com/msdownload/platformsdk/sdkupdate/
	  (http://www.microsoft.com/msdownload/platformsdk/sdkupdate/)
	
	  When you are prompted, click No for more information, or click Yes to download
	  immediately.
	
	Additional query words: adsi
	
	======================================================================
	Keywords          : kbADSI kbVC600 kbDSupport w2000adsi w2000schema 
	Technology        : kbVCsearch kbAudDeveloper kbVC32bitSearch
	Version           : :6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
