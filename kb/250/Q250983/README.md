---
layout: page
title: "Q250983: Using Netscape Server Push Technology with ASP"
permalink: /kb/250/Q250983/
---

## Q250983: Using Netscape Server Push Technology with ASP

{% raw %}

	Article: Q250983
	Product(s): Internet Information Server
	Version(s): WINDOWS:5; winnt:4.0,5.0
	Operating System(s): 
	Keyword(s): kbOSWin2000
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	- Microsoft Internet Explorer (Programming) version 5 
	- Microsoft Internet Information Server version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Netscape Web browser implements a proprietary technology known as Server
	Push to send a type of dynamic page updates to a client. This technology is not
	supported by Microsoft Internet Explorer. However, you can use Server Push with
	Microsoft Active Server Pages (ASP), or you can Client Pull as an optional
	method of displaying dynamic page updates in Internet Explorer.
	
	MORE INFORMATION
	================
	
	Microsoft provides programming examples for illustration only, without warranty
	either expressed or implied, including, but not limited to, the implied
	warranties of merchantability and/or fitness for a particular purpose. This
	article assumes that you are familiar with the programming language being
	demonstrated and the tools used to create and debug procedures. Microsoft
	support professionals can help explain the functionality of a particular
	procedure, but they will not modify these examples to provide added
	functionality or construct procedures to meet your specific needs. If you have
	limited programming experience, you may want to contact a Microsoft Certified
	Partner or the Microsoft fee-based consulting line at (800) 936-5200. For more
	information about Microsoft Certified Partners, please visit the following
	Microsoft Web site:
	
	  http://www.microsoft.com/partner/referral/
	
	For more information about the support options that are available and about how
	to contact Microsoft, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	Server Push Using ASP:
	
	To implement Server Push using ASP, do the following:
	
	1. Save the following code as Push.asp in a folder with at least Script access
	  defined:
	
	  <% @Language="VBScript" %>
	  <%
	    Option Explicit
	    Dim strBoundary
	
	    ' change the following string to whatever boundary you wish to use
	    strBoundary = "MSBOB"
	
	    ' turn off buffering
	    Response.Buffer = False
	
	    ' set the content type as a multipart document
	    Response.ContentType = "multipart/x-mixed-replace;boundary=" & strBoundary
	
	    ' create a function to output the boundary
	    Sub WriteBoundary()
	      Response.Write "--" & strBoundary & vbCrLf
	      Response.Write "Content-Type: text/html" & vbCrLf & vbCrLf
	    End Sub
	
	    ' this is a very unelegant sleep function just to create a short delay
	    Sub Sleep(tmpSeconds)
	      Dim dtmOne,dtmTwo
	      dtmOne = Now()
	      While DateDiff("s",dtmOne,dtmTwo) < tmpSeconds
	        dtmTwo = Now()
	      Wend
	    End Sub
	  %>
	  <% WriteBoundary %>
	  <html>
	  <body>
	  <p>First Page</p>
	  </body>
	  </html>
	  <%
	    Sleep 10
	    WriteBoundary
	  %>
	  <html>
	  <body>
	  <p>Second Page</p>
	  </body>
	  </html>
	  <%
	    Sleep 10
	    WriteBoundary
	  %>
	  <html>
	  <body>
	  <p>Third Page</p>
	  </body>
	  </html>
	
	2. Browse to the page using the Netscape Web browser. The following behavior
	  should occur:
	
	   - The first page displays for 10 seconds, and the browser indicates that it
	     is still loading a document.
	
	   - The second page displays for 10 seconds, and the browser continues to
	     indicate that it is still loading a document.
	
	   - The third page displays, and the browser indicates that the document
	     loading has completed.
	
	For more information on Server Push, Client Pull, and Microsoft's Internet
	products, please see the following articles:
	
	  Q159650 - Server Push Animation Not Supported in Internet Explorer
	
	  Q194083 - FP98: How to Use Client Pull in FrontPage Web Documents
	
	  Q196471 - FP2000: How to Use Client Pull in FrontPage Web Documents
	
	  Q240774 - How to Enable Client Pull for Web Servers, Sites, and Folders
	
	  An Exploration Of Dynamic Documents
	
	The third-party contact information included in this article is provided to help
	you find the technical support you need. This contact information is subject to
	change without notice. Microsoft in no way guarantees the accuracy of this
	third-party contact information.
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbOSWin2000 
	Technology        : kbiisSearch kbIEsearch kbAudDeveloper kbSDKIESearch kbiis500 kbiis400 kbZNotKeyword kbSDKIE500
	Version           : WINDOWS:5; winnt:4.0,5.0
	Issue type        : kbhowto
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
