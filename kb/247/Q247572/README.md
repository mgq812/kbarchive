---
layout: page
title: "Q247572: Problems with AddSystem and Addsytemgui SMS Resource Kit Tools"
permalink: /kb/247/Q247572/
---

## Q247572: Problems with AddSystem and Addsytemgui SMS Resource Kit Tools

{% raw %}

	Article: Q247572
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0,2.0 SP1
	Operating System(s): 
	Keyword(s): kbenv kbtool kbsms200 kbsms200bug kbsms120 kbsms120bug
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The AddSystem and Addsytemgui utilities in the Systems Management Server (SMS)
	Resource Kit have the following problems:
	
	1. They are hard coded to create a DDR with the sitecode set to BER.
	
	2. They do not set and key properties on DDRAddxxx functions. Because of this,
	  if Addsytem is run again on the same computer, a duplicate resource is
	  created under SMS. Note that DDM has no way of checking if the resource
	  already exists.
	
	3. Addsytem sets some wrong properties in the DDR and misses some required ones.
	
	4. Operating System Name and Version property is hard coded to Microsoft Windows
	  NT Advanced Server 4.0. This should be set dependent on the operating system
	  installed (Windows NT Workstation 4.0, Windows NT Server 4.0, Windows NT
	  Advanced Server 4.0). This would permit the remote installation service to
	  act on operating system type if the administrator has set specific types to
	  be installed, such as workstations only, servers only, and so on.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Systems Management Server service pack that contains this fix.
	
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
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date       Time               Size    File name       Platform
	  --------------------------------------------------------------
	  12/20/1999 6:58PM             21 KB   AddSystem.exe   i386
	  3/1/2000   8:00PM             112 KB  Addsysgui.exe   i386
	  12/20/1999 6:58PM             9 KB    AddSystem.exe   alpha
	  3/1/2000   8:00PM             213 KB  Addsysgui.exe   alpha
	
	NOTE: Due to file dependencies, the most recent hotfix or feature that contains
	the above files may also contain additional files.
	
	To install the hotfix, replace the current files with the ones listed above.
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 2.0.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbenv kbtool kbsms200 kbsms200bug kbsms120 kbsms120bug 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1
	Version           : winnt:2.0,2.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
