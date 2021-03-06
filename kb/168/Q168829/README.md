---
layout: page
title: "Q168829: HOWTO: Get a Hierarchical List of Window Names and Classes"
permalink: /kb/168/Q168829/
---

## Q168829: HOWTO: Get a Hierarchical List of Window Names and Classes

{% raw %}

	Article: Q168829
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVBDB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Access for Windows 95, version 7.0 
	- Microsoft Access 97 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When trying to determine whether a child window of an application is open, you
	need to know whether it is a child of the main application window, a grandchild,
	or an independent window. This article provides a method of creating a
	hierarchical listing of all currently open windows and their window class names,
	making it easier navigating a program's window hierarchy.
	
	MORE INFORMATION
	================
	
	WARNING: Microsoft provides code examples for illustration only, without
	warranty either expressed or implied, including but not limited to the implied
	warranties of merchantability and/or fitness for a particular purpose. This code
	is provided 'as is' and Microsoft does not guarantee that the following code can
	be used in all situations. Microsoft does not support modifications of the code
	to suit customer requirements for a particular purpose.
	
	Step-by-Step Example
	--------------------
	
	1. Create a new project with a Form and a Module.
	
	2. Add the following controls to the form:
	
	  Control            Name         Property   Value
	  ------------------------------------------------
	  Command button     Command1
	  Text box           Text1        MultiLine  TRUE
	  Text box           Text1        Scrollbars 2- Vertical
	
	  NOTE: The MultiLine property only applies to Visual Basic.
	
	3. Type the following code into the module:
	
	        Option Explicit
	
	        Public Const GW_CHILD = 5
	        Public Const GW_HWNDNEXT = 2
	
	        Declare Function GetWindow Lib "user32" (ByVal hwnd As Long, _
	                ByVal wCmd As Long) As Long
	        Declare Function GetWindowText Lib "user32" Alias "GetWindowTextA" _
	                (ByVal hwnd As Long, ByVal lpString As String, _
	                ByVal cch As Long) As Long
	        Declare Function GetTopWindow Lib "user32" _
	                (ByVal hwnd As Long) As Long
	        Declare Function GetClassName Lib "user32" Alias "GetClassNameA" _
	                (ByVal hwnd As Long, ByVal lpClassName As String, _
	                ByVal nMaxCount As Long) As Long
	
	4. Add the following code to the form's module:
	
	        Sub AddChildWindows(ByVal hwndParent As Long, ByVal Level As Long)
	        Dim WT As String, CN As String, Length As Long, hwnd As Long
	          If Level = 0 Then
	            hwnd = hwndParent
	          Else
	            hwnd = GetWindow(hwndParent, GW_CHILD)
	          End If
	          Do While hwnd <> 0
	            WT = Space(256)
	            Length = GetWindowText(hwnd, WT, 255)
	            WT = Left$(WT, Length)
	            CN = Space(256)
	            Length = GetClassName(hwnd, CN, 255)
	            CN = Left$(CN, Length)
	            Me!Text1 = Me!Text1 & vbCrLf & String(2 * Level, ".") _
	                     & WT & " (" & CN & ")"
	            AddChildWindows hwnd, Level + 1
	            hwnd = GetWindow(hwnd, GW_HWNDNEXT)
	          Loop
	        End Sub
	
	        Sub Command1_Click()
	        Dim hwnd As Long
	          hwnd = GetTopWindow(0)
	          If hwnd <> 0 Then
	            AddChildWindows hwnd, 0
	          End If
	        End Sub
	
	5. Visual Basic only: Run the project.
	
	  Access only: Open the form.
	
	6. Click the CommandButton. The text box will be filled with a list of windows
	  and their children arranged in a hierarchical order. The class name will
	  follow the window name, such as:
	
	     MainWindowName (WindowClass)
	     ..ChildWindowName (WindowClass)
	     ....GrandchildWindowName (WindowClass)
	
	NOTE: Not all windows will have a name but all will have a Window Class.
	
	REFERENCES
	==========
	
	Microsoft Windows SDK
	
	Additional query words: kbVBp500 kbVBp600 kbdse kbDSupport kbVBp kbWinAPI
	
	======================================================================
	Keywords          : kbGrpDSVBDB 
	Technology        : kbVBSearch kbAudDeveloper kbAccessSearch kbZNotKeyword6 kbAccess97 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbAccess97Search kbAccess95Search kbVB400Search kbVB400 kbZNotKeyword3 kbAccess700
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
