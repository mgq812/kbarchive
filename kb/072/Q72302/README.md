---
layout: page
title: "Q72302: Specifying A20 Handlers with HIMEM.SYS /M in MS-DOS"
permalink: /kb/072/Q72302/
---

## Q72302: Specifying A20 Handlers with HIMEM.SYS /M in MS-DOS

{% raw %}

	Article: Q72302
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.x,6.0,6.2,6.21
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 5.0, 5.0a, 6.0, 6.2, 6.21 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	MS-DOS version 5.0 includes HIMEM.SYS version 2.77. MS-DOS version 6.0 includes
	HIMEM.SYS version 3.07. MS-DOS versions 6.2, 6.21, and 6.22 include HIMEM.SYS
	version 3.10. These versions include an A20 handler for the following computers
	that can be used with the /M: or /MACHINE switch:
	
	  CODE            Number          A20 Handler
	  ----            ------          -----------
	  at              1               IBM PC/AT
	  ps2             2               IBM PS/2
	  pt1cascade      3               Phoenix Cascade BIOS
	  hpvectra        4               HP Vectra (A and A+)
	  att6300plus     5               AT&T 6300 Plus
	  acer1100        6               Acer 1100
	  toshiba         7               Toshiba 1600 and 1200XE
	  wyse            8               Wyse 12.5 MHz 286
	  tulip           9               Tulip SX
	  zenith          10              Zenith ZBIOS
	  at1             11              IBM PC/AT
	  at2             12              IBM PC/AT (alternative delay)
	  css             12              CSS Labs
	  at3             13              IBM PC/AT (alternative delay)
	  philips         13              Philips
	  fasthp          14              HP Vectra
	  ibm7552         15              IBM 7552 Industrial Computer
	  bullmicral      16              Bull Micral 60
	  dell            17              Dell XBIOS
	
	There are two values that are considered defaults. /M:1 is the standard default
	for IBM AT-class machines, and t/M:2 is the standard default for IBM PS/2
	machines. For most 100-percent-compatible machines, the /M:1, /M:11, /M:12, and
	/M:13 A-20 handler switches should work. Although the other switches are
	hardware specific, one may be required for proper operation on certain
	machines.
	
	NOTE: In the above list, the device driver should detect the correct handler to
	use. The following computers may need the corresponding switch added to the
	CONFIG.SYS file:
	
	  System                    Switch
	  ------                    ------
	  Bull Micral 60            /machine:16
	  COMPUADD 386 systems      /machine:1 or /machine:8
	  Datamedia 386/486         /machine:2
	  Hitachi HL500C            /machine:8
	  Intel 301z or 302         /machine:8
	  JDR 386/33                /machine:1
	  Toshiba 5100              /machine:7
	  UNISYS PowerPort          /machine:2
	
	MORE INFORMATION
	================
	
	The /M switch specifies which hardware the computer is using. If the wrong
	switch is used, HIMEM.SYS may not load properly or the system may hang. For more
	information, query on the following words:
	
	  HIMEM and /M
	
	Additional query words: 6.22 5.00 5.00a 6.00 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS621 kbMSDOS620 kbMSDOS600 kbMSDOS500 kbMSDOS500a
	Version           : MS-DOS:5.x,6.0,6.2,6.21
	
	=============================================================================
	

{% endraw %}
