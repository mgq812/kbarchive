---
layout: page
title: "Q246490: PRB: Unspecified Error When You Add an HTML Template to WebClass"
permalink: /kb/246/Q246490/
---

## Q246490: PRB: Unspecified Error When You Add an HTML Template to WebClass

{% raw %}

	Article: Q246490
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbVBp600 kbVisID600 kbWebClasses kbGrpDSASP kbDSupport
	Last Modified: 25-APR-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When adding an HTML template to a WebClass, Visual Basic may display the
	following error message in a WebClass Designer dialog box:
	
	  An unspecified error has occurred
	
	CAUSE
	=====
	
	The Triedit.dll, which is located by default in the C:\Program Files\Common
	Files\Microsoft Shared\Triedit folder or its dependent dynamic-link libraries
	(DLLs), may not be registered correctly.
	
	RESOLUTION
	==========
	
	Unregister and reregister the Triedit.dll by entering the following command in
	the Run box, accessed from the Start button, or within the Command Prompt:
	
	  regsvr32 /u "c:\program files\common files\microsoft shared\triedit\triedit.dll"
	  regsvr32 "c:\program files\common files\microsoft shared\triedit\triedit.dll"
	
	You should be able to add an HTML template to your WebClass. If this does not
	work, the error may not be the Triedit.dll, but its dependent DLLs. You may have
	to update Internet Explorer to the latest version. Or, do an uninstall and
	reinstall of Internet Explorer.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	The Triedit.dll is installed with Visual Studio, Office, and Internet Explorer.
	When an HTML template is added to a WebClass, the Triedit.dll is used to parse
	the HTML template to search for tags that could trigger server events.
	
	REFERENCES
	==========
	
	For additional information and technical articles on using WebClasses, see the
	following page at the Visual Basic site:
	
	  http://msdn.microsoft.com/vbasic/technical/articles/internet.asp
	
	For the latest Knowledge Base articles and other support information on Visual
	Basic, see the following page on the Microsoft Technical Support site:
	
	  http://support.microsoft.com/support /vbasic/
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVBp600 kbVisID600 kbWebClasses kbGrpDSASP kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : :6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
