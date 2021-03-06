---
layout: page
title: "Q245699: Cannot Save RRAS Configuration After Upgrading to Service Pack 6"
permalink: /kb/245/Q245699/
---

## Q245699: Cannot Save RRAS Configuration After Upgrading to Service Pack 6

{% raw %}

	Article: Q245699
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0 SP6
	Operating System(s): 
	Keyword(s): kbui
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 SP6 
	- Microsoft Windows NT Server version 4.0 SP6 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you upgrade a computer running Windows NT Server and Routing and Remote
	Access Service (RRAS) to Windows NT Service Pack 6 (SP6), the RRAS configuration
	can no longer be saved. When you attempt to save an RRAS configuration by
	selecting Save Configuration from the Server menu drop down list, you receive
	the following error message:
	
	  An error occurred while backing up the configuration. The filename, directory
	  name, or volume label syntax is incorrect. If you are saving the
	  configuration of a remote computer, then the directory and drive in which you
	  are saving the configuration must exist on both the local and remote
	  computers.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Windows NT 4.0 service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English-language version of this fix should have the following file
	attributes or later:
	
	  Date        Time     Size      File name   Platform
	  ---------------------------------------------------
	  1/4/00      7:28PM   50,960    Mprapi.dll  Intel
	  1/4/00      7:32PM   81,680    Mprapi.dll  Alpha
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0 SP6.
	
	Additional query words: Configuration, Routing and RAS Admin, steelhead
	
	======================================================================
	Keywords          : kbui 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400sp6 kbWinNTS400sp6 kbWinNTS400search
	Version           : winnt:4.0 SP6
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
