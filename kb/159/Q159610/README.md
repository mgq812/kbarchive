---
layout: page
title: "Q159610: SMS: Access Violation Occurs with Pollinv.exe"
permalink: /kb/159/Q159610/
---

## Q159610: SMS: Access Violation Occurs with Pollinv.exe

{% raw %}

	Article: Q159610
	Product(s): Microsoft Systems Management Server
	Version(s): 1.2
	Operating System(s): 
	Keyword(s): kbsmsUtil smsutil
	Last Modified: 31-JUL-2001
	
	1.00 1.20
	WINDOWS
	kbenv kbbug1.20
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If a computer listed in the Invcolcl.txt file cannot be located on the network
	by the Systems Management Server Windows NT Inventory File Collector Service,
	Pollinv.exe, the following will occur:
	
	- The service will appear to stop responding when trying to locate that
	  computer. It will not log anything further in the Invcolcl.log log file.
	
	- If the service is then restarted manually, or comes to the beginning of its
	  next watchdog cycle (the default is 24 hours), then an access violation (AV)
	  error will occur.
	
	WORKAROUND
	==========
	
	To work around this problem, remove the nonexistent computer from the list of
	computers to poll in the Invcolcl.txt file.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 1.2, the Systems Management Server Resource Kit 1.2, and the Backoffice
	Resource Kit version 1.0. We are researching this problem and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	
	Additional query words: prodsms reskit 1.00 bork SMS_NT_INVENTORY_FILE_COLLECTOR inv32cli invwin32 climonnt
	
	======================================================================
	Keywords          : kbsmsUtil smsutil 
	Technology        : kbSMSSearch kbSMS120
	Version           : :1.2
	
	=============================================================================
	

{% endraw %}
