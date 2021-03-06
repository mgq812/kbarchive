---
layout: page
title: "Q63052: FIX: PWB 1.0 Extensions Will Only Return True Under MS-DOS"
permalink: /kb/063/Q63052/
---

## Q63052: FIX: PWB 1.0 Extensions Will Only Return True Under MS-DOS

{% raw %}

	Article: Q63052
	Product(s): Microsoft Programming Utilities
	Version(s): MS-DOS:1.0; OS/2:1.0
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 31-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Programmer's Workbench for MS-DOS, version 1.0 
	- Microsoft Programmer's Workbench for OS/2, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Extensions written for use by the Programmer's WorkBench (PWB) version 1.0 under
	the DOS operating system are recognized as returning true regardless of their
	actual return values.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in PWB version 1.0. This problem
	was corrected in PWB version 1.1.
	
	MORE INFORMATION
	================
	
	The use of return values as a way of providing conditional jumps inside PWB
	macros is a common practice that is affected by the above limitation for PWB
	extensions. The sample extension and macros below demonstrate the above problem.
	Once installed, both the f1() and f2() functions will be seen as returning true
	to PWB.
	
	Sample Code
	-----------
	
	  // TEST.C
	
	  #include <string.h>
	  #include <stdlib.h>
	  #include <ext.h>
	
	  PWBFUNC f1( unsigned argData, ARG far *pArg, flagType fMeta );
	  PWBFUNC f2( unsigned argData, ARG far *pArg, flagType fMeta);
	
	  // Switches.
	  struct swiDesc swiTable[] =
	  {
	     { NULL, NULL, 0 }
	  };
	
	  // Commands.
	  struct cmdDesc cmdTable[] =
	  {
	     { "f1", f1, 0, NOARG },
	     { "f2",f2,0, NOARG },
	     { NULL, NULL, 0, 0 }
	  };
	
	  void EXTERNAL WhenLoaded()
	  {
	      SetKey( "f1",         "alt+f" );
	      SetKey( "f2",       "ctrl+f" );
	      return;
	  }
	
	  PWBFUNC f1( unsigned argData, ARG far *pArg, flagType fMeta )
	  {
	   return(FALSE);  /* FALSE is defined as 0 in ext.h */ 
	  }
	
	  PWBFUNC f2( unsigned argData, ARG far *pArg, flagType fMeta)
	  {
	   return(TRUE);   /* TRUE is defined as 1 in ext.h  */ 
	  }
	
	  // End of TEST.C
	
	Sample Macros
	-------------
	
	  ; sample macros  for TOOLS.INI to test f1 and f2
	
	  load f1
	
	  test:=f1 ->loc1 arg "true" message => :>loc1 arg "false" message
	  test2:=f2 ->loc2 arg "true" message => :>loc2 arg "false" message
	
	  test:alt+t
	  test2:ctrl+2
	
	Additional query words: 1.00 buglist1.00 fixlist1.10
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbAudDeveloper kbPWBSearch kbZNotKeyword3 kbPWB100DOS kbPWB100OS2
	Version           : MS-DOS:1.0; OS/2:1.0
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
