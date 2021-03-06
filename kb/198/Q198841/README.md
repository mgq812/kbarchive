---
layout: page
title: "Q198841: XFOR: Store Notification for CALCON May Stop"
permalink: /kb/198/Q198841/
---

## Q198841: XFOR: Store Notification for CALCON May Stop

{% raw %}

	Article: Q198841
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5 SP2,5.5 SP3
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5 SP2, 5.5 SP3 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	
	SYMPTOMS
	========
	
	The Microsoft Exchange Calendar Connector relies on store notifications for
	processing MAPI-based queries from Exchange clients. In certain cases, this
	notification mechanism may stop, and require a restart of the Calendar
	Connector.
	
	CAUSE
	=====
	
	There is a problem with the store's push notification mechanism. In a heavy
	stress environment, this problem becomes more apparent. This problem occurs more
	often on high-powered Alpha-based servers than on Intel servers.
	
	WORKAROUND
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	To work around this problem, add a key to the registry. To do this, follow these
	steps:
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate the following key in the registry:
	
	  HKLM\SYSTEM\CurrentControlSet\Services\MSExchangeIS\ParametersSystem
	
	  NOTE: The above registry key is one path; it has been wrapped for readability.
	
	3. On the Edit menu, click Add Value, and then add the following registry value:
	
	  Value Name: Notification Timeout
	  Data Type:  REG_DWORD
	  Value:      1
	
	4. Quit Registry Editor.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5.
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbZNotKeyword2 kbExchange550SP2 kbExchange550SP3
	Version           : winnt:5.5 SP2,5.5 SP3
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
