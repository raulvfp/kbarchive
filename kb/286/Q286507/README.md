---
layout: page
title: "Q286507: XGEN: CDO Returns Substring Search Instead of Prefix"
permalink: /kb/286/Q286507/
---

## Q286507: XGEN: CDO Returns Substring Search Instead of Prefix

{% raw %}

	Article: Q286507
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): exc55 kbExchange550preSP5fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you use Collaboration Data Objects (CDO) message filter objects to generate
	a result set, if you filter by one of the nine documented message properties in
	the following rule, an incorrect result record set may be returned. The results
	should be returned by using the following documented rule from the Microsoft
	Developer Network (MSDN):
	
	  For fields of data type other than String, the MAPI search restriction type
	  is RES_PROPERTY with relational operator RELOP_EQ. For fields of data type
	  String, the restriction type is RES_CONTENT with fuzzy level options
	  FL_SUBSTRING, FL_IGNORECASE, and FL_LOOSE. However, the following MAPI
	  properties are compared using FL_PREFIX instead of FL_SUBSTRING:
	
	- PR_ACCOUNT
	
	- PR_BUSINESS_ADDRESS_CITY
	
	- PR_COMPANY_NAME
	
	- PR_DEPARTMENT_NAME
	
	- PR_DISPLAY_NAME
	
	- PR_GIVEN_NAME
	
	- PR_OFFICE_LOCATION
	
	- PR_SURNAME
	
	- PR_TITLE
	
	However, the result set is comprised of a SUBSTRING search rather than the
	PREFIX, for example:
	
	  FilterFields.Add CdoPR_SURNAME, "M"
	
	This builds a filter with all of the last names that contain the letter "M",
	rather than those that begin with the letter "M".
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft Exchange Server 5.5 service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: Collaboration Data Objects (OLEMSG, CDO)
	
	+-------------------------+
	| File name | Version     | 
	+-------------------------+
	| Cdo.dll   | 5.5.2654.45 | 
	+-------------------------+
	
	NOTE: Because of file dependencies, Exchange Server version 5.5 Service Pack 4
	must be applied before you apply this fix.
	
	
	
	For additional information on how to download the update for this problem, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q289606 XGEN: Exchange Server 5.5 Post-Service Pack 4 Collaboration Data
	  Objects Fixes Available
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5.
	
	MORE INFORMATION
	================
	
	For more information about message filter collections in CDO, please refer to
	the following MSDN Web site:
	
	  http://msdn.microsoft.com/library/psdk/cdo/_olemsg_messagefilter_object.htm
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55 kbExchange550preSP5fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
