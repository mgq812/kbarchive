---
layout: page
title: "Q93456: SYSINI.WRI from Windows for Workgroups Version 3.1 (Part B)"
permalink: /kb/093/Q93456/
---

## Q93456: SYSINI.WRI from Windows for Workgroups Version 3.1 (Part B)

{% raw %}

	Article: Q93456
	Product(s): Microsoft Windows 3.x Retail Product
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 25-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows for Workgroups version 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following information was taken from the Microsoft Windows for Workgroups
	version 3.1 SYSINI.WRI file. This article contains the second half of the
	SYSINI.WRI file.
	
	MORE INFORMATION
	================
	
	[standard] Section Settings
	===========================
	
	The [standard] section contains settings that are specific to running
	Windows for Workgroups in standard mode:
	
	The [standard] section can contain the following settings:
	
	FasterModeSwitch=<0-or-1>
	
	Default: 0
	
	Purpose: Enabling this setting causes Windows for Workgroups running
	in standard mode to use a faster method of switching from protected
	mode to real mode on many 80286-based computers. When this setting is
	enabled, Windows for Workgroups responds quicker to hardware
	interrupts, allowing better throughput for interrupt-intensive
	applications, such as communications applications. In addition, you
	should enable this setting if you are using a Zenith Z-248 system and
	are losing characters while typing, or if you are using an Olivetti M-
	250-E and lose mouse functionality.
	
	Note: This setting has no effect on 80386-based computers. Some early
	IBM AT and compatible computers do not have the BIOS support necessary
	to use this setting. Enabling this setting on these computers may
	cause them to lock up when starting Windows for Workgroups.
	
	Int28Filter=<number>
	
	Default: 10
	
	Purpose: Specifies the interval of INT28h interrupts, generated when
	the system is idle, that are made visible (or reflected) to software
	that is loaded before Windows for Workgroups. Windows for Workgroups
	will reflect every nth interrupt, where n is the value of this
	setting. For example, a value of 1 reflects every INT28h interrupt, a
	value of 2 reflects every second INT28h interrupt, and so on.
	Increasing this value might improve Windows for Workgroups
	performance, but may interfere with some memory-resident programs,
	such as network software. Set this value to 0 to prevent any INT28h
	interrupts from being reflected. Setting this value too low (from 1 to
	9) might interfere with communications applications.
	
	NetHeapSize=<kilobytes>
	
	Default: 20
	
	Purpose: Specifies the size (in kilobytes) of the data-transfer buffer
	that Windows for Workgroups running in standard mode allocates in
	conventional memory for transferring data over a network. If an
	application is not running correctly, your network may require a
	larger buffer than the default value. Increasing this value will
	decrease the amount of memory available to applications. If no network
	software is running, this setting will be ignored and no memory will
	be allocated.
	
	[386Enh] Section Settings
	=========================
	
	The [386Enh] section contains information specific to running Windows
	for Workgroups in 386 enhanced mode, including information used for
	virtual-memory page swapping.
	
	The [386Enh] section can contain the following settings:
	
	AllVMsExclusive=<boolean>
	
	Default: False
	
	Purpose: If enabled, this setting forces all applications to run in
	exclusive full-screen mode, overriding all contrary settings in the
	applications' program information files (PIFs). Enabling this setting
	might prolong the length of the Windows session when you are running
	network and memory-resident software that is incompatible with Windows
	for Workgroups.
	
	COMBoostTime=<milliseconds>
	
	Default: 2
	
	Purpose: Specifies the amount of time (in milliseconds) to allow a
	virtual machine to process a COM interrupt. If, while running a
	communications application, you lose keyboard characters on the
	screen, you can try increasing this value.
	
	COMMdrv30=<boolean>
	
	Default: False
	
	Purpose: If enabled, the Virtual COM Driver (VCD) uses its own copy of
	the interrupt handler for the serial communications driver. This
	improves performance of your COM ports. Enable this setting if you are
	using a Windows version 3.0 serial communications driver. Disable this
	setting if you are using the standard Windows version 3.1 serial
	communications driver.
	
	COM1FIFO=<boolean>
	COM2FIFO=<boolean>
	COM3FIFO=<boolean>
	COM4FIFO=<boolean>
	
	Default: True
	
	Purpose: Specifies whether the FIFO buffer of a COM port's 16550
	Universal Asynchronous Receiver Transmitter (UART) should be enabled
	(True) or disabled (False). If a serial port does not have a 16550
	UART, this setting is ignored.
	
	Note: These values are used by Windows for Workgroups for both
	standard and 386 enhanced modes.
	
	COMIrqSharing=<boolean>
	
	Default: True for Micro Channel Architecture and EISA machines; False
	for all other machines.
	
	Purpose: Specifies whether COM interrupt lines are sharable between
	multiple serial ports or with other devices. Enable this setting if
	your machine uses the same interrupt for COM3 or COM4 as it does for
	COM1 or COM2.
	
	DOSPromptExitInstruc=<boolean>
	
	Default: Yes
	
	Purpose: If this setting is enabled, when you start MS-DOS Prompt, a
	message appears with instructions on how to exit and switch away from
	MS-DOS Prompt. Disable this setting if you do not want to see the
	message.
	
	DualDisplay=<boolean>
	
	Default: See "Purpose" below.
	
	Purpose: Typically, when running in 386 enhanced mode, the memory
	between B000:0000 and B7FF:000F is used by the general system unless a
	secondary display is detected. Enable this setting if you are using a
	VGA-based color display and want EMM386.EXE to include this address
	space as an upper memory block (UMB). In addition to enabling this
	setting, you must include the i= option in the device=EMM386.EXE
	command line in your CONFIG.SYS file as follows:
	
	  device=EMM386.EXE  i=B000-B7FF
	
	If this setting is disabled, the address range is available on EGA
	systems, but not on VGA systems, because the VGA display device
	supports monochrome modes, which use this address space.
	
	EMMExclude=<paragraph-range>
	
	Default: None
	
	Purpose: Specifies a range of memory that Windows for Workgroups will
	not scan to find unused address space. This has the side effect of
	turning off the RAM and ROM search code for the range. The range (two
	paragraph values separated by a hyphen) must be between A000 and EFFF.
	This scanning can interfere with some adapters that use the same
	memory area. The starting value is rounded down and the ending value
	is rounded up to a multiple of 16K. For example, you could set
	EMMExclude=C800-CFFF to prevent Windows for Workgroups from scanning
	the addresses C800:0000 through CFFF:000F. You can specify more than
	one range by including more than one EMMExclude line.
	
	EMMInclude=<paragraph-range>
	
	Default: None
	
	Purpose: Specifies a range of memory that Windows for Workgroups will
	treat as unused address space regardless of what may be there.
	EMMInclude takes precedence over EMMExclude if you specify ranges that
	overlap. The range (two values separated by a hyphen) must be between
	A000 and EFFF. The starting value is rounded down and the ending value
	is rounded up to a multiple of 16K. For example, you could set
	EMMInclude=C800-CFFF to ensure that Windows for Workgroups can use the
	addresses C800:0000 through CFFF:000F. You may specify more than one
	range by including more than one EMMInclude line.
	
	EMMPageFrame=<paragraph>
	
	Default: None
	
	Purpose: Specifies the starting paragraph where the 64K page frame
	will begin when Windows for Workgroups (running in 386 enhanced mode)
	cannot find a suitable page frame. Allows an EMM page frame in an area
	containing some unused RAM or ROM. For example, you could set
	EMMPageFrame=C400 to start the page frame at C400:0000.
	
	EMMSize=<kilobytes>
	
	Default: 65536
	
	Purpose: Specifies the total amount of memory available for mapping as
	expanded memory. The default value allocates the maximum possible
	amount of system memory as expanded memory. Specify a value for this
	setting if you run an application that allocates all of the available
	expanded memory. If this is the case, you cannot create new virtual
	machines. If this value is zero, no expanded memory is allocated, but
	the EMM driver will load. To disable EMM and prevent the EMM driver
	from loading, use the NoEMMDriver setting.
	
	EnableSharingPopUps=<boolean>
	
	Default: False
	
	Purpose: Specifies whether a SHARE.EXE sharing-violation message
	should appear when a sharing violation occurs while you are using
	VSHARE. If this setting is enabled, the SHARE.EXE messages will
	appear. If this setting is disabled, the SHARE.EXE message will not
	appear and you will not be notified of a sharing violation. Enable
	this setting if you are using an MS-DOS-based application that relies
	on the sharing-violation message.
	
	FileSysChange=<on-or-off>
	
	Default: Off in 386 enhanced mode; not supported in standard mode.
	
	Purpose: Indicates whether File Manager automatically updates file
	information anytime an MS-DOS-based application creates, renames, or
	deletes a file. If this setting is disabled, a virtual machine can run
	exclusively, even if it modifies files. Enabling this setting can slow
	down system performance significantly. If you are sharing directories
	and someone else changes the contents of your directories by using an
	MS-DOS-based application, File Manager does not update the directory
	or file information, even if this setting is enabled.
	
	InDOSPolling=<boolean>
	
	Default: No
	
	Purpose: If enabled, prevents Windows for Workgroups from running
	other applications when memory-resident software has the InDOS flag
	set. Enabling this setting is necessary if the memory-resident
	software needs to be in a critical section to do operations off an
	INT21 hook, but will slow down system performance slightly.
	
	INT28Critical=<boolean>
	
	Default: True
	
	Purpose: Specifies whether a critical section is needed to handle
	INT28h interrupts used by memory-resident software. Some networks do
	internal task switching on INT28h interrupts. These interrupts might
	lock up some network software, indicating the need for an INT28h
	critical section. If you are not using such software, you might
	improve Windows task switching by disabling this setting.
	
	LocalReboot=<on-or-off>
	
	Default: On
	
	Purpose: Specifies whether you can press CTRL+ALT+DEL to quit
	applications that cause an unrecoverable error in 386 enhanced mode.
	If this setting is enabled, you can quit the applications without
	restarting Windows for Workgroups. If this setting is disabled,
	pressing CTRL+ALT+DEL will restart your entire system.
	
	MaxBPs=<number>
	
	Default: 200
	
	Purpose: Specifies the maximum number of break points (a method for
	transferring control to Windows running in 386 enhanced mode) that can
	be used by the virtual-memory manager. You may need to increase this
	value if you are using Microsoft C version 7.0 or a third-party
	virtual-device driver that requires more break points than the default
	value.
	
	MaxCOMPort=<number>
	
	Default: 4
	
	Purpose: Specifies the maximum number of COM ports supported in 386
	enhanced mode. Change this value if you have more than four COM ports
	installed in your computer.
	
	NetAsynchFallback=<boolean>
	
	Default: False
	
	Purpose: If this setting is enabled, Windows for Workgroups attempts
	to save a failing NetBIOS request. When an application issues an
	asynchronous NetBIOS request, Windows for Workgroups attempts to
	allocate space in its global network buffer to receive the data. If
	there is insufficient space in the global buffer, Windows for
	Workgroups typically fails the NetBIOS request. If this setting is
	enabled, Windows for Workgroups attempts to save such a request by
	allocating a buffer in local memory and preventing any other virtual
	machines from running until the data is received or the timeout period
	(specified by the NetAsynchTimeout setting) expires.
	
	NetAsynchTimeout=<seconds>
	
	Default: 5.0
	
	Purpose: Specifies the timeout period (in seconds) when Windows for
	Workgroups will enter a critical section in order to service an
	asynchronous NetBIOS request. It is used only when the
	NetAsynchFallback setting is enabled. This value can include a decimal
	(such as 0.5).
	
	NetCard=<filename>
	
	Default: None (Setup sets this value to match your configuration.)
	
	Purpose: Specifies the virtual-device drivers for your network adapter
	that Windows for Workgroups uses when running in 386 enhanced mode.
	
	NetDMASize=<kilobytes>
	
	Default: 32 on Micro Channel Architecture machines (IBM PS/2 or
	compatible); 0 on non-Micro Channel Architecture machines (IBM PC/AT
	or compatible).
	
	Purpose: Specifies the DMA buffer size (in kilobytes) for NetBIOS
	transport software if a network has been installed. In this case, the
	buffer size is the larger of this value or the value of DMABufferSize.
	
	NetHeapSize=<kilobytes>
	
	Default: 12
	
	Purpose: Specifies the size (in kilobytes) of the data-transfer
	buffers in conventional memory that Windows for Workgroups allocates
	for transferring data over a network when running in 386 enhanced
	mode. This setting is only needed if you are using real-mode
	protocols. It is not required if you are using the VNB.386 protocol.
	All values are rounded up to the nearest 4K.
	
	Network=<filename-or-devicename>
	
	Default: vnetbios.386, vnetsup.386, vredir.386, vserver.386,
	vbrowse.386, vwc.386
	
	Purpose: Specifies the virtual-network drivers that are used when
	Windows for Workgroups is running in 386 enhanced mode.
	
	ReflectDosInt2A=<boolean>
	
	Default: False
	
	Purpose: Indicates whether Windows for Workgroups should consume or
	reflect DOS INT 2A signals. The default means Windows for Workgroups
	will consume these signals and therefore run more efficiently. Enable
	this setting if you are running memory-resident software that relies
	on detecting INT2A messages.
	
	SecondNet=<filename>
	
	Default: None (Setup sets this value to match your configuration.)
	
	Purpose: Specifies the virtual-network drivers for the networks you
	have added support for. Windows for Workgroups uses these drivers when
	running in 386 enhanced mode.
	
	SyncTime=<boolean>
	
	Default: True
	
	Purpose: If this setting is enabled, Windows for Workgroups
	periodically synchronizes its time with the computer's CMOS clock. If
	this setting is disabled, Windows for Workgroups usually maintains the
	correct time, unless TrapTimerPorts is disabled and you are running
	applications that can cause the system time to run faster or slower
	than the actual time. This setting is related to the TrapTimerPorts
	setting.
	
	TimerCriticalSection=<milliseconds>
	
	Default: 0
	
	Purpose: Instructs Windows for Workgroups to go into a critical
	section around all timer interrupt code and specifies a timeout period
	(in milliseconds). Specifying a positive value causes only one virtual
	machine at a time to receive timer interrupts. Some networks,
	protocols, and other global memory-resident software may fail unless
	this setting is used. However, using this setting slows down
	performance and can make the system seem to stop for short periods of
	time.
	
	Transport=<filename>
	
	Default: vnb.386 (Microsoft NetBEUI)
	
	Purpose: Specifies the network-protocol virtual-device-driver file
	that Windows for Workgroups uses when running in 386 enhanced mode.
	
	TrapTimerPorts=<boolean>
	
	Default: True
	
	Purpose: Specifies whether Windows for Workgroups should trap read and
	write operations to the system timer ports that are performed by
	applications. If this setting is disabled, Windows for Workgroups will
	not trap these operations, allowing applications that frequently read
	or write to the timer to run faster. However, this may interfere with
	ability of Windows for Workgroups to keep accurate system time. If
	this setting is disabled, Windows for Workgroups can usually detect
	when an application has changed the timer interrupt interval and then
	make any adjustments to the time. If your system's time appears to be
	running fast or slow, enable this setting. If you do not want to
	enable this setting, enable the SyncTime setting. This causes Windows
	for Workgroups to check the time periodically and then make any
	necessary adjustments.
	
	V86ModeLANAs=<lana number, lana number>
	
	Default: None
	
	Purpose: Specifies the LANA numbers for all the real-mode protocols
	and NetBIOS's that Windows for Workgroups recognizes. This setting is
	for real-mode protocols and NetBIOS's only. This setting should not
	include any LANA numbers for protected-mode protocols or NetBIOS's. If
	you start the network before starting Windows for Workgroups, the
	values for this setting must include the LANA numbers for the real
	mode protocols and NetBIOS's that you want to use. If you do not start
	the network before starting Windows for Workgroups, make sure that the
	values for this setting do not include LANA numbers for protected-mode
	protocols or NetBIOS's.
	
	VirtualHDIrq=<on-or-off>
	
	Default: On for AT-compatible computers; Off for all other computers.
	
	Purpose: If enabled, Windows for Workgroups in 386 enhanced mode can
	terminate interrupts from the hard disk controller, bypassing the ROM
	routine that handles these interrupts. Some hard disk drives might
	require this setting to be disabled in order for interrupts to be
	processed correctly. If this setting is disabled, the ROM routine
	handles the interrupts, which slows down system performance.
	
	Additional query words: 3.10 wfw wfwg
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWFWSearch kbWFW310
	Version           : WINDOWS:3.1
	
	=============================================================================
	

{% endraw %}
