---
layout: page
title: "Q175644: Dr. Watson Fails to Appear Because of Long File Names in Path"
permalink: /kb/175/Q175644/
---

## Q175644: Dr. Watson Fails to Appear Because of Long File Names in Path

{% raw %}

	Article: Q175644
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.51,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it
	if a problem occurs. For information on how to do this, view the "Restoring
	the Registry" online Help topic in Regedit.exe or the "Restoring a Registry
	Key" online Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	Applications that are running on a computer running Windows NT Server or Windows
	NT Workstation may fail, but there is no error message or any other indication
	of failure, and no log is ever created.
	
	CAUSE
	=====
	
	During the installation of certain applications such as Visual C++ 5.0, the
	setup program changes the default debugger to the application itself. If that
	application is installed in a location that contains a long file name, or spaces
	in the path, the previously described symptom occurs.
	
	RESOLUTION
	==========
	
	Use one of the following methods to resolve this problem. The first two methods
	change the default debugger back to Dr. Watson.
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it.
	
	Method 1
	--------
	
	1. Click Start, point to Programs, and then click Command Prompt.
	
	2. Type the following command to start Dr. Watson and change Dr. Watson to the
	  default debugger:
	
	  " Drwtsn32 -i" (without the quotation marks)
	
	Method 2
	--------
	
	1. Run Registry Editor (regedt32.exe).
	
	2. Go to the following key:
	
	  HKEY_LOCAL_MACHINE\Software\Microsoft\WindowsNT\CurrentVersion
	  \AeDebug
	
	  NOTE: The above registry key is one path; it has been wrapped for readability.
	
	3. To change the default debugger back to Dr. Watson, modify the debugger value
	  to the following:
	
	  Value Name: Debugger
	  Data Type : REG_SZ
	  Data      : Drwtsn32 -p %ld -e %ld -g
	
	Method 3
	--------
	
	The following method will allow Visual C++ 5.0 to run as the default debugger:
	
	1. Run Registry Editor (regedt32.exe).
	
	2. Go to the following key:
	
	  HKEY_LOCAL_MACHINE\Software\Microsoft\WindowsNT\CurrentVersion
	  \AeDebug
	
	  NOTE: The above registry key is one path; it has been wrapped for readability.
	
	3. Modify the current debugger path to use the short file name, or place
	  quotation marks around the data path to allow the spaces to be correctly
	  interpreted.
	
	  For example, if Visual C++ 5.0 is installed and the path is C:\Program
	  Files\<application>, change the data value to the following:
	
	  Value Name: Debugger
	  Data Type : REG_SZ
	  Data      : C:\Progra~1\DevStudio\SharedIDE\Bin\Msdev.exe %ld -e %ld
	
	  -or-
	
	  Data      : "C:\Program Files\DevStudio\SharedIDE\Bin\Msdev.exe %ld
	  -e %ld"
	
	  NOTE: The above registry key is one path; it has been wrapped for readability.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.0. We are
	researching this problem and will post new information here in the Microsoft
	Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	When an application fails on a computer running Windows NT, that application
	tries to load a specified debugger, to log information about the failure.
	Windows NT attaches the specified debugger to the application, and generates a
	log will that contains information about the cause of the application failure.
	By default, Windows NT launches Dr. Watson. However, certain applications may
	change this default and include the path to the new debugger.
	
	If the path includes a long file name such as:
	
	  C:\Program Files\...
	
	Windows NT will not read the path correctly, and the debugger for an application
	that is failing will not load unless the full path is specified in the user's
	environment.
	
	Additional query words: load fails crash crashes disappears
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT400search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS351search
	Version           : WinNT:3.51,4.0
	Hardware          : ALPHA PPC x86
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
