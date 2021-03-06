---
layout: page
title: "Q129796: HOWTO: 32-Bit App Can Determine When a Shelled Process Ends"
permalink: /kb/129/Q129796/
---

## Q129796: HOWTO: 32-Bit App Can Determine When a Shelled Process Ends

{% raw %}

	Article: Q129796
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 4.0,6.0
	Operating System(s): 
	Keyword(s): kbtophit kbVBp kbVBp400 kbVBp600 kbDSupport
	Last Modified: 28-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Executing the Shell() function in a Visual Basic for Windows program starts
	another executable program asynchronously and returns control to the Visual
	Basic application. This shelled program continues to run independently of your
	application until the user closes it.
	
	However, if your Visual Basic application needs to wait for the shelled process
	to terminate, you could use the Windows API to poll the status of the
	application, but this is not a very efficient technique. The example in this
	article demonstrates a better way.
	
	A 16-bit application would use a completely different technique to accomplish the
	same effect.
	
	  For additional information, click the article number on the 16-bit process
	  below to view the article on the 16-bit process in the Microsoft Knowledge
	  Base:
	
	  Q96844 HOWTO: Determine When a Shelled Process Has Terminated
	
	MORE INFORMATION
	================
	
	The Win32 API has integrated functionality that enables an application to wait
	until a shelled process has completed. To use these functions, you need a handle
	to the shelled process. The easiest way to achieve this is to use the
	CreateProcess() API function to launch your shelled program rather than Visual
	Basic's Shell() function.
	
	Creating the Shelled Process
	----------------------------
	
	In a 32-bit application, you need to create an addressable process. To do this,
	use the CreateProcess() function to start your shelled application. The
	CreateProcess() function gives your program the process handle of the shelled
	process through one of its passed parameters.
	
	Waiting for the Shelled Process to Terminate
	--------------------------------------------
	
	Having used CreateProcess() to get a process handle, pass that handle to the
	WaitForSingleObject() function. This causes your Visual Basic application to
	suspend execution until the shelled process terminates.
	
	Getting the Exit Code from the Shelled Application
	--------------------------------------------------
	
	It was common for a DOS application to return an exit code indicating the status
	of the completed application. While Windows provides other ways to convey the
	same information, some applications only provide exit codes. Passing the process
	handle to the GetExitCodeProcess() API allows you to retrieve this information.
	
	Following are the steps necessary to build a Visual Basic for Windows program
	that uses the CreateProcess() function to execute the Windows Notepad
	(Notepad.exe) application. This code demonstrates how to use the Windows API
	CreateProcess() and WaitForSingleObject() functions to wait until a shelled
	process terminates before resuming execution. It also uses the
	GetExitCodeProcess() function to retrieve the exit code of the shelled process,
	if any.
	
	
	The syntax of the CreateProcess() function is extremely complicated, so in the
	example code, it is encapsulated into a function called ExecCmd(). ExecCmd()
	takes one parameter, the command line of the application to execute.
	
	Step-by-Step Example
	--------------------
	
	1. Start a new project in Visual Basic. Form1 is created by default.
	
	2. Add the following code to the General Declarations section of Form1:
	
	     Private Type STARTUPINFO
	        cb As Long
	        lpReserved As String
	        lpDesktop As String
	        lpTitle As String
	        dwX As Long
	        dwY As Long
	        dwXSize As Long
	        dwYSize As Long
	        dwXCountChars As Long
	        dwYCountChars As Long
	        dwFillAttribute As Long
	        dwFlags As Long
	        wShowWindow As Integer
	        cbReserved2 As Integer
	        lpReserved2 As Long
	        hStdInput As Long
	        hStdOutput As Long
	        hStdError As Long
	     End Type
	
	     Private Type PROCESS_INFORMATION
	        hProcess As Long
	        hThread As Long
	        dwProcessID As Long
	        dwThreadID As Long
	     End Type
	
	     Private Declare Function WaitForSingleObject Lib "kernel32" (ByVal _
	        hHandle As Long, ByVal dwMilliseconds As Long) As Long
	
	     Private Declare Function CreateProcessA Lib "kernel32" (ByVal _
	        lpApplicationName As String, ByVal lpCommandLine As String, ByVal _
	        lpProcessAttributes As Long, ByVal lpThreadAttributes As Long, _
	        ByVal bInheritHandles As Long, ByVal dwCreationFlags As Long, _
	        ByVal lpEnvironment As Long, ByVal lpCurrentDirectory As String, _
	        lpStartupInfo As STARTUPINFO, lpProcessInformation As _
	        PROCESS_INFORMATION) As Long
	
	     Private Declare Function CloseHandle Lib "kernel32" _
	        (ByVal hObject As Long) As Long
	
	     Private Declare Function GetExitCodeProcess Lib "kernel32" _
	        (ByVal hProcess As Long, lpExitCode As Long) As Long
	
	     Private Const NORMAL_PRIORITY_CLASS = &H20&
	     Private Const INFINITE = -1&
	
	     Public Function ExecCmd(cmdline$)
	        Dim proc As PROCESS_INFORMATION
	        Dim start As STARTUPINFO
	
	        ' Initialize the STARTUPINFO structure:
	        start.cb = Len(start)
	
	        ' Start the shelled application:
	        ret& = CreateProcessA(vbNullString, cmdline$, 0&, 0&, 1&, _
	           NORMAL_PRIORITY_CLASS, 0&, vbNullString, start, proc)
	
	        ' Wait for the shelled application to finish:
	           ret& = WaitForSingleObject(proc.hProcess, INFINITE)
	           Call GetExitCodeProcess(proc.hProcess, ret&)
	           Call CloseHandle(proc.hThread)
	           Call CloseHandle(proc.hProcess)
	           ExecCmd = ret&
	     End Function
	
	     Sub Form_Click()
	        Dim retval As Long
	        retval = ExecCmd("notepad.exe")
	        MsgBox "Process Finished, Exit Code " & retval
	     End Sub
	
	3. Press the F5 key to run the application.
	
	4. Using the mouse, click the Form1 window. At this point the NotePad
	  application is started.
	
	5. Quit NotePad. A MsgBox appears indicating termination of the NotePad
	  application and an exit code of 0.
	
	  NOTE: The MsgBox statement following the ExecCmd() function is not executed
	  because the WaitForSingleObject() function prevents it. The message box does
	  not appear until Notepad is closed when the user chooses Exit from Notepad's
	  File menu (ALT, F, X).
	
	REFERENCES
	==========
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q288216 PRB: Call to ExitProcess() from Visual Basic Application Hinders
	  Process Exit
	
	For more information, please see the "CreateProcess" topic in the MSDN Library
	CD-ROM.
	
	Additional query words: GetModuleUsage
	
	======================================================================
	Keywords          : kbtophit kbVBp kbVBp400 kbVBp600 kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600 kbVB400Search kbVB400
	Version           : :4.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
