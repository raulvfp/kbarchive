---
layout: page
title: "Q271284: HOWTO: Access COM+ Object Constructor String in VB Component"
permalink: kb/271/Q271284/
---

## Q271284: HOWTO: Access COM+ Object Constructor String in VB Component

	Article: Q271284
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 2.0,2.1,2.1 SP1,2.1 SP2,2.5,2.6,5.0,6.0
	Operating System(s): 
	Keyword(s): kbCOMPlus kbOSWin2000 kbVBp500 kbVBp600 kbGrpDSVBDB kbMDACNoSweep kbATM
	Last Modified: 23-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In Microsoft Windows 2000, you can configure a unique object constructor string
	for each dynamic-link library (DLL) component that is installed in the COM+ run
	time. This constructor string is commonly used to specify an initialization
	string that must be accessible to all object instances of the component. This
	article includes a code sample that demonstrates how you can configure the COM+
	object constructor string for a Visual Basic component that the component's
	object instances can use.
	
	MORE INFORMATION
	================
	
	The constructor string is commonly used to specify a Database connection string
	that the object instances of a component use to establish database connections.
	An advantage of using the constructor string for this purpose is that it
	prevents the connection string from being hardcoded in the component's code. To
	change the name of the database server, point to a different database, or
	implement other modifications, you only have to modify the component's COM+
	object constructor; you no longer have to change the component's code and
	recompile the actual DLL. Besides storing database connection information, you
	can also use the COM+ object constructor string to specify any initialization
	string that needs to be accessible to all object instances of the component for
	which it is configured.
	
	How to Configure the COM+ Object Constructor String
	---------------------------------------------------
	
	The Visual Basic component should implement the IObjectConstruct COM+ interface
	to enable its object instances to access the COM+ object constructor string that
	has been configured for it. IObjectConstruct exposes a single method named
	Construct (IObjectConstruct_Construct) that fires when an object instance of the
	component is created. You can use the Constructor object that is passed as a
	parameter to this method to obtain the configured COM+ object constructor
	string. To implement a sample that demonstrates how you can this functionality,
	perform the following steps:
	
	1. Open a new ActiveX DLL project in Visual Basic.
	
	2. Rename the project "prjConstruct".
	
	3. Rename the class module "clsConstruct".
	
	4. Set project references to COM+ Services Library and ActiveX Data Objects 2.5
	  Library.
	
	5. Copy and paste the following code in the class module:
	
	  'General Declarations Section
	  Implements IObjectConstruct
	  Dim connstr As String
	
	  Private Sub IObjectConstruct_Construct(ByVal pCtorObj As Object)
	
	  Dim mConstructString As IObjectConstructString
	  Set mConstructString = pCtorObj
	  connstr = mConstructString.ConstructString
	
	  End Sub
	
	  Public Function GetAuthors() As ADODB.Recordset
	
	  Dim cn As ADODB.Connection
	  Dim rs As ADODB.Recordset
	
	  Set cn = New ADODB.Connection
	  cn.Open connstr
	
	  Set rs = New ADODB.Recordset
	  rs.CursorLocation = adUseClient
	  rs.Open "Select * from Authors", cn, adOpenStatic, adLockBatchOptimistic
	  Set rs.ActiveConnection = Nothing
	
	  Set GetAuthors = rs
	  GetObjectContext.SetComplete
	
	  End Function
	
	  This code sample demonstrates how to implement IObjectConstruct_Construct to
	  access the COM+ object constructor string. The Construct object parameter
	  must be cast to an IObjectConstructString interface. IObjectConstructString
	  exposes a single property called ConstructString that can be used to access
	  the COM+ object constructor string. Notice how the constructor string is
	  assigned to a global variable and reused in the GetAuthors function.
	
	6. Compile the DLL. To create the COM+ Server application to host the
	  prjConstruct.clsConstruct component, follow these steps:
	
	  a. In Control Panel, point to Administrative Tools, and then click Component
	     Services to open Component Services Microsoft Management Console (MMC)
	     snap-in.
	
	  b. Click to expand the Component Services, Computers, My Computer, and COM+
	     Applications nodes. Click COM+ Applications.
	
	  c. Right-click COM+ Applications, point to New, and then click Application.
	
	  d. Create an empty server-side application named VBComPlusTest, and set its
	     identity property to use the credentials of the Interactive user.
	
	  e. Complete the wizard, and click Finish. This creates the sample COM+
	     application that is used to host the prjConstruct.clsConstruct Visual
	     Basic component.
	
	7. To install the prjConstruct.clsConstruct component in the "VBComPlusTest"
	  COM+ application , follow these steps:
	
	  a. In the Component Services MMC snap-in, click to expand the VBComPlusTest
	     node. Click the Components subfolder.
	
	  b. Right-click Components, point to New, and then click Component.
	
	  c. In the COM Component Install Wizard, click Next, click "Install new
	     component(s)", and select prjConstruct.dll, and click Next.
	
	  d. Complete the wizard, and click Finish.
	
	8. Open the Properties window for the Visual Basic component
	  prjConstruct.clsConstruct.
	
	9. On the Activation tab, select the "Enable Object construction" check box.
	
	10. In the Constructor String box, specify the following ADO connection string,
	  and then click OK:
	
	  NOTE: This sample uses the Microsoft SQL Server PUBS sample database.
	
	  "Provider=SQLOLEDB;Data Source=<Your SQL Server>;Initial Catalog=pubs;" & _
	                     "User Id=<User Id>;Password=<Password>"
	
	How to Use the COM+ Object Constructor String
	---------------------------------------------
	
	1. Open a new Standard EXE project in Visual Basic to test the Visual Basic COM+
	  component. Form1 is created by default.
	
	2. Add a list box (List1) and a command button (Command1) to Form1.
	
	3. Copy and paste the following code in the Click event of Command1:
	
	  Dim obj As Object
	  Dim rs As Object
	
	  Set obj = CreateObject("prjConstruct.clsConstruct")
	  Set rs = obj.GetAuthors()
	  Do While Not rs.EOF
	    List1.AddItem rs.fields("au_fname")
	    rs.movenext
	  Loop
	
	  Set obj = Nothing
	
	4. Save the Standard EXE project, and run it.
	
	5. Click Command1 to populate the list box with the first names of all the
	  authors in the Authors table.
	
	To demonstrate the usefulness of the COM+ object constructor string, change the
	DataSource property in the constructor string to point to a different SQL Server
	that also has the PUBS sample database. When you run the client code, the
	records from the new data source are retrieved and displayed. To confirm this,
	add a new record to the Authors table in the second SQL Server PUBS database.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbCOMPlus kbOSWin2000 kbVBp500 kbVBp600 kbGrpDSVBDB kbMDACNoSweep kbATM 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600
	Version           : :2.0,2.1,2.1 SP1,2.1 SP2,2.5,2.6,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	