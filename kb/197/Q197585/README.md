---
layout: page
title: "Q197585: HOWTO: Cover the Taskbar with a Window in Visual Basic"
permalink: /kb/197/Q197585/
---

## Q197585: HOWTO: Cover the Taskbar with a Window in Visual Basic

{% raw %}

	Article: Q197585
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbAPI kbGrpDSUser kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Windows taskbar has an AutoHide property that allows it to hide at the very
	edge of the screen, taking up very little space, until the mouse is positioned
	directly over it, which causes it reappear at it's normal size. When you set the
	AutoHide property, a maximized window covers the entire screen. If you do not
	set the AutoHide property, a maximized window covers the entire screen except
	for the area occupied by the taskbar.
	
	MORE INFORMATION
	================
	
	There is no programmatic way to change the AutoHide property in Microsoft
	Windows. To size a Visual Basic form so that it fills the entire screen,
	including covering the taskbar if it is showing, you must explicitly set the
	height and width of the window.
	
	In the following sample code, the SetWindowPos API enables the specified window
	to cover the entire screen, including covering all taskbars. This or any similar
	approach only works if the window is not already maximized. If the window is
	currently maximized, you must first set the window to a restored/normal state
	prior to using the SetWindowPos API.
	
	Step-by-Step Procedures
	-----------------------
	
	1. Create a new Standard EXE project. Form1 is created by default.
	
	2. Add a CommandButton to Form1.
	
	3. Paste the following code into Form1's code window:
	
	        Private Sub Command1_Click()
	           Dim cx As Long
	           Dim cy As Long
	           Dim RetVal As Long
	
	           ' Determine if screen is already maximized.
	           If Me.WindowState = vbMaximized Then
	              ' Set window to normal size
	              Me.WindowState = vbNormal
	           End If
	
	           ' Get full screen width.
	           cx = GetSystemMetrics(SM_CXSCREEN)
	
	           ' Get full screen height.
	           cy = GetSystemMetrics(SM_CYSCREEN)
	
	           ' Call API to set new size of window.
	           RetVal = SetWindowPos(Me.hwnd, HWND_TOP, 0, 0, cx, cy, _
	              SWP_SHOWWINDOW)
	        End Sub
	
	4. Add a standard module to the Project menu.
	
	5. Paste the following code into the module:
	
	        Declare Function SetWindowPos Lib "user32" (ByVal hwnd As Long, _
	           ByVal hWndInsertAfter As Long, ByVal x As Long, ByVal y As Long, _
	           ByVal cx As Long, ByVal cy As Long, ByVal wFlags As Long) As Long
	
	        Declare Function GetSystemMetrics Lib "user32" _
	           (ByVal nIndex As Long) As Long
	
	        Public Const SM_CXSCREEN = 0
	        Public Const SM_CYSCREEN = 1
	        Public Const HWND_TOP = 0
	        Public Const SWP_SHOWWINDOW = &H40
	
	6. Run the project.
	
	7. Click the CommandButton.
	
	RESULT: The form will cover the entire screen, including any taskbars.
	
	This works for all taskbars on the primary monitor, including the shell's taskbar
	and any other taskbars (such as the Microsoft Office taskbar) that are written
	to use the standard Desktop Application Toolbar interface.
	
	REFERENCES
	==========
	
	For information on how to do this in C/C++, please see the following article in
	the Microsoft Knowledge Base:
	
	  Q179363 : HOWTO: Cover the Task Bar with a Window
	
	
	The code in this article can easily be adapted to work with the sample code found
	in the following article in the Microsoft Knowledge Base:
	
	  Q161299 : HOWTO: Capture and Print the Screen, a Form, or any Window
	
	Additional query words: tray auto hide autohide properties
	
	======================================================================
	Keywords          : kbAPI kbGrpDSUser kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400
	Version           : WINDOWS:4.0,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
