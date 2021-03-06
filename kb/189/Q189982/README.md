---
layout: page
title: "Q189982: PRB: Error 429 When Trying to Access an MTS Component"
permalink: /kb/189/Q189982/
---

## Q189982: PRB: Error 429 When Trying to Access an MTS Component

{% raw %}

	Article: Q189982
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 2.0,5.0
	Operating System(s): 
	Keyword(s): kbVBp500 kbGrpDSVBDB
	Last Modified: 01-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	- Microsoft Transaction Server 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When running a Visual Basic client for a Microsoft Transaction Server (MTS)
	component on the server on which MTS is running, you may get the following error
	message:
	
	  "Run-time error '429': ActiveX component can't create object."
	
	CAUSE
	=====
	
	You may have run the MTS remote client setup EXE on the server computer.
	
	RESOLUTION
	==========
	
	Do not run the MTS remote client setup EXE on the server computer.
	
	If you have already run the MTS remote client setup EXE on the server, you must
	remove the remote client files. In order to do this:
	
	1. From the server's Taskbar, select Start, Settings, Control Panel.
	
	2. Open Add/Remove Programs.
	
	3. Select the "Remote Application" entry that corresponds to your MTS component,
	  and then click Add/Remove.
	
	  You can then use the Transaction Server Explorer to remove and reinstall the
	  component from the package that will correct the problem.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	The server's registry is updated when you compile your Visual Basic ActiveX DLL
	project. The server's registry is also updated when you install the compiled
	ActiveX DLL into an MTS package. Once you have installed the ActiveX DLL into
	the MTS package, you may run the client application on the server.
	
	To allow a remote client to run the client application, use the Export utility in
	MTS to export the package information from MTS. This can be done by select the
	package in the MTS Explorer, right-mouse clicking and choosing the Export
	option. When you Export the package from MTS, MTS creates a remote client setup
	EXE. Copy this remote client setup EXE from the server to the remote machine and
	run the remote client setup. Now the remote client application will be able to
	access the remote MTS component on the server.
	
	You do not need to run the remote client setup EXE on the server. The remote
	component setup updates a system's registry to act as a remote client. The
	remote client setup EXE should never be run on the server where the MTS
	component is hosted.
	
	The Microsoft Knowledge Base article Q186342 mentioned in the REFERENCES section
	below contains complete information on creating a Visual Basic database
	application that uses components installed under Microsoft Transaction Server.
	Please refer to that article for more detailed instructions on installing a
	package into MTS and creating remote client setup files.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create the server component. This is an ActiveX DLL written in Visual Basic.
	
	2. Create the client application. This is a standard EXE written in Visual
	  Basic.
	
	3. Install the server component into a MTS package. You are now able to run the
	  client application on the server.
	
	4. Set up the client computers. You are now able to run the client application
	  on the remote clients.
	
	5. Run the remote client setup EXE on the server. When you run the client
	  application on the server, you get "Run-time error '429': ActiveX component
	  can't create object." The remote clients are also unable to run the client
	  application.
	
	6. To remove the client files from the server:
	
	  a. From the server's Taskbar, select Start, Settings, Control Panel.
	
	  b. Open Add/Remove Programs.
	
	  c. Select the "Remote Application" entry that corresponds to your MTS
	     component, and then click Add/Remove.
	
	7. Remove and reinstall the server component into an MTS package. You should now
	  be able to run the client application on the server and on the remote
	  clients.
	
	REFERENCES
	==========
	
	MTS 2.0 Online Help
	
	For information on creating a Visual Basic database application which uses
	components installed under Microsoft Transaction Server, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q186342 : HOWTO: Create a 3-Tier App Using VB, MTS and SQL Server
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q177394 : HOWTO: Troubleshoot Run-Time Error '429' in DCOM Applications
	
	  Q269330 HOWTO: Troubleshoot DCOM for Visual Basic Client/Server Applications
	
	Additional query words: kbMTSExplorer kbMTS200 kbDCOM kbDSupport kbdse kbVBp500 kbVBp600 kbVBp
	
	======================================================================
	Keywords          : kbVBp500 kbGrpDSVBDB 
	Technology        : kbVBSearch kbMTSsearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB500 kbMTS200
	Version           : :2.0,5.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
