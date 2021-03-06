---
layout: page
title: "Q196727: HOWTO: Process Idle Time and Termination in Performance Monitor"
permalink: /kb/196/Q196727/
---

## Q196727: HOWTO: Process Idle Time and Termination in Performance Monitor

{% raw %}

	Article: Q196727
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.1,3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.1 
	- Microsoft Windows NT Workstation version 3.1 
	- Microsoft Windows NT Advanced Server, version 3.1 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Sometimes it is desirable or necessary to determine when a process has ended
	when charting it in Performance Monitor. Use the Process|Elapsed Time counter to
	determine this.
	
	MORE INFORMATION
	================
	
	When monitoring a process in Chart View in Performance Monitor (from either
	current activity or a log file) you might need to determine when a process has
	ended. The Processor|%Processor Time counter is not appropriate for such a
	determination because it shows only if the process is active or idle.
	Performance Monitor shows an idle process at 0 percent processor time; however,
	it also shows an ended process at 0 percent processor time (if it was running at
	one time during the current charting or logging procedure).
	
	The Process|Elapsed Time counter, on the other hand, increments from zero from
	the moment a process is started and continues to increment until the process
	ends. After the process ends, this counter returns to zero. This is why this is
	the more appropriate counter to use for determining an ended process.
	
	NOTE: If you start a process, end it, and then start it again (in which case it
	usually receives a different Process ID, or PID) the Process|Elapsed Time
	counter accounts for this as the same process.
	
	TIP: You can use the Process|Elapsed Time counter for the CSRSS (the Win32
	subsystem) process instance to determine when a system has trapped or otherwise
	shut down while charting or logging it with Performance Monitor, in additional
	to the usual methods (that is, bookmark notations in the Time window).
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTW310 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS310 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS351search kbWinNTS350search kbWinNTS310search kbWinNT310Search kbWinNTW310Search
	Version           : WinNT:3.1,3.5,3.51,4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
