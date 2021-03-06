---
layout: page
title: "Q162218: Unable to Rename WinNT Root Dir After Upgrade to WinNT 4.0"
permalink: /kb/162/Q162218/
---

## Q162218: Unable to Rename WinNT Root Dir After Upgrade to WinNT 4.0

{% raw %}

	Article: Q162218
	Product(s): Microsoft Windows NT
	Version(s): 3.5 3.51 4.0
	Operating System(s): 
	Keyword(s): kbenv kbsetup
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Windows NT versions 3.5 and 3.51 are installed by default into the directory
	name WINNT35. After you upgrade these versions to Windows NT 4.0, the Windows NT
	system files still reside in the same directory name.
	
	CAUSE
	=====
	
	The Windows NT operating system and installed applications have settings that
	are dependent upon the existing Windows root directory name. These settings are
	extensive and may be found in the Windows NT registry and in configuration files
	such as *.ini and *.cfg files.
	
	WORKAROUND
	==========
	
	There is no practical method for renaming a WINNT35 directory name after
	installing Windows NT 4.0. The only workaround is to reinstall Windows NT 3.51
	using a generic directory name such as "WINNT," and then upgrade to Windows NT
	4.0.
	
	Additional query words: prodnt
	======================================================================
	Keywords          : kbenv kbsetup 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : 3.5 3.51 4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
