---
layout: page
title: "Q272492: POP3 and IMAP Clients Are Not Authenicated on Exchange Server"
permalink: /kb/272/Q272492/
---

## Q272492: POP3 and IMAP Clients Are Not Authenicated on Exchange Server

{% raw %}

	Article: Q272492
	Product(s): Microsoft Windows NT
	Version(s): 4.0,4.0 SP6a
	Operating System(s): 
	Keyword(s): kbWinNT400PreSP7Fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 4.0, 4.0 SP6a 
	- Microsoft Windows NT Server, Enterprise Edition versions 4.0, 4.0 SP6a 
	- Microsoft Windows NT Workstation versions 4.0, 4.0 SP6a 
	- Microsoft Exchange 2000 Server 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When the Exchange Server 2000 registry key
	HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\LSA has the
	LmCompatibilitylevel value set to 5, POP3 and IMAP clients are not
	authenticated.
	
	CAUSE
	=====
	
	This issue occurs because the 5 value does not allow a check for clear text
	passwords, and authentication therefore does not work properly.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem.
	
	To resolve this problem, contact Microsoft Product Support Services to obtain the
	fix. For a complete list of Microsoft Product Support Services phone numbers and
	information on support costs, please go to the following address on the World
	Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date         Time   Size     File name     Platform
	  ---------------------------------------------------
	  25-Sep-2000  21:07  247,056  Advapi32.dll  x86
	  25-Sep-2000  21:08   48,400  Msv1_0.dll    x86
	
	  25-Sep-2000  21:06  403,728  Advapi32.dll  Alpha
	  25-Sep-2000  21:06   79,632  Msv1_0.dll    Alpha
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0.
	
	Additional query words: 4.00
	
	======================================================================
	Keywords          : kbWinNT400PreSP7Fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400sp6 kbWinNTS400search kbWinNTS400 kbExchangeSearch kbExchange2000Search kbWinNTSEnt400SP6a kbWinNTW400SP6a kbExchange2000Serv
	Version           : :4.0,4.0 SP6a
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
