---
layout: page
title: "Q45183: Incorrect Handling of SP Can Cause CodeView to Corrupt Stack"
permalink: /kb/045/Q45183/
---

## Q45183: Incorrect Handling of SP Can Cause CodeView to Corrupt Stack

{% raw %}

	Article: Q45183
	Product(s): See article
	Version(s): 2.20 2.30 | 2.20 2.30
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | | mspl13_basic
	Last Modified: 7-JUN-1989
	
	CodeView will use your program's stack for temporary variables in
	between assembly instructions. Thus, when writing an assembly language
	program, if you forget to increase the stack pointer (SP) to point
	beyond the memory locations you are using on the stack, CodeView will
	overwrite that memory.
	
	This is expected behavior. Even if CodeView did not use the stack, you
	would still have to increment the stack pointer to keep your program
	from overwriting your variables when you make a call, or with any
	operation that pushes values on the stack.

{% endraw %}
