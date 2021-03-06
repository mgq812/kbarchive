---
layout: page
title: "Q173962: Anonymous Acct. Not Created When Windows NT 4.0 &amp; IIS Are on BDC"
permalink: /kb/173/Q173962/
---

## Q173962: Anonymous Acct. Not Created When Windows NT 4.0 &amp; IIS Are on BDC

{% raw %}

	Article: Q173962
	Product(s): Internet Information Server
	Version(s): WinNT:1.0,2.0,3.0
	Operating System(s): 
	Keyword(s): kbinterop kbsetup
	Last Modified: 16-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Active Server Pages 
	- Microsoft Internet Information Server versions 2.0, 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you setup Active Server Pages (ASP) on a backup domain controller (BDC),
	you will get an error message that the IUSR account is improperly setup.
	
	CAUSE
	=====
	
	During the setup of Microsoft Windows NT Server version 4.0 and Internet
	Information Server (IIS), the IUSR account cannot be created because the Windows
	NT installation does not have network connectivity to create the IUSR account in
	the domain account database.
	
	WORKAROUND
	==========
	
	Uninstall and re-setup IIS on the BDC. Then set up ASP.
	
	MORE INFORMATION
	================
	
	This is referenced in the Readme.txt that comes with ASP.
	
	======================================================================
	Keywords          : kbinterop kbsetup 
	Technology        : kbiisSearch kbAudDeveloper kbASPsearch kbiis300 kbiis200
	Version           : WinNT:1.0,2.0,3.0
	Hardware          : ALPHA x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
