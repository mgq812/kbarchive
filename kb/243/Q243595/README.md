---
layout: page
title: "Q243595: XADM: Resetting Default &amp; Anonymous Permissions on Public Folder"
permalink: /kb/243/Q243595/
---

## Q243595: XADM: Resetting Default &amp; Anonymous Permissions on Public Folder

{% raw %}

	Article: Q243595
	Product(s): Microsoft Exchange
	Version(s): 4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): exc4 exc5 exc55
	Last Modified: 13-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article explains how to restore missing Default and Anonymous accounts that
	are normally assigned to an Exchange Server public folder. By default, the
	default accounts have assigned to them "Author" level permissions, and the
	anonymous accounts have assigned to them "None" level permissions.
	
	MORE INFORMATION
	================
	
	An Exchange Administrator or owner of a public folder may intentionally or
	unintentionally remove the Default or Anonymous accounts of an Exchange Server
	public folder. When this is done, these accounts do not appear in the list of
	permissions for the public folder. This may also cause unintended access
	problems for some users. It is preferable to set the access level for these
	default accounts to None rather than delete them altogether.
	
	Only an Exchange Server Administrator or a user with Owner permissions to the
	public folder may restore these default names to the Permissions tab so they may
	be configured with the appropriate settings. If an administrator or owner of the
	public folder simply accesses the Permissions tab of the folder, the default
	accounts will be re-displayed with their default values of None. Once the user
	selects OK on the Properties dialog box, the names will be restored to the
	public folder. The following steps show how to restore these default accounts in
	either the Microsoft Outlook client or the Microsoft Exchange Server
	Administrator program.
	
	Restoring Permissions Using Outlook
	-----------------------------------
	
	NOTE: You must be an Owner of the folder to perform these steps.
	
	1. In Outlook, find the public folder in the public folder hierarchy,
	  right-click the public folder, and then click Properties.
	
	2. Click the Permissions tab. Note that the Default and Anonymous roles are
	  displayed and are set to None.
	
	3. Modify the permissions as necessary, and then click OK.
	
	Restoring Permissions Using the Exchange Server Administrator Program
	---------------------------------------------------------------------
	
	1. In the Exchange Server Administrator program, click the public folder, and
	  then click Properties on the File menu.
	
	2. On the General tab, click Client Permissions. Note that the Default and
	  Anonymous roles are displayed and are set to None.
	
	3. Modify the permissions as necessary, and then click OK.
	
	Additional query words:
	
	======================================================================
	Keywords          : exc4 exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : :4.0,5.0,5.5
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
