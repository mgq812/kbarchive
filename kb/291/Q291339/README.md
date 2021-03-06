---
layout: page
title: "Q291339: SMS: Administrator Console/Services Can't Connect to SQL Server"
permalink: /kb/291/Q291339/
---

## Q291339: SMS: Administrator Console/Services Can't Connect to SQL Server

{% raw %}

	Article: Q291339
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): kbsms200
	Last Modified: 06-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In Systems Management Server (SMS) 2.0 sites in which both the site server and
	the server that is running Microsoft SQL Server are located on the same
	computer, the SMS Administrator console and the SMS services and threads may not
	connect to the SQL database under certain conditions.
	
	The following entry may be logged in the Smsprov.log file:
	
	  E:\OPALSP2\Sdk_provider\Nt\Smsprov\SspObjectQuery.cpp(4233) : SQL Connection
	  attempt timed out
	  SQL Error: Unable to connect: SQL Server is unavailable or does not exist.
	  General network error. Check your documentation.
	
	The following entry may be logged in an SMS Executive service thread such as
	Hman.log:
	
	  ~Cannot connect to the site source on the database, sleep 10 minutes..
	
	Other programs may not have SQL connectivity issues. For example, you may be able
	to successfully connect with and run queries from the SQL Server Query Analyzer,
	even from the SMS database. You may not notice any errors or warnings in the SQL
	error log files.
	
	CAUSE
	=====
	
	This issue may occur if you configured the LocalServer open database
	connectivity (ODBC) data source name (DSN) entry for SQL Server to use a network
	library other than the Named Pipes network library.
	
	
	WORKAROUND
	==========
	
	To work around this issue:
	
	1. Start the ODBC Data Source Administrator tool from Control Panel.
	
	2. Click the System DSN tab, and then double click LocalServer.
	
	3. Click Next.
	
	4. Click Client Configuration.
	
	5. Click Named Pipes in the Network Libraries section.
	
	6. Click OK.
	
	7. Make sure that "With Windows NT authentication using the network login ID" is
	  selected.
	
	8. Click Next, and then click Finish.
	
	MORE INFORMATION
	================
	
	This issue has been reproduced using SQL 7.0 and SQL 2000 that is installed as
	the database for SMS 2.0 Service Pack 2 (SP2) and Service Pack 3 (SP3) sites.
	
	If a program or a user creates either a user or a system DSN that uses the SQL
	Server driver, if the newly created DSN uses a network library other than the
	Named Pipes library, all of the DSNs that use the SQL Server driver are
	reconfigured to use the other network library.
	
	
	Additional query words: prodsms ODBC DSN
	
	======================================================================
	Keywords          : kbsms200 
	Technology        : kbSMSSearch kbSMS200
	Version           : :2.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
