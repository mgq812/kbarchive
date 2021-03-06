---
layout: page
title: "Q199035: PRB: Solution and Web Files Are Added to Different Databases"
permalink: /kb/199/Q199035/
---

## Q199035: PRB: Solution and Web Files Are Added to Different Databases

{% raw %}

	Article: Q199035
	Product(s): Microsoft SourceSafe
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbFrontPage kbSSafe kbVisID600 kbGrpDSASP kbDSupport
	Last Modified: 03-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, version 6.0 
	- Microsoft Visual InterDev, version 6.0 
	- Microsoft Visual Studio 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When adding a Visual Studio solution (.sln file) that contains a Web project to
	Visual SourceSafe (VSS), the .sln file and the project files are added to
	different VSS databases.
	
	CAUSE
	=====
	
	The .sln file and the Web project use different mechanisms for SourceSafe
	integration. The .sln file uses the same mechanism as other Visual Studio
	components, such as Visual Basic and Visual C++. Visual InterDev uses the
	FrontPage Server Extensions (FPSE), which in turn interact with VSS through OLE
	automation. This mechanism determines which database the Web files are added to.
	It is important to note that all VSS operations on the Web files are done on the
	IIS server machine, not on Visual InterDev clients.
	
	RESOLUTION
	==========
	
	To resolve this problem, first identify which VSS database is being used by
	FPSE, then ensure that the .sln file is added to that database. For most users
	the best option will be to create a workstation installation of VSS on the
	client machine by running VSS's netsetup from the database used by the Internet
	Information Server machine.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Both integration methods "decide" which VSS database to use by finding a copy of
	the Srcsafe.ini file.
	
	Under normal circumstances FPSE will use the Srcsafe.ini that is in the directory
	above the Ssapi.dll file on the IIS server (Ssapi.dll is in the VSS\win32
	directory). If there are multiple copies of Ssapi.dll on the server, it will use
	the copy that is registered. In this situation you can run Regsvr32 <path to
	ssapi.dll> to register the desired copy. The registry key
	
	  HKEY_CLASSES_ROOT\CLSID\{783CD4E4-9D54-11CF-B8EE-00608CC9A71F}\InprocServer32
	
	shows which version of Ssapi.dll is currently registered.
	
	
	The database used for the .sln file is determined by the VSS settings on the
	client machine. First it looks at the following registry key
	
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\Current Database
	
	If this key is not set, it will then look at the path to the Ssscc.dll in the
	key
	
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath,
	
	and use the Srcsafe.ini file in the parent directory of that path.
	
	Unlike the FPSE mechanism, you can interactively choose which database will be
	used for the .sln file. In the Visual Studio IDE select Options from the Tools
	menu, then in the Environment ... Source Control section of the Options dialog
	box, click Advanced . Select the Integration tab of the SourceSafe Options
	dialog box, under Choose SourceSafe Database, select Prompt.
	
	Steps to Reproduce Behavior
	---------------------------
	
	The following steps assume that there are two server installations of VSS on the
	IIS server in \VSS1 and \VSS2 subdirectories, and that VSS2 was installed last
	(hence, its copy of Ssapi.dll is registered).
	
	1. On a client machine run Netsetup from the server's \VSS1 directory.
	
	2. On that client machine, use VI to create new Web project on the IIS server.
	
	3. In the Project Explorer, select the Solution and select Project ... Source
	  Control ... Add to Source Control. When prompted, select to add the whole
	  solution
	
	4. You will first be prompted to specify which project you are adding the
	  solution to. Note that this is for the .sln file only and by default it is
	  pointing to VSS1. You may receive an additional dialog box prompting you to
	  add the .sln file.
	
	5. After completing the above operation, you will receive another dialog box
	  with the title Enable Source Control. This is using the FPSE mechanism to add
	  the Web to VSS. After clicking OK, the Web will be added to the VSS2
	  database.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbFrontPage kbSSafe kbVisID600 kbGrpDSASP kbDSupport 
	Technology        : kbVSsearch kbVisIDsearch kbSSafeSearch kbAudDeveloper kbVisID600 kbSSafe600 kbVS600 kbVS600Search
	Version           : WINDOWS:6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
