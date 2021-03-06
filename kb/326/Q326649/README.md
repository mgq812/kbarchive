---
layout: page
title: "Q326649: Changes in COMTI Regions (TOR or AOR) Cause Some COMTI Applicati"
permalink: /kb/326/Q326649/
---

## Q326649: Changes in COMTI Regions (TOR or AOR) Cause Some COMTI Applicati

{% raw %}

	Article: Q326649
	Product(s): Microsoft SNA Server
	Version(s): 4.0 SP4
	Operating System(s): 
	Keyword(s): 
	Last Modified: 14-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Host Integration Server 2000 
	- Microsoft SNA Server, version 4.0 SP4 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	After you upgrade COM Transaction Integrator (COMTI) to SNA Server version 4.0
	Service Pack (SP) 4 or to Host Integration Server 2000, COMTI applications that
	use Customer Information Control System (CICS) LINK over logical unit (LU) 6.2
	with SNA Server 4.0 SP 3 or earlier may not communicate correctly with the host
	transaction program.
	
	CAUSE
	=====
	
	On a mainframe computer that has CICS installed, terminals that are connected to
	one CICS region (a Terminal Owning Region [TOR]) can run transactions on another
	CICS region (an Application Owning Region [AOR]).
	
	With versions earlier than SNA Server 4.0 SP 4, if the program that is being
	called is to be run in an AOR, COMTI always passes the default CICS mirror
	transaction ID to the AOR.
	
	In SNA Server 4.0 SP 4 and Host Integration Server 2000, COMTI always passes the
	Source TP Name that is on the Host Names tab of the Method Properties in the
	COMTI Component Builder as the mirror transaction ID that is to be used by the
	AOR.
	
	Because of this change, COMTI applications that rely on COMTI to pass the default
	CICS mirror transaction ID to the AOR do not work correctly after COMTI is
	upgraded to SNA Server 4.0 SP 4 or to Host Integration Server 2000.
	
	RESOLUTION
	==========
	
	SNA Server 4.0 SP 4
	-------------------
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Apply it only to
	computers that are experiencing this specific problem. This fix may receive
	additional testing. Therefore, if you are not severely affected by this problem,
	Microsoft recommends that you wait for the next Microsoft SNA Server 4.0 SP 4
	that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, visit the following Microsoft
	Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The typical support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The English version of this fix has the file attributes (or later) that are
	listed in the following table. The dates and times for these files are listed in
	coordinated universal time (UTC). When you view the file information, it is
	converted to local time. To find the difference between UTC and local time, use
	the Time Zone tab in the Date and Time tool in Control Panel.
	
	  Date         Time   Version      Size    File name
	  --------------------------------------------------
	  NOV-05-2001  11:29  4.993.0.0   54,447   Dpl1.dll
	  NOV-05-2001  11:48  4.993.0.0  133,015   TranLU62.dll
	
	NOTE: Because of file dependencies, the most recent fix that contains the above
	files may also contain additional files.
	
	
	
	Host Integration Server 2000
	----------------------------
	
	No fix is available at this time.
	
	
	WORKAROUND
	==========
	
	To work around this problem, follow these steps:
	
	1. Use the COMTI Component Builder to change the Source TP Name of each method
	  to CSMI.
	
	2. Save and redeploy the COMTI component.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	This fix implements a registry key so that COMTI works as it did in SNA Server
	4.0 SP 3 and earlier. When this key exists and is set to a value, COMTI always
	passes the default CICS mirror transaction ID (CSMI) to the AOR.
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate and then click the following key in the registry:
	
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cedar\Defaults
	
	3. On the Edit menu, click Add Value, and then add the following registry value:
	
	  Value name: SourceTPNameOverride
	  Data type: REG_SZ
	  Value data: True
	
	  NOTE: The actual data value is not checked, but you must enter a data value.
	
	4. Quit Registry Editor.
	
	For additional information about the change in COMTI behavior between SP 3 and SP
	4 of SNA Server 4.0 and Host Integration Server 2000, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q275864 COMTI TOR/AOR Changes
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbHostIntegServ2000 kbSNAServ400SP4
	Version           : :4.0 SP4
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
