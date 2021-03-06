---
layout: page
title: "Q86368: Windows Err Msg: Could Not Continue... Paging Error"
permalink: /kb/086/Q86368/
---

## Q86368: Windows Err Msg: Could Not Continue... Paging Error

{% raw %}

	Article: Q86368
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.0,3.0a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 27-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.0, 3.0a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you run Microsoft Windows operating system version 3.0, the following error
	message may occur while running multiple applications:
	
	  Could not continue running Windows because of paging error.
	
	This error message is usually caused by running Windows on 386 computers with low
	RAM configurations. Increasing the amount of RAM or reducing the number of
	applications running will usually lessen the chances of receiving a paging
	error. In addition, running less MS-DOS-based applications with the PIF's
	background option set will help reduce these errors because Windows will be able
	to free more RAM by swapping the MS-DOS-based application out to the swap file.
	Some Windows-based applications are more prone to causing paging errors due to
	their memory-allocation methods.
	
	MORE INFORMATION
	================
	
	In 386 enhanced mode, Windows uses both physical RAM and hard-drive space, by
	using temporary or permanent swap files, to supply applications with the memory
	that they need. This process is controlled by Windows Virtual Memory Manager
	(VMM).
	
	How VMM Works
	-------------
	
	When virtual memory is used in 386 enhanced mode, some program code and data are
	kept in physical memory while the rest is swapped to the hard disk in a swap
	file to free more physical RAM for other applications. Whenever a reference is
	made to a memory address, it can be used without interruption if the information
	is currently in physical RAM. If the information is not in physical RAM, then a
	Page Fault occurs and the VMM takes control, pulling the required information
	back into physical RAM and, if necessary, swapping other information to the
	disk.
	
	What Happens When a Paging Error Occurs
	---------------------------------------
	
	Windows is encountering a nested page fault. It causes the hard drive to attempt
	to read and write information faster than the VMM can control. This condition is
	known as "disk-racing" or "disk-thrashing" due to the high rate of hard-disk
	access.
	
	This race condition occurs when one or more 4K pages of memory are brought into
	physical RAM from the swap file, and at the same time Windows must force one or
	more 4K pages out of physical RAM and into the swap file. The problem occurs
	when the pages that were moved to the swap file are needed immediately and are
	brought back into physical RAM, forcing the previous pages back to the swap
	file.
	
	The situation quickly degenerates into a disk-racing or disk-thrashing condition
	and the system shuts down, displaying the above error message. You may notice
	the hard drive light is constantly on before the error message is displayed.
	
	Windows uses three types of code:
	
	1. Fixed or locked code that cannot be moved from one memory address to another
	
	2. Moveable code that can be relocated from one memory address to another or
	  even swapped out to disk
	
	3. Discardable code that can be deleted from memory and is reread from the hard
	  drive when needed
	
	The condition to trigger this problem can be minimized by applications designed
	to use mostly moveable or discardable code, which is not locked into physical
	RAM address, but can be swapped out to disk or to another RAM address. In
	protect mode, moveable code can still be moved in memory even when the global
	memory is locked (GlobalLocked()).
	
	In Windows 3.0, fixed memory is page locked at a specific memory address in 386
	enhanced mode. This can create large chunks of code located in RAM memory that
	can quickly overload Windows' paging system.
	
	REFERENCES
	==========
	
	"Microsoft Windows Resource Kit" guide for operating system version 3.1, pages
	242-247
	
	Additional query words: 3.00 vm hang lock swapfile
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin300 kbWin300a
	Version           : WINDOWS:3.0,3.0a
	
	=============================================================================
	

{% endraw %}
