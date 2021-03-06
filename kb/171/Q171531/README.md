---
layout: page
title: "Q171531: FIX: IPF When Changing Project Name with Binary Compatibility"
permalink: /kb/171/Q171531/
---

## Q171531: FIX: IPF When Changing Project Name with Binary Compatibility

{% raw %}

	Article: Q171531
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbVBp500 kbVS97sp2fix kbGrpDSVB kbvbp500sp2fix
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When building an ActiveX control project with "Binary Version Compatibility,"
	Visual Basic may cause the following error:
	
	  "VB5 has caused an invalid page fault in module <module> at
	  <address>"
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been fixed in Visual Studio 97 Service
	Pack 2.
	
	For more information on the Visual Studio 97 Service Pack 2, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q170365 INFO: Visual Studio 97 Service Packs - What, Where, and Why
	
	For a list of the Visual Basic 5.0 bugs that were fixed in the Visual Studio 97
	Service Pack 2, please see the following article in the Microsoft Knowledge
	Base:
	
	  Q171554 INFO: Visual Basic 5.0 Fixes in Visual Studio 97 Service Pack 2
	
	MORE INFORMATION
	================
	
	This behavior will only occur if a previous build of the ActiveX control is
	canceled due to an incompatibility warning and then a subsequent build of the
	ActiveX control is started.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start a new ActiveX Control project in Visual Basic 5.0.
	
	2. From the View menu, select Code.
	
	3. Enter the following code in the General Declarations section of
	  UserControl1:
	
	        Event Goo()
	        Public Boo
	
	4. Select Make Project1.ocx from the File menu, and click OK.
	
	5. Open the Project Properties dialog from the Project Menu.
	
	6. Select the Component Tab, and click Binary Compatibility.
	
	7. Select the General Tab and change the Project name to Project2. Click OK.
	
	8. (Important!!) Press CTRL+J in the UserControl1 Code window to invoke the list
	  of properties/methods. (A recompile is forced this way.)
	
	9. Make the Project1.ocx again from the File Menu. Click OK.
	
	10. Answer Yes to overwrite project1.ocx. When you get a warning about the name
	  property being different, choose Accept.
	
	11. Select Cancel from the incompatibility warning dialog.
	
	12. Select Cancel Again from the make project dialog.
	
	13. Choose Make Project1.ocx again from the File Menu. Select OK.
	
	14. Answer Yes to overwrite project1.ocx.
	
	  Visual Basic will cause a Invalid Page Fault in <module> at
	  <address>.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVBp500 kbVS97sp2fix kbGrpDSVB kbvbp500sp2fix 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500Search kbVBA500 kbVB500 kbZNotKeyword3
	Version           : 5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
