---
layout: page
title: "Q156105: XCLN: Viewing Other Attendees after Accepting Meeting Request"
permalink: /kb/156/Q156105/
---

## Q156105: XCLN: Viewing Other Attendees after Accepting Meeting Request

{% raw %}

	Article: Q156105
	Product(s): Microsoft Schedule+ for Windows
	Version(s): WINDOWS:7.0; Win95:7.0
	Operating System(s): 
	Keyword(s): kbfaq
	Last Modified: 21-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Schedule+ for Windows, version 7.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If you have already accepted a Microsoft Schedule+ Meeting Request, you cannot
	view other Attendees by using the Attendees tab when viewing the meeting
	details. Only the Originator of a Meeting Request can see the attendees using
	this tab.
	
	
	WORKAROUND
	==========
	
	There are two workarounds for this problem.
	
	The first workaround is for the originator of the Meeting Request to give READ
	access privileges on their schedule to everyone who is invited to the meeting.
	This can also be done by setting the Default access privilege to READ privileges
	or higher. The attendees would then log into the originator's schedule to view
	the meeting. They should open the File menu, click Open, click Other's
	Appointment Book, and enter the originator's alias. This will display the
	originator's appointment book details. The attendee can then locate the
	appointment, double-click on it to display the appointment dialog box, and
	select the Attendee's tab to view who will be or will not be attending.
	
	Note: This will create additional network traffic. Also, this cannot be set per
	meeting. This is set for the entire schedule.
	
	The second workaround is for the attendee to keep the original Meeting Request
	message. Although this will not show who will actually be attending, it will
	show the original list of people invited to attend the meeting. This won't work
	for anyone who automatically accepts meeting requests because the message is
	automatically deleted by the system. It might also be an incomplete list if the
	originator invites other people in another message.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in version 7.0 of Microsoft
	Schedule+. We are researching this problem and will post new information here in
	the Microsoft Knowledge Base as it becomes available.
	
	Additional query words:
	
	======================================================================
	Keywords          :  kbfaq
	Technology        : kbOfficeSearch kbSQLServ700 kbScheduleSearch kbOffice95Search kbZNotKeyword3
	Version           : WINDOWS:7.0; Win95:7.0
	
	=============================================================================
	

{% endraw %}
