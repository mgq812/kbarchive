---
layout: page
title: "Q173773: HOWTO: Move a Form that Has No Title Bar (32-Bit)"
permalink: kb/173/Q173773/
---

## Q173773: HOWTO: Move a Form that Has No Title Bar (32-Bit)

	Article: Q173773
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbnetwork kbnokeyword kbAPI kbSDKPlatform kbVBp500 kbVBp600 kbGrpDSVB kbGrpDSNet
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Control Creation Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article demonstrates how to move a form with the mouse when the form has no
	title bar by using the 32-bit Windows API SendMessage function with the
	WM_NCLBUTTONDOWN message.
	
	MORE INFORMATION
	================
	
	The WM_NCLBUTTON message is generated by Windows when a user right-clicks on a
	window's title bar. Windows uses this message to determine whether the window
	should be moved by further user actions. If the title bar does not exist, this
	message is not generated. However, it is often useful to move a window when it
	doesn't have a title bar. A window or form in 32-bit Visual Basic will not have
	a title bar under the following circumstances:
	
	  Visual Basic 5.0 and Visual Basic 6.0
	     Caption = ""
	     ControlBox = False
	
	  Visual Basic 4.0
	     Caption = ""
	     ControlBox = False
	     MaxButton = False
	     MinButton = False
	
	The sample code below illustrates a way of letting users move a form without a
	title bar by simply clicking and dragging it from anywhere on the form. The code
	placed in the MouseMove event procedure of Form1 may be placed in other event
	procedures, if so desired. For example, the code could be placed in the
	MouseDown event procedure of a Label control allowing movement of the form by
	selecting and dragging from the Label control.
	
	NOTE: In Visual Basic 4.0, a form with a menu will have the title bar supplied by
	default so the method demonstrated below is not necessary. In Visual Basic 5.0
	and Visual Basic 6.0, a form with a menu will not have a title bar supplied by
	default.
	
	Step-By-Step Example
	--------------------
	
	1. Start a new Standard EXE project. Form1 is added by default.
	
	2. Set Form1's ControlBox, MinButton, and MaxButton properties to False, and
	  then clear its Caption.
	
	3. Place a CommandButton control (Command1) on Form1.
	
	4. Place the following code in the General Declarations section of Form1:
	
	        Private Declare Function SendMessage Lib "User32" _
	                           Alias "SendMessageA" (ByVal hWnd As Long, _
	                                                 ByVal wMsg As Long, _
	                                                 ByVal wParam As Long, _
	                                                 lParam As Any) As Long
	
	        Private Declare Sub ReleaseCapture Lib "User32" ()
	
	        Const WM_NCLBUTTONDOWN = &HA1
	        Const HTCAPTION = 2
	
	        Private Sub Form_Load()
	           Command1.Caption = "Exit"
	        End Sub
	
	        Private Sub Form_MouseMove(Button As Integer, Shift As Integer, _
	                                   X As Single, Y As Single)
	           Dim lngReturnValue As Long
	
	           If Button = 1 Then
	              Call ReleaseCapture
	              lngReturnValue = SendMessage(Form1.hWnd, WM_NCLBUTTONDOWN, _
	                                           HTCAPTION, 0&)
	           End If
	        End Sub
	
	        Private Sub Command1_Click()
	           End
	        End Sub
	
	5. Press the F5 key to run the program. Clicking and holding over Form1 will
	  allow you to move the form. Pressing the CommandButton control will exit the
	  program.
	
	REFERENCES
	==========
	
	For information on how to move a form without a title bar in 16-bit versions of
	Visual Basic, please see the following article in the Microsoft Knowledge Base:
	
	  Q114593 : HOWTO: Move a Form that Has No Titlebar or Caption
	
	======================================================================
	Keywords          : kbnetwork kbnokeyword kbAPI kbSDKPlatform kbVBp500 kbVBp600 kbGrpDSVB kbGrpDSNet 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400 kbZNotKeyword3
	Hardware          : x86
	Issue type        : kbhowto
	
	=============================================================================
	