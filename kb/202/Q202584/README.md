---
layout: page
title: "Q202584: FIX: C1001 Compiling File Containing Local Enum with Debug Info"
permalink: /kb/202/Q202584/
---

## Q202584: FIX: C1001 Compiling File Containing Local Enum with Debug Info

{% raw %}

	Article: Q202584
	Product(s): Microsoft C Compiler
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbide kbVC600bug kbVS600sp3fix
	Last Modified: 07-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When building a source file that contains a function with a local enumeration,
	and the compiler options are set to generate debug information, the compiler
	fails with the following error:
	
	  <filename>(line#) : fatal error C1001: INTERNAL COMPILER ERROR
	  (compiler file 'msc1.cpp', line 1786)
	  Please choose the Technical Support command on the Visual C++
	  Help menu, or open the Technical Support help file for more information
	
	This bug typically occurs only during a full build and not when compiling an
	individual file.
	
	RESOLUTION
	==========
	
	The following is a suggested workaround:
	
	- Turn off use of precompiled headers. This solution can result in excessive
	  build times, especially for large projects.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	This bug was corrected in Visual Studio 6.0 Service Pack 3.
	
	For more information about Visual Studio service packs, please see the following
	articles in the Microsoft Knowledge Base:
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That Visual Studio 6.0 Service Packs Are Installed
	
	Additional query words:
	
	======================================================================
	Keywords          : kbide kbVC600bug kbVS600sp3fix 
	Technology        : kbVCsearch kbAudDeveloper kbVC600 kbVC32bitSearch
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
