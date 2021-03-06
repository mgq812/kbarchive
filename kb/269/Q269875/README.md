---
layout: page
title: "Q269875: SVCACLS.EXE Is Not Included With The Windows 2000 Resource Kits"
permalink: /kb/269/Q269875/
---

## Q269875: SVCACLS.EXE Is Not Included With The Windows 2000 Resource Kits

{% raw %}

	Article: Q269875
	Product(s): Microsoft Press
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdocfix kbdocerr
	Last Modified: 09-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- MSPRESS Microsoft Windows 2000 Server Resource Kit ISBN 1-57231-805-8 
	- MSPRESS Microsoft Windows 2000 Professional Resource Kit ISBN 1-57231-808-2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following documentation on the Service ACL Editor (SVCACLS.EXE) is included
	in the Windows 2000 Resource Kit Tools Help file. However, the SVCACLS.exe file
	is not included on the Microsoft Windows 2000 Resource Kits' CD-ROM.
	
	  Svcacls.exe: Service ACL Editor
	
	  This command-line tool sets access control lists (ACLs) on service objects,
	  enabling administrators to delegate control of services.
	
	  To initially use Service ACL Editor, you must have Administrator privileges,
	  although someone with Administrator privileges can use the tool to grant
	  someone without Administrator privileges permission to use the tool. Delete,
	  Read Control, and Write discretionary access control are required to modify
	  discretionary access control lists (DACLs) for services. The DACL (usually
	  referred to simply as ACL) determines the permissions on an object. To change
	  a DACL, a permission called WRITE_DAC is required.
	
	  Service ACL Editor runs only on x86-based computers running Windows 2000 or
	  Windows NT version 4.0.
	
	  Caution
	  Do not remove permissions on any service for Administrators or System. If you
	  do, you might have to reinstall Windows 2000 to regain control over the
	  service.
	
	  Service ACL Editor Topics
	  Service ACL Editor Syntax
	  Service ACL Editor Examples
	
	  File Required
	
	  Svcacls.exe
	
	MORE INFORMATION
	================
	
	The Svcacls.exe utility was pulled from the Resource Kit CD-ROM at the last
	minute. Unfortunately the documentation for this utility was inadvertently left
	behind.
	
	This utility was pulled because the same functionality is available in the
	SUBINACL tool. Additional information on the SUBINACL tool is available in the
	Resource Kit Tools Help file.
	
	Additional query words: RKBook Reskit Win2k Win2kPro Win2000
	
	======================================================================
	Keywords          : kbdocfix kbdocerr 
	Technology        : kbMSPressSearch
	Version           : :
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
