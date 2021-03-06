---
layout: page
title: "Q172382: WD97: No Results When Faxing by Using Outlook Distribution List"
permalink: /kb/172/Q172382/
---

## Q172382: WD97: No Results When Faxing by Using Outlook Distribution List

{% raw %}

	Article: Q172382
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): winword word97
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	- Microsoft Outlook 97 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you try to fax from Word 97 by using an Outlook distribution list, the
	process does not finish. When this happens, you receive no error messages.
	
	CAUSE
	=====
	
	On the File menu, you may be pointing to Send To, and then clicking Fax
	Recipient.
	
	WORKAROUND
	==========
	
	There are three methods you can use to work around this issue.
	
	Method 1: Choose Send To Mail Recipient
	---------------------------------------
	
	When you are ready to fax your document from Word, follow these steps:
	
	1. On the File menu, point to Send To, and then click Mail Recipient.
	
	2. In the Message dialog box, click the To button.
	
	3. In the Show Names From list box, click Personal Address Book.
	
	4. In the Personal Address Book, select the Distribution List to use for the
	  recipients of the fax.
	
	5. On the Message toolbar, click Send.
	
	The fax should then begin processing.
	
	Method 2: Choose Print To Microsoft Fax
	---------------------------------------
	
	1. On the File menu, click Print.
	
	2. In the printer Name list, click Microsoft Fax.
	
	3. Click OK.
	
	4. In the Compose New Fax dialog box, click Address Book.
	
	5. In the Show Names From list box, select Personal Address Book.
	
	6. In the Personal Address Book, select the Distribution List to use for the
	  recipients of the fax.
	
	7. Click OK.
	
	8. Continue through the wizard.
	
	Method 3: Fax from Outlook
	--------------------------
	
	Fax the Word document as an attachment to a fax sheet in Outlook by using the
	distribution list. To do so, follow these steps:
	
	1. Open Outlook.
	
	2. On the Compose menu, click New Fax.
	
	3. Click the Address Book button.
	
	4. In the Show Names From list box, click Personal Address Book.
	
	5. In the Personal Address Book, select the Distribution List to use for the
	  recipients of the fax.
	
	6. Click OK.
	
	7. Continue through the wizard.
	
	NOTE: On the Select Cover Page, leave the Subject field blank; otherwise, you may
	receive an error message. You can add information in the Notes section of the
	page. For additional information about this general error, please see the
	following articles in the Microsoft Knowledge Base:
	
	  Q168704 OL97 ErrMsg: General Error When Sending a Fax
	
	  Q140432 Problems Sending Fax from MAPI-Aware Programs
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article.
	
	MORE INFORMATION
	================
	
	To create a distribution list in Outlook, follow these steps:
	
	1. In Outlook, on the Tools menu, click Address Book.
	
	2. On the File menu, click New Entry.
	
	3. In the New Entry dialog box, under "Select the Entry Type", select Personal
	  Distribution List. In the "In The" list, under "Put This Entry", select
	  Personal Address Book, and then click OK.
	
	4. In the New Personal Distribution List Properties box, click Add/Remove
	  Members.
	
	5. Under "Show Names from the", select Contacts.
	
	6. Select the members you want, and click Members to add the names under the
	  "Personal Distribution List" column. After all names are added, click OK.
	
	7. Under "Name on the New Personal Distribution List Properties", type a name
	  for the distribution list, and then click OK.
	
	8. Close the Address Book.
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q160474 WD97: Fax Wizard Falsely Implies Completion of Faxing Process
	
	  Q169755 WD97: Troubleshooting Fax Problems from Word
	
	  Q171043 OL98: (CW) Microsoft Fax Does Not Process Dialing Properties
	
	
	Additional query words: 8.0 8.00 faxing fails cannot exchange
	
	======================================================================
	Keywords          : winword word97 
	Technology        : kbWordSearch kbOutlookSearch kbWord97 kbWord97Search kbZNotKeyword2 kbOutlook97Search kbZNotKeyword3
	Version           : WINDOWS:97
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
