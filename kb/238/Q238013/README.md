---
layout: page
title: "Q238013: XADM: How to Disable a Mailbox in Exchange Server"
permalink: /kb/238/Q238013/
---

## Q238013: XADM: How to Disable a Mailbox in Exchange Server

{% raw %}

	Article: Q238013
	Product(s): Microsoft Exchange
	Version(s): winnt:5.0,5.5
	Operating System(s): 
	Keyword(s): exc5 exc55
	Last Modified: 22-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	If a user leaves a company, instead of removing that user's mailbox, you may
	want to keep it, but not allow other users to send mail to or receive mail from
	it.
	
	In Exchange Server version 5.5, you can use the Exchange Server Administrator
	program to view the properties of the mailbox, and on the Limits tab, change the
	settings so that the mailbox cannot send or receive mail.
	
	In Exchange Server version 5.0, the Exchange Server Administrator program only
	allows you to change the settings so that the mailbox cannot send mail; you
	cannot prohibit the mailbox from receiving, so other users can still send mail
	to it.
	
	MORE INFORMATION
	================
	
	To disable a mailbox in either Exchange Server 5.0 or 5.5:
	
	1. Use the Exchange Server Administrator program to open the mailbox properties.
	
	2. Click the Advanced tab, click Hide From Address Book, and then click Apply.
	
	3. Click the Limits tab, and in either the Prohibit Send box (in Exchange Server
	  5.0) or the Prohibit Send and Receive box (in Exchange Server 5.5), enter
	  either 0 or 1 kilobyte (KB).
	
	  NOTE: You can add a user to the Delivery Restrictions tab to reject messages
	  from certain users or accept messages from only certain users.
	
	4. Click Apply.
	
	5. Click the E-Mail Addresses tab, and then change the e-mail address for each
	  proxy type (for example, SMTP, X.400, Lotus cc:Mail, and Microsoft Mail) for
	  the user. Add additional characters to the user names, such as "XXX." For
	  example:
	
	  XXXsomeone@microsoft.com
	
	  NOTE: You can also perform a directory export to a .csv file, modify the
	  e-mail addresses in Microsoft Excel, and then perform a directory import to
	  overwrite the information.
	
	Additional query words: GAL remove hiding Recipient Delivery
	
	======================================================================
	Keywords          : exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbZNotKeyword2
	Version           : winnt:5.0,5.5
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
