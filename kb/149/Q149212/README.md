---
layout: page
title: "Q149212: XCLN: How to Configure Public Folder Favorites for Users"
permalink: /kb/149/Q149212/
---

## Q149212: XCLN: How to Configure Public Folder Favorites for Users

{% raw %}

	Article: Q149212
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:4.0,5.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 24-MAR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Windows 95/98 client, versions 4.0, 5.0 
	- Microsoft Exchange Windows 3.x client, versions 4.0, 5.0 
	- Microsoft Exchange Windows NT client, versions 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Many Microsoft Exchange Administrators would like to automatically configure
	certain Public Folder Favorites for all their users. This functionality is not
	available in Microsoft Exchange version 4.0.
	
	MORE INFORMATION
	================
	
	To make it easier for users to add public folders to their favorites list, the
	administrator can send email to the users with the set of public folder
	shortcuts in the message. This message could also include directions on how to
	add these shortcuts to the list of favorites. For example, the instructions to
	the user might read:
	
	Use the following steps to add the attached public folders to your list of
	favorites. Follow these steps for each shortcut in this email message:
	
	1. Double-click the shortcut in the mail message to open the folder.
	
	2. On the File menu, click Add to Favorites.
	
	Steps the Administrator Needs to Perform
	----------------------------------------
	
	1. Create shortcuts for all the public folders that need to be added to the
	  user's favorites. To create a shortcut to a public folder:
	
	  a. From the Microsoft Exchange client (Windows 3.x, Windows NT, or Windows
	     95), select (highlight) the public folder.
	
	  b. On the File menu, click Create Shortcut. This brings up the Create
	     Shortcut dialog box.
	
	  c. Enter the name that you want the shortcut to have, and click OK. This
	     creates a shortcut file.
	
	2. Create a new mail message addressed to all the users that are to receive the
	  shortcuts. Attach all the shortcut files created in step 1.
	
	3. Send the message.
	
	Steps the User Needs to Perform
	-------------------------------
	
	After receiving the message with the attached shortcuts, the user needs to follow
	these steps:
	
	1. From the Microsoft Exchange client (Windows 3.x, Windows NT, or Windows 95),
	  open the message that contains the attached shortcuts.
	
	2. For each shortcut in the message, perform the following steps:
	
	  a. Double-click the shortcut. This brings up another client window with the
	     public folder open. If the client does not have permissions to that public
	     folder, an error message will appear.
	
	  b. On the File menu, click Add to Favorites. This adds the currently open
	     public folder to the user's public folder favorites.
	
	  c. Close the current window by double-clicking the icon in the top-left
	     corner of the window.
	
	Additional query words: faq
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbExchange400 kbExchangeClientSearch kbZNotKeyword kbZNotKeyword2 kbZNotKeyword3 kbExchange400NT kbExchange500NT kbExchange400Win95 kbExchange500Win95
	Version           : WINDOWS:4.0,5.0
	
	=============================================================================
	

{% endraw %}
