---
layout: page
title: "Q251005: OLE Automation Number Conversion Changed in SP4"
permalink: /kb/251/Q251005/
---

## Q251005: OLE Automation Number Conversion Changed in SP4

{% raw %}

	Article: Q251005
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0 SP4,4.0 SP5,4.0 SP6,4.0 SP6a
	Operating System(s): 
	Keyword(s): kbWinNT400PreSP7Fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 4.0 SP4, 4.0 SP5, 4.0 SP6, 4.0 SP6a 
	- Microsoft Windows NT Server versions 4.0 SP4, 4.0 SP5, 4.0 SP6, 4.0 SP6a 
	- Microsoft Windows NT Server, Enterprise Edition versions 4.0 SP4, 4.0 SP5, 4.0 SP6, 4.0 SP6a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	There may be conflicting symbols for decimal separators and digit grouping for
	numbers and currencies in a user's regional settings. For example:
	
	                  Numbers        Currency
	  ---------------------------------------
	  Decimal         ,              .
	  Grouping        .              ,
	
	Prior to Service Pack 4, programs can convert strings to numbers correctly in
	this situation. With Service Pack 4 or later, numbers are truncated after the
	first symbol in the string. Or, there may be other effects resulting in
	incorrect conversion of user input.
	
	CAUSE
	=====
	
	The conversion algorithm was changed so that it honors both number types. When
	the settings conflict, incorrect results occur.
	
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
	
	The English-language version of this fix should have the following file
	attributes or later:
	
	  Date       Time        Version       Size      File name
	  -----------------------------------------------------------
	  01/05/00   3:10:50pm   2.40.4514.1   143,632   Asycfilt.dll
	  01/05/00   3:10:50pm   2.40.4514.1   614,672   Oleaut32.dll
	  01/05/00   3:10:50pm   5.0.4514.1    164,112   Olepro.dll
	  01/05/00   3:10:50pm   2.40.4514.1    16,896   Stdole2.tlb
	
	
	
	WORKAROUND
	==========
	
	Programs can check for conflicting settings by calling the Win32 GetLocaleInfo
	function by using these values for the LCType parameter:
	
	                  Numbers           Currency
	  --------------------------------------------------------
	  Decimal         LOCALE_SDECIMAL   LOCALE_SMONDECIMALSEP
	  Grouping        LOCALE_STHOUSAND  LOCALE_SMONTHOUSANDSEP
	
	If conflicting settings are detected, the program can prompt the user to resolve
	the mismatch.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	The files for this hotfix are the same as those referenced in the following
	Microsoft Knowledge Base article:
	
	  
	
	  Q251002 Loading Invalid Image Using OLE Automation Displays Assertion
	
	Please retrieve the files by using this article number.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbWinNT400PreSP7Fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400search kbWinNT400search kbWinNTW400sp5 kbWinNTW400sp4 kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400sp6 kbWinNTSEnt400sp5 kbWinNTSEnt400sp4 kbWinNTS400sp6 kbWinNTS400sp5 kbWinNTS400sp4 kbWinNTS400search kbWinNTW400sp6 kbWinNTSEnt400SP6a kbWinNTW400SP6a
	Version           : winnt:4.0 SP4,4.0 SP5,4.0 SP6,4.0 SP6a
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
