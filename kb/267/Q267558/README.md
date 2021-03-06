---
layout: page
title: "Q267558: SMS: CAPs &amp; DPs Generate Critical Errors on Novell Servers"
permalink: /kb/267/Q267558/
---

## Q267558: SMS: CAPs &amp; DPs Generate Critical Errors on Novell Servers

{% raw %}

	Article: Q267558
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0
	Operating System(s): 
	Keyword(s): kbsms200 kbCAP kbNDS kbOSNovell
	Last Modified: 21-JUL-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In a mixed Microsoft Windows NT and Netware environment, it is possible for
	Client Access Points (CAPs) and Distribution Points (DPs) running on Netware
	servers to generate critical error messages while the NT CAPs and DPs continue
	to function properly.
	
	MORE INFORMATION
	================
	
	When a Systems Management Server site server runs in such a mixed environment
	two different security systems come into effect - Windows NT and Netware.
	
	In order for site systems (CAPs and DPs) to function properly on Netware servers
	and for the site server to be able to contact them, an account with proper
	Netware permissions must be created and added to Netware.
	
	If you notice Netware site systems generating critical errors, verify whether it
	is a security problem by looking in the Inbox Manager log (Inboxmgr.log) if
	enabled on the site server.
	
	The following log example contains the errors that may be recorded:
	
	Note: In order to view the NAL errors, you will first need to enable NAL logging
	on the site server as documented in the following article:
	
	  Q241001 SMS: Troubleshooting Server, Component, and Hierarchy Issues
	
	Inboxmgr.log:
	
	  NAL[1] - ERROR: failed to make a network connection through the NDS provider.  Access is denied.	
	  SMS_INBOX_MANAGER 
	  NAL[4] - Attempting to release current connection.
	  SMS_INBOX_MANAGER	 
	  NAL[4] - A connection has not yet been made.
	  SMS_INBOX_MANAGER	 
	  NAL[2] - WARNING: Connect() failed.  Access is denied.
	  SMS_INBOX_MANAGER 
	  NAL[2] - WARNING: _TryUser() failed.  Access is denied.
	  SMS_INBOX_MANAGER 
	  NAL[4] - Recoverable error: Access is denied.
	  SMS_INBOX_MANAGER	 
	  NAL[2] - WARNING: TryEachInList() failed.  Unspecified error
	  SMS_INBOX_MANAGER 
	  NAL[4] - Recoverable error: Unspecified error
	  SMS_INBOX_MANAGER	 
	  NAL[4] - Attempting access under the context of the current process ...
	  SMS_INBOX_MANAGER 
	  NAL[4] - Attempting to connect using the Access interface.
	  SMS_INBOX_MANAGER 
	  NAL[4] - Applying default account (user name and password are both null).
	  SMS_INBOX_MANAGER 
	  NAL[4] - Attempting to gain access through NAL provider NWNDS.
	  SMS_INBOX_MANAGER 
	  NAL[4] - CNWNDSTree::GetAccess, server components are not allowed access using the default user/password.  	
	  SMS_INBOX_MANAGER 
	  NAL[2] - WARNING: Connect() failed.  Access is denied. 
	  SMS_INBOX_MANAGER	 
	  NAL[2] - WARNING: _TryUser() failed.  Access is denied.
	  SMS_INBOX_MANAGER
	  NAL[4] - Recoverable error: Access is denied. 
	
	To recover from this state you need to create an administrator's account on the
	Novell server, and grant it proper rights to the CAP and Distribution Point
	folders.
	
	For the proper permissions required on these folder, refer to the white paper at
	this location:
	
	  Integrating Microsoft Systems Management Server 2.0 With Novell NetWare
	
	Once that account is created you need to configure the Systems Management Server
	(SMS) Site Server:
	
	1. Within the SMS Administrator Console, navigate to:
	
	  Site Settings\Connection accounts\Site system
	
	2. Right-click Site System, and then choose New - Netware account. Add the tree
	  and user name that were previously created.
	
	Once this is done you can monitor the Inbox Manager log again. You should see the
	following log entries:
	
	 	
	  NAL[4] - GetPath returns path: \\MYNDSTREE\.MYVOLS_VOL1.QUALITY.CHARLOTTE\ 
	  SMS_INBOX_MANAGER
	  NAL[4] - Try() is attempting to access \\MYNDSTREE\.MYVOLS_VOL1.QUALITY.CHARLOTTE\CAP_GS1\ 
	  SMS_INBOX_MANAGER
	  NAL[4] - Try() succeeded. 
	  SMS_INBOX_MANAGER
	  NAL[4] - _TryUser() succeeded. 
	  SMS_INBOX_MANAGER 
	  NAL[4] - TryEachInList() succeeded. 
	  SMS_INBOX_MANAGER
	
	  Established connection to ["Display=\\MYNDSTREE\.MYVOLS_VOL1.QUALITY.CHARLOTTE"]NWNDS:["SMS_SITE=GS1"]\\MYNDSTREE\.MYVOLS_VOL1.QUALITY.CHARLOTTE\CAP_GS1\ 
	
	REFERENCES
	==========
	
	To learn more about SMS and Netware please refer to the white paper at the
	following location:
	
	  Integrating Microsoft Systems Management Server 2.0 With Novell NetWare
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200 kbCAP kbNDS kbOSNovell 
	Technology        : kbSMSSearch kbSMS200
	Version           : winnt:2.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
