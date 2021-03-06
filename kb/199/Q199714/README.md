---
layout: page
title: "Q199714: Cannot Join Domain Because of SMB Signing"
permalink: /kb/199/Q199714/
---

## Q199714: Cannot Join Domain Because of SMB Signing

{% raw %}

	Article: Q199714
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	The following error message is displayed when you attempt to add a computer
	running Windows NT to the domain:
	
	  Unable to connect to the domain controller for this domain. Either
	  the username or password entered is incorrect.
	
	The error message is displayed even though networking is enabled and the correct
	administrator name and password credentials were supplied.
	
	CAUSE
	=====
	
	SMB Signing has been enabled and set to required. SMB is also known as the
	Common Internet File System (CIFS) file sharing protocol.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	There are two different ways of resolving this problem:
	
	Option 1:
	
	Temporarily disable SMB Signing on the PDC.
	
	NOTE: This option is required to get a backup domain controller (BDC)
	successfully added to the domain.
	
	1. Run Registry Editor (Regedt32.exe).
	
	2. From the HKEY_LOCAL_MACHINE subtree, go to the following key:
	
	  System\CurrentControlSet\Services\LanManServer\Parameters
	
	3. Set the following value to 0:
	
	  Name: RequireSecuritySignature
	  Type: REG_DWORD
	  Value: 0 (disable), 1 (enable)
	
	  NOTE: The default is 0 (disable)
	
	4. Click OK and then quit Registry Editor.
	
	5. Shut down and restart Windows NT.
	
	Option 2:
	
	Temporarily join a workgroup, and then enable SMB Signing on the member server or
	workstation prior to joining the domain.
	
	NOTE: Windows NT Workstation Service Pack 3 or later has SMB Signing enabled by
	default. Windows NT Server has SMB Signing disabled by default.
	
	To re-enable SMB Signing on a computer running Windows NT Workstation 4.0 Service
	Pack 3 or later:
	
	1. Run Registry Editor (Regedt32.exe).
	
	2. From the HKEY_LOCAL_MACHINE subtree, go to the following key:
	
	  \System\CurrentControlSet\Services\Rdr\Parameters
	
	3. Click Add Value on the Edit menu.
	
	4. Modify the following value:
	
	  Value Name: EnableSecuritySignature
	  Data Type: REG_DWORD
	  Data: 1
	
	  NOTE: The default is 1 (enable)
	
	5. Click OK and then quit Registry Editor.
	
	6. Shut down and restart Windows NT.
	
	To enable SMB Signing on a computer running Windows NT Server Service Pack 3 or
	later:
	
	1. Run Registry Editor (Regedt32.exe).
	
	2. From the HKEY_LOCAL_MACHINE subtree, go to the following key:
	
	  System\CurrentControlSet\Services\LanManServer\Parameters
	
	3. Set the following value to 1:
	
	  Name: EnableSecuritySignature
	  Type: REG_DWORD
	  Value: 1
	
	  NOTE: The default is 0 (disable)
	
	4. Click OK and then quit Registry Editor.
	
	5. Shut down and restart Windows NT.
	
	MORE INFORMATION
	================
	
	For more information on SMB Signing, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q161372 How to Enable SMB Signing in Windows NT
	
	Additional query words: SMB Signing password incorrect
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
