---
layout: page
title: "Q288952: XADM:  Error 2186 When Starting the Information Store Service"
permalink: /kb/288/Q288952/
---

## Q288952: XADM:  Error 2186 When Starting the Information Store Service

{% raw %}

	Article: Q288952
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): kberrmsg kbfile
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you start the Microsoft Exchange Information Store service in Control
	Panel, you may receive the following error message:
	
	  Could not start the Microsoft Exchange Information Store service on
	  \\<Computername>.
	  Error 2186: The service is not responding to the control function
	
	In addition, the following event ID messages are logged in the Application event
	log:
	
	  Event ID: 1121
	  MSExchangeIS
	  Type: Error
	  Description:
	  Error 0xfb5 connecting to the Microsoft Exchange Server Directory Service
	
	  -and-
	
	  Event ID: 5000
	  MSExchangeIS
	  Type: Error
	  Description:
	  Unable to initialize connecting to the Microsoft Exchange Information Store
	  Service Error 0xfb5
	
	  -and-
	
	  Event ID: 1005
	  MSExchangeSA
	  Type: Error
	  Description:
	  Unexpected error -0xc0040000 - Network problems are preventing connection to
	  the Microsoft Exchange Server computer. Microsoft Exchange Server Information
	  Store ID no: 80040115-0514-000006bf occurred.
	
	The following event ID messages are logged in the System event log:
	
	  Event ID: 7009
	  Source: Service Control Manager
	  category: None
	  Description:
	  Timeout (120000 milliseconds) waiting for service to connect
	
	  -and-
	
	  Event ID: 7000
	  Source: Service Control Manager
	  Category: None
	  Description:
	  The Microsoft Exchange Information Store service failed to start due to the
	  following error: The service did not respond to the start or control request
	  in a timely fashion.
	
	CAUSE
	=====
	
	This issue can occur if the Information Store service has been configured to log
	on as a system account or to use the Local System account.
	
	RESOLUTION
	==========
	
	To resolve this issue:
	
	1. Open Control Panel, double-click Services, click "Microsoft Exchange
	  Information Store service", and then click Startup.
	
	2. In the Log On As box, click This Account, and then enter the name of the
	  Exchange Service Account or an account that has Service Account administrator
	  rights on the Organization, Site, and Configuration containers.
	
	3. Retype the password and password confirmation.
	
	4. Start the Information Store service.
	
	Additional query words: exch2kp2w
	
	======================================================================
	Keywords          : kberrmsg kbfile 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
