---
layout: page
title: "Q167282: WD97: Equation Object Not Inserted at Insertion Point"
permalink: /kb/167/Q167282/
---

## Q167282: WD97: Equation Object Not Inserted at Insertion Point

{% raw %}

	Article: Q167282
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): kbgraphic kbole
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you insert an Equation Editor object, the object does not appear at the
	place where the insertion point is located.
	
	CAUSE
	=====
	
	By default, the Equation Editor object is inserted as a floating object. When an
	object has the Float Over Text property, it is inserted into the drawing layer.
	This feature allows you to precisely position the object by dragging it to the
	desired location.
	
	WORKAROUND
	==========
	
	Use one of the following methods to work around this behavior:
	
	Method 1. Insert the object as an inline (non-floating) object
	--------------------------------------------------------------
	
	1. Position the insertion point where you want to insert the object.
	
	2. On the Insert menu, click Object.
	
	3. Click to clear the Float Over Text check box.
	
	4. In the Object Type list, click Microsoft Equation 3.0, and then click OK.
	
	Method 2. Use the InsertEquation command
	----------------------------------------
	
	The InsertEquation command is a built-in Word command that inserts the Equation
	Editor object as an inline object by default. To do this:
	
	1. Position the insertion point where you want to insert the object.
	
	2. On the Tools menu, point to Macro, and then click Macros.
	
	3. In the Macros In drop-down list, click Word Commands.
	
	4. In the Macro list, click InsertEquation, and then click Run.
	
	  The Equation Editor appears. When you close the Equation Editor, the equation
	  object will be inserted at the insertion point.
	
	You can add the InsertEquation command to a menu, toolbar, or shortcut key. For
	more information about how to do this, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q155800 WD97: How to Customize, Create, and Restore Word Menus/Toolbars
	
	For more information about customizing toolbars, click the Office Assistant, type
	"customizing toolbars," click Search, and then click "Add a button to a
	toolbar."
	
	For more information about customizing menus, click the Office Assistant, type
	"customizing menus," click Search, and then click "Add a command or other item
	to a menu."
	
	For more information about assigning shortcut keys, click the Office Assistant,
	type "customizing shortcut keys," click Search, and then click "Assign shortcut
	keys to a command or other item."
	
	NOTE: If the Assistant is hidden, click the Office Assistant button on the
	Standard toolbar. If Word Help is not installed on your computer, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q120802 Office: How to Add/Remove a Single Office Program or Component
	
	Method 3 - Convert a floating object to an inline object
	--------------------------------------------------------
	
	When the object has already been inserted into the document as a floating object,
	convert it to an inline object using these steps:
	
	1. Right-click the object, and click Format Object on the menu that appears.
	
	2. Click the Position tab.
	
	3. Click to clear the Float Over Text check box.
	
	4. Click OK.
	
	  -or-
	
	5. Click once on the Equation object.
	
	6. Click Object on the Format menu.
	
	7. Click the Position tab.
	
	8. Click to clear the Float Over Text check box.
	
	9. Click OK.
	
	MORE INFORMATION
	================
	
	For more information about floating objects, please see the following articles
	in the Microsoft Knowledge Base:
	
	  Q155822 WD97: "Float Over Text" Check Box Checked If Paste Link Selected
	
	  Q157465 WD97: Can't See Field Codes for Some Objects
	
	  Q157773 WD97: Macro to Disable Float Over Text Property
	
	  Q163808 WD97: Picture Is Pasted as Float Over Text Not as Inline
	
	  Q161692 WD97: Problems With Float Over Text Objects
	
	  Q155804 WD97: Inserted Picture or Drawing Object Moves Down Page
	
	Additional query words: 97 word97 editor msapps
	
	======================================================================
	Keywords          : kbgraphic kbole 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:
	Hardware          : x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
