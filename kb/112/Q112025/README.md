---
layout: page
title: "Q112025: Updated VSHARE.386 for Windows/Windows for Workgroups"
permalink: /kb/112/Q112025/
---

## Q112025: Updated VSHARE.386 for Windows/Windows for Workgroups

{% raw %}

	Article: Q112025
	Product(s): Microsoft Windows 3.x Retail Product
	Version(s): 3.1,3.11
	Operating System(s): 
	Keyword(s): win31
	Last Modified: 14-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.1, 3.11 
	- Microsoft Windows for Workgroups 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The WW1000.EXE file contains VSHARE.386 version 3.11.0.402. This version of
	VSHARE.386 is compatible with Microsoft Windows version 3.1 and Windows for
	Workgroups versions 3.1 and 3.11.
	
	  NOTE: Microsoft Office versions 4.2 and 4.3 install version 3.11.0.401 of
	  VSHARE.386.
	
	This version of VSHARE.386 differs from the version included with Windows for
	Workgroups 3.11 (version 3.11.0.300) in the following ways:
	
	- This version of VSHARE.386 supports Windows version 3.1.
	
	- This version of VSHARE.386 corrects a problem than can cause Windows for
	  Workgroups 3.11 to stop responding (hang) when you start your computer.
	
	USING VSHARE.386
	----------------
	
	MORE INFORMATION
	================
	
	If you are using applications that support OLE 2.0, you must run either
	SHARE.EXE or VSHARE.386. VSHARE.386 eliminates the need to run SHARE.EXE when
	you run Windows 3.1 or Windows for Workgroups in 386 enhanced mode. If you run
	Windows 3.1 in standard mode, you must run SHARE.EXE. If you run applications
	that are not compatible with SHARE.EXE and you are running Windows 3.1 in 386
	enhanced mode, the applications may work with VSHARE.386 instead of SHARE.EXE.
	
	INSTALLING THE UPDATED VSHARE.386 FILE
	--------------------------------------
	
	To install VSHARE.386 version 3.11.0.402, follow these steps:
	
	1. Download the WW1000.EXE file from the Microsoft Software Library.
	
	2. Double-click the WW1000.EXE file you downloaded in step 1.
	
	3. Quit Windows.
	
	4. At the MS-DOS command prompt, type the following command and then press
	  ENTER
	
	  copy <source>:\vshare.386 <location>
	
	  where <source> is the directory containing the file you downloaded from
	  online services, and <location> is the path to your Windows\SYSTEM
	  subdirectory.
	
	  For example, if you downloaded the WW1000.EXE file from online services to
	  C:\DOWNLOAD and C:WINDOWS\SYSTEM is the path to your Windows\SYSTEM
	  subdirectory, type:
	
	  copy c:\download\vshare.386 c:\windows\system
	
	5. Use any text editor (such as MS-DOS Editor) to edit the AUTOEXEC.BAT file.
	  Remove the SHARE.EXE command from the AUTOEXEC.BAT file and then save and
	  close the file.
	
	6. Edit the [386Enh] section of the SYSTEM.INI file to add the following line:
	
	  device=vshare.386
	
	7. Save and then close the SYSTEM.INI file.
	
	8. Restart your computer.
	
	The following file(s) are available for download from the Microsoft Software
	Library:
	
	  Ww1000.exe
	  (http://download.microsoft.com/download/win31/Update/3.11.0.402/WIN/EN-US/ww1000.exe)
	
	For more information about downloading files from the Microsoft Software Library,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	
	Additional query words:
	
	======================================================================
	Keywords          : win31 
	Technology        : kbAudDeveloper kbWin3xSearch kbWFWSearch kbZNotKeyword3 kbWin310 kbWin311
	Version           : :3.1,3.11
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
