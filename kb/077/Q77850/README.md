---
layout: page
title: "Q77850: Lotus 1-2-3 Release 3 and MS-DOS 5.0"
permalink: /kb/077/Q77850/
---

## Q77850: Lotus 1-2-3 Release 3 and MS-DOS 5.0

{% raw %}

	Article: Q77850
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 22-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Executing Lotus 1-2-3 Release 3 with MS-DOS 5.0 may cause any of the following
	problems:
	
	- computer lock up when loading 1-2-3
	
	- keyboard lock up
	
	- having to press a key several times to get a response
	
	- beeping when pressing a key
	
	- typing a character and having a different character displayed
	
	The following error message may also be encountered:
	
	  UNEXPECTED INTERRUPT
	
	Lotus provides a series of SET DOS16M environment commands to be used in the
	AUTOEXEC.BAT file to resolve these problems.
	
	This information applies to Microsoft MS-DOS version 5.0.
	
	MORE INFORMATION
	================
	
	These errors may occur if using a nonstandard technique for switching from
	protected mode to real mode.
	
	The Lotus series of SET DOS16M commands are specific to certain computer
	configurations and may eliminate these errors. These commands, as stated below,
	can be entered in at the MS-DOS prompt for testing before starting Lotus 1-2-3
	Release 3. Reboot the computer after trying each different command. After
	finding the one that works, add it to the AUTOEXEC.BAT file.
	
	Command            Application
	-------            -----------
	SET DOS16M=10      Use these commands for 80286 machines
	SET DOS16M=10,750  using the "fast" method of switching
	                  from protected to real mode.
	
	SET DOS16M=9       Use these commands for 80286 machines
	SET DOS16M=9,750   using the "standard" method of
	                  switching from protected to real mode.
	
	SET DOS16M=13      Use for AST Research 80286 machines
	                  with older keyboard ROM chips.
	
	SET DOS16M=7       Use for machines with older Phoenix
	                  Technologies ROM chips.
	
	SET DOS16M=6       Use for some AT&T PC 6300 series machine.
	
	SET DOS16M=2       Use for IBM PS/2 80286 machines.
	
	SET DOS16M=3       Use for some 80386 computers without VCPI
	                  drivers.
	
	If none of the above commands solve the problem, Lotus has a utility, available
	at no cost, called CHK1-2-3 that will identify the hardware in the system and
	suggest changes that will help run Release 3. CHK1-2-3 can be obtained from a
	local Lotus authorized reseller, a Lotus sales representative, or a Lotus
	authorized training center.
	
	The products included here are manufactured by vendors independent of Microsoft;
	we make no warranty, implied or otherwise, regarding these products' performance
	or reliability.
	
	Reference(s):
	
	Lotus Customer Service: (800) 345-1043
	
	Lotus Magazine, January 1990, pages 57-63
	
	Additional query words: 5.00 3rdparty
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS500
	Version           : MS-DOS:5.0
	
	=============================================================================
	

{% endraw %}
