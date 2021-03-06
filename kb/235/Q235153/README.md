---
layout: page
title: "Q235153: Software Metering Client Agent Is Unable to Activate Retry Mode"
permalink: /kb/235/Q235153/
---

## Q235153: Software Metering Client Agent Is Unable to Activate Retry Mode

{% raw %}

	Article: Q235153
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): kbsetup kbClient kbConfig kbMMC kbServer kbsms200 kbsms200bug kbsmsAdmin kbsmsMeter
	Last Modified: 04-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When a Software Metering Client Agent is unable to contact a software metering
	server, the Software Metering Client Agent goes into the Retry mode. However,
	the attempted retry may not occur.
	
	CAUSE
	=====
	
	This behavior may occur because the default configuration settings prevent the
	retry from occurring. By default, the settings in the Configuration Polling
	Interval box and the Delay Before Retrying box are both set to 240 minutes.
	These settings disable the attempted connection retry as the polling interval is
	activated before the retry can occur.
	
	WORKAROUND
	==========
	
	To work around this behavior, the setting in the Delay Before Retrying box must
	be set to a value which is less than the setting in the Configuration Polling
	Interval box.
	
	NOTE: It is recommended that you configure the preceding settings before you
	install any clients.
	
	If these settings had not been configured before you enabled the Software
	Metering Client Agent, the new configuration settings cannot be updated until
	the next successful connection of the Software Metering Client Agent to the
	software metering server.
	
	An example of a configuration:
	
	Retries = 5
	Delay Before Retrying = 60
	Configuration Polling Interval = 240
	
	With the preceding configuration, the Software Metering Client Agent can make
	five attempts to connect to the software metering server every 60 minutes. The
	setting in the Configuration Polling Interval box ensures that a polling
	interval occurs every 240 minutes.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsetup kbClient kbConfig kbMMC kbServer kbsms200 kbsms200bug kbsmsAdmin kbsmsMeter 
	Technology        : kbSMSSearch kbSMS200
	Version           : :2.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
