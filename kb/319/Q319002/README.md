---
layout: page
title: "Q319002: FIX: Toolbar May Cause Incorrect Control Focus with MSAA"
permalink: /kb/319/Q319002/
---

## Q319002: FIX: Toolbar May Cause Incorrect Control Focus with MSAA

{% raw %}

	Article: Q319002
	Product(s): Microsoft FoxPro
	Version(s): 7.0
	Operating System(s): 
	Keyword(s): kbGrpDSFox kbDSupport kbCodeSnippet kbvfp700 _IK283 kbVFP700sp1fix
	Last Modified: 17-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 7.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use the Accessible Event Watcher from the Microsoft Active
	Accessibility Software Development Kit (SDK), and a toolbar control is present,
	Microsoft Active Accessibility may incorrectly indicate that a control on the
	toolbar has focus, when the control on the form actually has the focus. This may
	also occur with screen reader products that use Active Accessibility.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Visual FoxPro for
	Windows 7.0. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q316964 How to Obtain the Latest Visual FoxPro for Windows 7.0 Service Pack
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Visual FoxPro for
	Windows 7.0.
	
	This problem was first corrected in Visual FoxPro for Windows 7.0 Service Pack 1.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce the Behavior
	-------------------------------
	
	1. Download the following files from Microsoft Active Accessibility 2.0 SDK
	  Tools
	  (http://www.msdn.Microsoft.com/downloads/default.asp?URL=/downloads/sample.asp?url=/msdn-files/027/001/785/msdncompositedoc.xml),
	  and then save them in the same folder:
	
	   - Accevent32.exe
	   - Event32.dll
	
	2. Start Visual FoxPro 7.0. Make sure that the Properties window is closed.
	
	3. Run the Accessible Event Watcher (AccEvent32.exe) from the files that you
	  downloaded.
	
	4. Return to Visual FoxPro, paste the following code in a program (.prg), and
	  then run the program from the Command window:
	
	  PUBLIC oForm AS FORM, ;
	  	oTB AS TOOLBAR
	
	  oTB = NULL
	  oForm = NEWOBJECT("MyForm")
	  oForm.SHOW
	  READ EVENTS
	  RELEASE oTB
	  RELEASE oForm
	
	  *~~~~~~~~~~
	  DEFINE CLASS MyForm AS FORM
	  	AUTOCENTER = .T.
	  	SHOWWINDOW = 2
	
	  	ADD OBJECT FormText1 AS TEXTBOX WITH TOP = 50
	  	ADD OBJECT FormEdit1 AS EDITBOX WITH TOP = 80
	
	  	ADD OBJECT FormOptiongroup1 AS OPTIONGROUP WITH TOP = 150, ;
	  		BUTTONCOUNT = 2, ;
	  		HEIGHT = 50, ;
	  		WIDTH = 150
	
	  	PROCEDURE FormOptiongroup1.INIT
	  		THIS.SETALL("Autosize", .T.)
	  	ENDPROC
	
	  	ADD OBJECT FormOptiongroup2 AS OPTIONGROUP WITH TOP = 150, ;
	  		BUTTONCOUNT = 2, ;
	  		HEIGHT = 50, ;
	  		WIDTH = 150, ;
	  		LEFT = 175
	
	  	PROCEDURE FormOptiongroup2.INIT
	  		THIS.SETALL("Autosize", .T.)
	  	ENDPROC
	
	  	PROCEDURE QUERYUNLOAD()
	  		CLEAR EVENTS
	  	ENDPROC
	
	  	PROCEDURE ACTIVATE()
	  		IF ISNULL(oTB)
	  			oTB = NEWOBJECT("MyToolbar")
	  			oTB.SHOW
	  		ENDIF
	  	ENDPROC
	  ENDDEFINE
	
	  DEFINE CLASS MyToolbar AS TOOLBAR
	  	SHOWWINDOW = 1
	  	ADD OBJECT ToolbarCommand1 AS COMMANDBUTTON WITH CAPTION = "1"
	  	ADD OBJECT ToolbarCommand2 AS COMMANDBUTTON WITH CAPTION = "2"
	  	ADD OBJECT ToolbarCommand3 AS COMMANDBUTTON WITH CAPTION = "3"
	  	ADD OBJECT ToolbarCommand4 AS COMMANDBUTTON WITH CAPTION = "4"
	  	ADD OBJECT ToolbarCommand5 AS COMMANDBUTTON WITH CAPTION = "5"
	  	PROCEDURE INIT
	  		THIS.SETALL("width", 26, "Commandbutton")
	  	ENDPROC
	  ENDDEFINE
	
	5. Press the TAB key a few times to move between the TextBox, the EditBox, and
	  the two OptionGroup controls.
	
	6. Observe the output in the Accessible Event Watcher window. Note that when the
	  Optionbuttons have focus, the items on the toolbar will sometimes incorrectly
	  appear as if they have focus.
	
	OBJ_FOCUS	 Name="FORMTEXT1" Role=editable text State=focused,focusable
	OBJ_FOCUS	 Name="FORMEDIT1" Role=editable text State=focused,focusable
	OBJ_FOCUS	 Name="Toolbarcommand2" Role=push button State=focusable
	OBJ_FOCUS	 Name="Toolbarcommand4" Role=push button State=focusable
	
	If you repeat Step 4 after you close the toolbar, you receive the following
	results as expected:
	
	OBJ_FOCUS	 Name="FORMTEXT1" Role=editable text State=focused,focusable
	OBJ_FOCUS	 Name="FORMEDIT1" Role=editable text State=focused,focusable
	OBJ_FOCUS	 Name="Option1" Role=radio button State=focused,focusable
	OBJ_FOCUS	 Name="Option1" Role=radio button State=focused,focusable
	
	Additional query words:
	
	======================================================================
	Keywords          : kbGrpDSFox kbDSupport kbCodeSnippet kbvfp700 _IK283 kbVFP700sp1fix 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP700
	Version           : :7.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
