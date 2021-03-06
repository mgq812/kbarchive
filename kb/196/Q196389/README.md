---
layout: page
title: "Q196389: STOP 0x0000000A or STOP 0x00000050 in NTOSKRNL.EXE"
permalink: /kb/196/Q196389/
---

## Q196389: STOP 0x0000000A or STOP 0x00000050 in NTOSKRNL.EXE

{% raw %}

	Article: Q196389
	Product(s): Microsoft Windows NT
	Version(s): 4.0 SP3
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 SP3 
	- Microsoft Windows NT Server version 4.0 SP3 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	During the execution of a program, a "STOP 0x0000000A" or "STOP 0x00000050"
	error message may appear.
	
	The parameters of the stop code may vary.
	
	The problem only occurs with Windows NT 4.0 with Service Pack 3 installed.
	
	The issue was first noticed during the second portion of Exceed 6.1 Setup if the
	workstation files are stored on a NetWare 4.11 server. Various other scenarios
	can reproduce the same issue.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Windows NT 4.00 service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English-language version of this fix should have the following file
	attributes or later:
	
	  Date      Time    Version      Size    File name     Platform
	  -------------------------------------------------------------
	  6/3/1998  3:28pm  4.0.1381.43 932KB    NTKRNLMP.EXE  x86
	  6/3/1998  3:27pm  4.0.1381.43 903KB    NTOSKRNL.EXE  x86
	  6/3/1998  3:28pm  4.0.1381.43 1376KB   NTKRNLMP.EXE  Alpha
	  6/3/1998  3:27pm  4.0.1381.43 1349KB   NTOSKRNL.EXE  Alpha
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	This problem was first corrected in Windows NT version 4.0 Service Pack 5.
	
	The fix is actually a post-Service Pack 3 Hotfix for customers running Windows NT
	4.0 Service Pack 3.
	
	
	
	MORE INFORMATION
	================
	
	If you are running Windows NT Terminal Server and are experiencing the same
	issue, please see the following article in the Microsoft Knowledge Base:
	
	  Q216538 STOP 0x0000000A in NTOSKRNL at 801453ea
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400search kbWinNT400search kbWinNTW400sp3 kbWinNTSsearch kbWinNTS400sp3 kbWinNTS400search
	Version           : :4.0 SP3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
