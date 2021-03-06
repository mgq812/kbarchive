---
layout: page
title: "Q251362: FIX: Suspend and Resume Thread Hangs Visual C++ Debugger"
permalink: /kb/251/Q251362/
---

## Q251362: FIX: Suspend and Resume Thread Hangs Visual C++ Debugger

{% raw %}

	Article: Q251362
	Product(s): Microsoft C Compiler
	Version(s): winnt:6.0
	Operating System(s): 
	Keyword(s): kbide kbVC600bug kbDSupport kbGrpDSVCCompiler kbVS600sp4fix kbVS600sp5fix
	Last Modified: 20-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Integrated Debugger, used with:
	   - Microsoft Visual C++, 32-bit Editions, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When debugging in the thread dialog box, suspend one of the threads and then
	continue debugging. When the debugger stops on another breakpoint, resume the
	suspend thread. As a result, the debugger stops responding, or hangs, and CPU
	utilization may go to 100%.
	
	CAUSE
	=====
	
	Under a debug build, every function call is prefixed with MOVESI, ESP (code
	bytes: 8B F4) for the run-time check feature (/GZ). Thus, if you set a
	breakpoint on any function call, the 8B is replaced with CC (INT 3) in memory to
	generate a user-defined exception. Before execution continues, the debugger
	replaces the CC with the original byte (in this case, 8B).
	
	The debugger ignores the first user-defined exception (0x80000003) for the
	breakpoint that was set. The byte after the 8B is F4. F4 is a HLT instruction
	which is a privileged instruction; when this instruction executes, a privileged
	instruction exception (0xC0000096) is generated. The debugger remains ignoring
	exceptions, but unlike the user-defined exception, the instruction pointer isn't
	advanced and when the debugger ignores this exception, the exception is
	generated again thus entering an endless loop.
	
	RESOLUTION
	==========
	
	One workaround is to use MsgBox() to simulate the suspend of thread.
	
	A supported fix for Visual C++ 6.0 that corrects this problem is now available
	from Microsoft, but it has not been fully regression tested and should be
	applied only to systems experiencing this specific problem.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information on support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	The English version of this fix should have the following file attributes or
	later:
	
	+----------------------------------------------------------------+
	| Name   | Size    | Date     | Time    | Version     | Platform | 
	+----------------------------------------------------------------+
	| dm.dll | 106,566 | 3/8/2000 | 6:50 AM | 6.00.8798.0 | x86      | 
	+----------------------------------------------------------------+
	
	
	NOTE: If this product was already installed on your computer when you purchased
	it from the Original Equipment Manufacturer (OEM) and you need this fix, please
	call the Pay Per Incident number listed on the above Web site. If you contact
	Microsoft to obtain this fix, a fee may be charged. This fee is refundable if it
	is determined that you only require the fix you requested. However, this fee is
	non-refundable if you request additional technical support, if your no-charge
	technical support period has expired, or if you are not eligible for standard
	no-charge technical support.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug was corrected in the latest service pack for
	Visual Studio 6.0.
	
	For additional information about Visual Studio service packs, click the article
	numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That a Visual Studio Service Pack Is Installed
	
	You can download the latest Visual Studio service pack from the following
	Microsoft Web site:
	
	  Visual Studio Product Updates
	  (http://msdn.microsoft.com/vstudio/downloads/updates.asp)
	
	MORE INFORMATION
	================
	
	Sample Code
	-----------
	
	  //   - Set a breakpoint on the printf() statement in ThreadMain().
	  //   - Start debugging the program.
	  //   - When the breakpoint is reached suspend the thread the breakpoint 
	  //     occurred in.
	  //   - Press F5. 
	  //   - When the breakpoint is reached resume the previously suspended
	  //     thread.
	  //   - Press F5.
	  //   - Note that the breakpoint in now not reached again and that CPU
	  //     usage is 100%.
	  // 
	  // Required compiler switches: /GZ
	  // 
	  #include <windows.h>
	  #include <stdio.h>
	  #include <process.h>
	  void ThreadMain(void *data)
	  {
	      for(int count=0; count<100; count++ )
	      {
	          printf("Thread id=%d,count=%d\n", (int)data, count );
	          Sleep( 1000 );
	      }
	      _endthread();
	  }
	
	  void main(void)
	  {
	      HANDLE ThreadId[2];
	      for (int i= 0; i < 2; i++)
	      {
	          Sleep(500);
	          ThreadId[i]=(HANDLE)_beginthread(ThreadMain, 0, (void *) i);
	      }
	      WaitForMultipleObjects( 2, ThreadId, TRUE, INFINITE );
	  }
	
	Additional query words: sp4
	
	======================================================================
	Keywords          : kbide kbVC600bug kbDSupport kbGrpDSVCCompiler kbVS600sp4fix kbVS600sp5fix 
	Technology        : kbVCsearch kbAudDeveloper kbIntegratedDebugger
	Version           : winnt:6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
