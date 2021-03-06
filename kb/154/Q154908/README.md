---
layout: page
title: "Q154908: Mastering Access: Error When Viewing Video or Graphic Files"
permalink: /kb/154/Q154908/
---

## Q154908: Mastering Access: Error When Viewing Video or Graphic Files

{% raw %}

	Article: Q154908
	Product(s): Microsoft Mastering Series
	Version(s): 1.0,1.0a; WINDOWS:95
	Operating System(s): 
	Keyword(s): kberrmsg kbmm kbnokeyword
	Last Modified: 09-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- MSPRESS Mastering Microsoft Access Programming ISBN 1-55615-912-9, versions 1.0, 1.0a 
	- the operating system: Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You may receive a "File Not Found" error when attempting to view video or
	graphic files in Mastering Microsoft Access Programming.
	
	CAUSE
	=====
	
	This problem occurs when the application is unable to open files on the CD-ROM
	for binary input in order to extract size information out of the file header.
	This process fails when either no drivers are installed or only Real-mode
	drivers have been installed for the CD-ROM device.
	
	RESOLUTION
	==========
	
	To verify that your computer is running Protect Mode CD drivers, follow these
	steps:
	
	1. Click the Start button, point to Settings, and then click Control Panel.
	
	2. Double-click the System Control Panel.
	
	3. Click the Device Manager tab.
	
	4. Examine the list of devices under Computer. If CD-ROM appears in this list,
	  then you are running Windows 95 Protect Mode drivers.
	
	To remove any existing Real Mode CD drivers, follow these steps:
	
	1. Click the Start button, and then click Run.
	
	2. In the Open field, type "sysedit" (without the quotation marks), and then
	  click OK.
	
	3. Examine the Autoexec.bat file. Look for a line referencing the file
	  MSCDEX.EXE. For example:
	
	  C:\WINDOWS\COMMAND\MSCDEX.EXE /D:CDROM01
	
	  Remark out this line by placing "REM " at the beginning of the line.
	
	4. Examine the Config.sys file. Look for a line containing an identical string
	  to the "/D:" string identified above. For example:
	
	  DEVICEHIGH=C:\CDROM\IDECD.SYS /D:CDROM01
	
	  Remark out this line by placing "REM " at the beginning of the line.
	
	5. Exit the System Configuration Editor. When you are prompted to save your
	  changes, click Yes.
	
	To install Protect Mode CD drivers, follow these steps:
	
	NOTE: If your computer is already running Protect Mode CD drivers, the following
	steps are not necessary.
	
	1. Click the Start button, point to Settings, and then click Control Panel.
	
	2. Double-click the Add New Hardware icon.
	
	3. Allow the Add New Hardware Wizard to detect your CD-ROM device.
	
	REFERENCES
	==========
	
	For more information about how to accomplish these tasks in Windows, see your
	Windows printed documentation or Online Help.
	
	Additional query words: 1.00 1.00a multi media multimedia multi-media mmtitles
	
	======================================================================
	Keywords          : kberrmsg kbmm kbnokeyword 
	Technology        : kbMSPressSearch kbOSWin95 kbOSWinSearch kbZNotKeyword2
	Version           : :1.0,1.0a; WINDOWS:95
	
	=============================================================================
	

{% endraw %}
