---
layout: page
title: "Q80379: Stepping Through Self-Modifying Code in CodeView"
permalink: /kb/080/Q80379/
---

## Q80379: Stepping Through Self-Modifying Code in CodeView

{% raw %}

	Article: Q80379
	Product(s): Microsoft Programming Utilities
	Version(s): 2.2,3.0,3.11,3.14,4.0,4.01,4.02,4.05,4.1
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 26-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft CodeView for MS-DOS, versions 2.2, 3.0, 3.11, 3.14, 4.0, 4.01, 4.02, 4.05, 4.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Code that is written to modify its own contents may run differently when run one
	line at a time in the Microsoft CodeView Debugger (CV). This occurs because of
	the the way the 80x86 processors fetch instructions. Because this is a
	limitation of how CodeView works, care should be used when debugging
	self-modifying code.
	
	The code may run one way outside of CodeView, and another way from within
	CodeView. Also, running the program by using the go (F5) command instead of the
	step (F10) or trace (F8) command may affect the program's execution. Different
	processors can also affect this behavior.
	
	MORE INFORMATION
	================
	
	The 80x86 processor will try to pre-fetch the next instruction from memory while
	processing the current instruction. If the code being modified is already
	waiting in the instruction queue, then the processor will run the unmodified
	code. However, a jump instruction will invalidate the queue, causing the next
	instruction to be fetched before execution. In self-modifying code, this will
	cause the modified instruction to be run. When stepping through a program in
	CodeView, the instruction queue is always marked invalid, so all modified
	instructions are run. The code below demonstrates this behavior.
	
	If you step through the sample code in CodeView it will output "Num = 1". If you
	run straight though the code, allowing the processor to pre-fetch instructions,
	it will output "Num = 0".
	
	Sample Code
	-----------
	
	  /* Compile options needed: /Zi
	  */ 
	
	  #include<stdio.h>
	
	  void main(void)
	  {
	  unsigned int Num;
	
	  _asm {
	       mov ax, cs
	       push ds
	       mov ds, ax
	       inc byte ptr [cnt + 1]    /* Adding a "jmp cnt" between the  */ 
	  cnt: mov ax, 0                 /* INC and the MOV will cause the  */ 
	       mov Num, ax               /* modified code to be run         */ 
	       pop ds
	       }
	     printf("Num = %d",Num);
	  }
	
	Additional query words: kbinf 2.20 3.00 4.00 4.10
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbAudDeveloper kbCodeView kbZNotKeyword3 kbCodeView220DOS kbCodeView300DOS kbCodeView311DOS kbCodeView314DOS kbCodeView400DOS kbCodeView401DOS kbCodeView402DOS kbCodeView405DOS kbCodeView410DOS
	Version           : :2.2,3.0,3.11,3.14,4.0,4.01,4.02,4.05,4.1
	
	=============================================================================
	

{% endraw %}
