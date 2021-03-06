---
layout: page
title: "Q115907: INF: ODBC Stored Procedures odbc#userid######## on SQL Server"
permalink: /kb/115/Q115907/
---

## Q115907: INF: ODBC Stored Procedures odbc#userid######## on SQL Server

{% raw %}

	Article: Q115907
	Product(s): Open Database Connectivity (ODBC)
	Version(s): WINDOWS:1.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 27-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Open Database Connectivity, version 1.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When an ODBC enabled application uses prepared execution to execute an SQL query
	on SQL Server and the user has permission to create stored procedures, the ODBC
	SQL Server driver creates a stored procedure with a name like
	"odbc#userid########" (for example, odbc#sa2147024896) on SQL Server and
	executes that stored procedure.
	
	The stored procedure is created in response to a SQLPrepare ODBC call and is
	executed when SQLExecute is called. Normally, when the connection is closed, the
	driver drops these stored procedures. Also, if the user does not have Create
	Proc permissions, the stored procedures are not created and SQL statements are
	executed directly.
	
	However, under certain situations when a connection might be terminated without
	closing the connection, the driver is not able to delete the stored procedures.
	This can happen if the client process terminates abnormally and is a more common
	occurrence in a development environment.
	
	This article describes how to remove these stored procedures from the SQL Server.
	
	MORE INFORMATION
	================
	
	To remove these stored procedures, follow these steps. Make sure no ODBC client
	is connected to the server when the following steps are carried out.
	
	1. Run the following script, with actual database name in the USE command, using
	  ISQL.EXE or any other SQL Server client tool and save the output so generated
	  in a file called DROP.SQL:
	
	        USE  <database_name>
	        go
	        SELECT CHAR(13) + CHAR(10)+ "DROP PROCEDURE " + NAME +
	               CHAR(13) + CHAR(10) + "go" +
	               CHAR(13) + CHAR(10)
	        FROM sysobjects
	        WHERE name LIKE "ODBC%"
	        go
	
	2. Modify the DROP.SQL script so generated to include a USE
	  <database_name> followed by a go at the top of the file. Remove any
	  "-------" lines generated by the tool to separate the header and the results.
	  Delete any "(X row(s) affected)" line if generated in the output by the tool.
	  Then, the DROP.SQL script file should look something like:
	
	        USE <database_name>
	        go
	
	        drop procedure odbc#sa1855970
	        go
	
	        drop procedure odbc#sa1232424
	        go
	
	        ...
	
	3. Run the DROP.SQL as the input script using a SQL client tool. For example,
	  using ISQL.EXE:
	
	  isql -S<server> -Usa -P<password> -idrop.sql
	
	  and verify that no errors were reported.
	
	  NOTE: If permission to create stored procedures is revoked from the users, the
	  SQL Server driver will not create these stored procedures. This can be used
	  as a workaround if it is desired that no stored procedures be created by the
	  driver.
	
	
	Additional query words: 1.01.2807 VB Visual Basic Access Excel Fox MSVC
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbODBCSearch kbODBC100
	Version           : WINDOWS:1.0
	
	=============================================================================
	

{% endraw %}
