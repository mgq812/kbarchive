---
layout: page
title: "Q103368: From Command Prompt: &quot;The Name Specified Is Not Recognized...&quot;"
permalink: /kb/103/Q103368/
---

## Q103368: From Command Prompt: &quot;The Name Specified Is Not Recognized...&quot;

{% raw %}

	Article: Q103368
	Product(s): Microsoft Windows NT
	Version(s): 3.1,3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): kbother
	Last Modified: 28-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.1, 3.5, 3.51, 4.0 
	- Microsoft Windows NT Workstation versions 3.1, 3.5, 3.51, 4.0 
	- Microsoft Windows NT Advanced Server 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	From the Windows NT Command Prompt, when you try to run a file or change to a
	directory whose name contains one of these characters
	
	  &  (  )  ^  ;  |  ,  or <space>
	
	you then receive one of the following error messages:
	
	  The name specified is not recognized as an internal or external command,
	  operable program or batch file.
	
	-or-
	
	  The system cannot find the path specified.
	  The name specified is not recognized as an internal or external command,
	  operable program or batch file.
	
	CAUSE
	=====
	
	Although File Manager and some other applications allow the use of the
	characters shown above, if you use any of these characters in a filename or
	directory name and then try to run the file or change to the directory from the
	Command Prompt, you will receive one of the error messages shown above.
	
	WORKAROUNDS
	-----------
	
	- In the Command Prompt, put quotation marks around the entire filename.
	
	  -or-
	
	- Put a "^" (without the quotation marks) before the extended character in the
	  filename or directory name. The ; and , characters will not work in a
	  filename or directory name.
	
	MORE INFORMATION
	================
	
	The Windows NT Command Prompt uses these characters for special functions. Refer
	to the Windows NT online Help file in the "What's New or Different from MS-DOS"
	section for information on the functions of these characters.
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Using File Manager, in the Windows NT program directory, copy NOTEPAD.EXE and
	  rename it to NOTE&PAD.EXE.
	
	2. From the Main group, start the Command Prompt.
	
	3. Change to the Windows NT program directory, type the following command, and
	  press ENTER:
	
	  note&pad
	
	  One of the above error messages will appear.
	
	Type the following command (with the quotation marks) to successfully run
	Notepad:
	
	  "note&pad"
	
	Additional query words: prodnt
	
	======================================================================
	Keywords          : kbother 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTW310 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS310 kbWinNTAdvSerSearch kbWinNTS351search kbWinNTS350search kbWinNTS310search kbWinNT310Search kbWinNTW310Search
	Version           : :3.1,3.5,3.51,4.0
	
	=============================================================================
	

{% endraw %}
