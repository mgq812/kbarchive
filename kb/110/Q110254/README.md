---
layout: page
title: "Q110254: INFO: How to Restart Windows from Within FoxPro"
permalink: /kb/110/Q110254/
---

## Q110254: INFO: How to Restart Windows from Within FoxPro

{% raw %}

	Article: Q110254
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:2.5,2.5a,2.5b,3.0
	Operating System(s): 
	Keyword(s): kbcode
	Last Modified: 18-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a, 2.5b 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	You can restart Windows from inside a FoxPro for Windows application by using
	the Windows API function ExitWindows(). With this function, you can restart
	Windows without rebooting the entire system, as explained below.
	
	This code does not work under Windows 95, Windows 98 or Windows NT 4.0 because
	there is no ExitWindows entry point in USER32.EXE on Win32 Operating Systems.
	
	
	MORE INFORMATION
	================
	
	By using FOXTOOLS.FLL and the Windows API function ExitWindows(), you can
	restart Windows. The following code illustrates this concept.
	
	NOTE: While it is possible to restart Windows from within a FoxPro for Windows
	program by making use of the Windows API function ExitWindows(), FoxPro may not
	do a complete cleanup and may leave *.TMP files in your SET TEMP= subdirectory.
	
	     *** Begin Code ***
	     * WARNING: Make sure all work is saved before running code
	
	     SET LIBRARY TO SYS(2004)+"FOXTOOLS.FLL" ADDITIVE
	     do_over=REGFN("ExitWindows","II","I")
	     title="Program Message"
	     msg="Would you like to restart Windows now?"
	     choice=MSGBOX(msg,title,36)
	     IF choice=6    && button 'Yes' was chosen
	        =CALLFN(do_over,66,0)
	     ELSE
	        WAIT WINDOW "You have chosen not to restart Windows" TIMEOUT 2
	     ENDIF
	     *** End Code ***
	
	The ExitWindows() function requires two numeric values to be passed in and
	returns a single integer. The significance of the first integer (66) is that it
	is the decimal equivalent of 0x42 hexadecimal or EW_RESTARTWINDOWS, which is a
	low-order word in the C++ language. The second integer is reserved and is always
	zero. When the ExitWindows() function is called, it sends a message to all
	active applications that a request has been made to restart Windows. If all
	applications "agree" to be terminated, the WM_ENDSESSION message will be sent to
	all applications before Windows is restarted.
	
	REFERENCES
	==========
	
	Visual C++ Help file
	
	
	Additional query words: VFoxWin FoxWin 2.50 quit restart exit 3.00 2.50a
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbFoxPro250 kbFoxPro250a kbFoxPro250b kbVFP300
	Version           : WINDOWS:2.5,2.5a,2.5b,3.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
