---
layout: page
title: "Q258837: Services That Use Remote Connections Leak User Sessions"
permalink: /kb/258/Q258837/
---

## Q258837: Services That Use Remote Connections Leak User Sessions

{% raw %}

	Article: Q258837
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbWinNT400PreSP7Fix
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When you run multiple services that connect to the Server service on a remote
	computer (for example, by using named pipes or to access files) and the services
	are using a user account for the services, under certain circumstances user
	logons that are created by the services will be left open on the server. These
	sessions continue to contribute to the active session count on the server, and
	may cause the server to reach the limit of 10 authenticated connections on
	Microsoft Windows NT Workstation or the license limit on Microsoft Windows NT
	Server when you are running in Per-Server licensing mode.
	
	When this occurs, programs receive error code 71 or 1395 when they make a new
	connection to the server.
	
	CAUSE
	=====
	
	The Windows NT redirector does not log a user off when a service is stopped when
	the session is going idle. The redirector relies on the removal of the session
	by a scavenger routine. This routine does not disconnect if the session is
	reused in the meantime.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Apply it only to
	computers that are experiencing this specific problem. This fix may receive
	additional testing. Therefore, if you are not severely affected by this problem,
	Microsoft recommends that you wait for the next Windows NT 4.0 service pack that
	contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, visit the following Microsoft
	Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The typical support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date        Time    Version        Size     File name   Platform
	  ------------------------------------------------------------------
	  05/12/2000  05:29p  4.0.1381.7052  265,264  Rdr.sys     Intel
	  05/16/2000  04:55p  4.0.1381.7052   58,640  Wkssvc.dll  Intel
	
	
	
	To enable this fix, you must install the hotfix files and set a registry entry as
	follows:
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate the following key in the registry:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters
	
	3. On the Edit menu, click Add Value, and then add the following registry value:
	
	  Value Name: KeepConn
	  Data Type: REG_DWORD
	  Value: 0
	
	4. Quit Registry Editor.
	
	WORKAROUND
	==========
	
	You can disconnect the client computer sessions by using the net session /delete
	<computer_name> command. This disconnects all logons from that computer
	and closes all open files. Note that using this command can cause data loss if
	open files that have not been saved are closed.
	
	You can also use a program to use the NetSessionEnum and NetSessionDel functions
	to find and remove client sessions.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbWinNT400PreSP7Fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
