---
layout: page
title: "Q152340: How To Configure the Command Window in Visual FoxPro Screen"
permalink: /kb/152/Q152340/
---

## Q152340: How To Configure the Command Window in Visual FoxPro Screen

{% raw %}

	Article: Q152340
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:3.0b
	Operating System(s): 
	Keyword(s): kbenv
	Last Modified: 15-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Macintosh, version 3.0b 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to configure the Command window in the Visual FoxPro
	screen. Visual FoxPro for Macintosh, like most Macintosh applications, does not
	have a parent application window. Many users want to simulate the windowing
	behavior of the Windows version within the Macintosh version. The Visual FoxPro
	Screen can provide some of this functionality including controlling the
	placement of the command window and preventing the Visual FoxPro Screen from
	obscuring other windows.
	
	MORE INFORMATION
	================
	
	This information covers customization through the default configuration file,
	Config.fpm.
	
	Method 1
	--------
	
	One of the most flexible Config.fpm commands is COMMAND. This allows you to pass
	any command you could enter in the Command window to Visual FoxPro every time
	you launch. The limitation to COMMAND is that only the last COMMAND line is
	processed. To include multiple commands in your configuration file, simply call
	a separate program file with multiple commands, without the COMMAND syntax. For
	example, assume you wanted to activate the Command window within the Visual
	FoxPro screen, display a picture, and wanted to call VFPStart, the program which
	initializes and adds Class Browser to the Tools menu:
	
	In your Config.fpm, place the following line:
	
	     COMMAND = DO Startup.prg
	
	The program file, Startup.prg, might look like this:
	
	     DO HOME()+"VFPStart.prg"
	     ACTIVATE WINDOW COMMAND IN SCREEN  && IN SCREEN clause is the key
	     _SCREEN.PICTURE="<path>:pict or bmp file"
	
	Method 2
	--------
	
	An alternative is to change the default setting of MACDESKTOP. When set to OFF,
	this specifies that windows reside on the main FoxPro for Macintosh window.
	Windows cannot be moved outside the main FoxPro for Macintosh window. If this
	setting is changed from within the Config.fpm, it will also affect system
	windows, such as the Command window. This will also cause all user-defined
	windows to be defined within the main Foxpro for Macintosh window by default.
	
	In your config.fpm, place the following line:
	
	     MACDESKTOP = OFF
	
	Additional query words: VFoxMac
	
	======================================================================
	Keywords          : kbenv 
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbVFP300bMac
	Version           : MACINTOSH:3.0b
	
	=============================================================================
	

{% endraw %}
