---
layout: page
title: "Q29735: FIX: LES Instruction Assembles Incorrectly"
permalink: /kb/029/Q29735/
---

## Q29735: FIX: LES Instruction Assembles Incorrectly

{% raw %}

	Article: Q29735
	Product(s): Microsoft Macro Assembler
	Version(s): 5.1,5.1a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Macro Assembler (MASM), versions 5.1, 5.1a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The program example below demonstrates a problem with the LES instructions in
	Microsoft Macro Assembler (MASM) versions 5.1 and 5.1a. The first LES
	instruction (Parm1) assembles correctly, but the second instruction (Parm2)
	generates the error message:
	
	  error A2056: Immediate mode illegal
	
	The only difference between the two instructions is the order of the arguments.
	In earlier versions of MASM, they produced identical code.
	
	CAUSE
	=====
	
	The problem is with the type operator and the way it handles registers inside
	brackets ([]). The type operator makes things a constant on the left of the
	expression.
	
	Parm1 works because it handles registers inside brackets differently. "TYPE x"
	turns bp into a constant; +10 then turns it back into an addressing mode.
	
	However, in Parm2, bp+10 has been turned into an addressing mode, which is then
	turned into a constant by "TYPE x". This difference is demonstrated in the
	sample code below.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in MASM versions 5.1 and 5.1a. This
	problem was corrected in MASM version 6.0.
	
	MORE INFORMATION
	================
	
	Sample Code
	-----------
	
	  ; Assemble options needed: none
	
	  .MODEL   small
	
	  x STRUC
	  y DD ?
	  x ENDS
	
	  Parm1 EQU DWORD PTR [bp+TYPE x+10]
	  Parm2 EQU DWORD PTR [bp+10+TYPE x]
	
	  .CODE
	  begin:
	      les di,Parm1
	      les di,Parm2
	
	  END begin
	
	Additional query words: 5.10 5.10a buglist5.10 buglist5.10a fixlist6.00
	
	======================================================================
	Keywords          :  
	Technology        : kbMASMsearch kbAudDeveloper kbMASM510 kbMASM510a
	Version           : :5.1,5.1a
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
