---
layout: page
title: "Q310127: SMS: Operating System Appears as &quot;Windows 9x&quot; at Parent Site"
permalink: /kb/310/Q310127/
---

## Q310127: SMS: Operating System Appears as &quot;Windows 9x&quot; at Parent Site

{% raw %}

	Article: Q310127
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): kbenv kbnetwork kbtool kbui kbsms200 kbsms200bug kbDiscovery
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In a Systems Management Server (SMS) implementation where a child primary site
	reports to a primary site, the operating system that is shown in the discovery
	data for clients that are running one of the following operating systems may
	appear as "Microsoft Windows 9x" at the parent site:
	
	- Microsoft Windows Millennium Edition (Me)
	
	- Microsoft Windows 98
	
	- Microsoft Windows 95
	
	However, the same client record at the child primary site shows a more accurate
	and complete description of the operating system, for example, "Microsoft
	Windows 98".
	
	CAUSE
	=====
	
	When network discovery defines a client's operating system as "Microsoft Windows
	9x", it flags this as a "low confidence" value in the discovery data record so
	that a more accurate value (if it exists ) won't be overwritten in the database.
	This works very well in a single site hierarchy.
	
	When discovery data is forwarded to another primary site (parent site), the
	Discovery Data Manager component combines the new discovery data with the data
	that already exists in the database and sends this combined data to the parent
	site.
	
	When the data is combined, the Discovery Data Manager ignores the "low
	confidence" flag and sends the "Microsoft Windows 9x" value to the parent site.
	Because this discovery data record does not have the "low confidence" flag set,
	the more accurate operating system value is overwritten.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Only apply it to systems
	that are experiencing this specific problem. This fix may receive additional
	testing. Therefore, if you are not severely affected by this problem, Microsoft
	recommends that you wait for the next Systems Management Server service pack
	that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, visit the following Microsoft
	Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The usual support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The SMS 2.0 post-Service Pack 3 version of this fix should have the following
	file attributes or later:
	
	  Date         Time   Version         Size       File name    Platform
	  --------------------------------------------------------------------
	  03-Mar-2001  15:15  2.00.1493.3203  2,429,712  Basesvr.dll  Alpha
	  03-Mar-2001   9:30  2.00.1493.3143    126,224  Cmprov.dll   Alpha
	  03-Mar-2001  22:30  2.00.1493.3182    171,792  Compmgr.exe  Alpha
	  03-Mar-2001  15:15  2.00.1493.3203  1,578,912  Basesvr.dll  Intel
	  03-Mar-2001   9:30  2.00.1493.3143     81,040  Cmprov.dll   Intel
	  03-Mar-2001  22:30  2.00.1493.3182    121,440  Compmgr.exe  Intel
	
	NOTE: Due to file dependencies, the most recent hotfix or feature that contains
	the above files may also contain additional files.
	
	
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article. This problem was first corrected in
	the Systems Management Server 2.0 Service Pack 4 Hotfix Rollup Package (HRP).
	
	For additional information about the SMS 2.0 SP4 HRP, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q323206 SMS: List of Bugs Fixed in the Systems Management Server 2.0 SP4 HRP
	
	MORE INFORMATION
	================
	
	When network discovery is run in an environment where some SMS clients run one
	of the following operating systems, the network discovery record for each of
	these clients shows the operating system as "Microsoft Windows 9x":
	
	- Microsoft Windows Millennium Edition (Me)
	
	- Microsoft Windows 98
	
	- Microsoft Windows 95
	
	This occurs because network discovery cannot access a computer that is running
	one of these operating systems to determine the specific operating system
	information unless file and print sharing is enabled.
	
	In a single-tiered environment, this does not present a problem for computers
	that are SMS clients because the heartbeat discovery record (which is generated
	immediately upon client installation and at periodic intervals thereafter) does
	identify the more specific operating system version, and then reports it
	correctly to the database. Later, if network discovery again reports "Microsoft
	Windows 9x" as the operating system, the entry is ignored because more specific
	information is already present.
	
	In a hierarchy with two or more tiers, when network discovery is run at a child
	primary site and that child site has Windows Me/98/95 clients installed,
	everything proceeds as previously described, except that the discovery records
	are then forwarded to the parent site. In this situation, the clients of the
	child site which appear in the parent site's database can have a more accurate
	operating system value such as "Microsoft Windows 98" overwritten with the less
	accurate value of "Microsoft Windows 9x".
	
	An administrator can see the client's discovery data at the central site
	fluctuate between these two operating system values depending on which type of
	discovery data record was last processed for the client.
	
	Because of a dependency between DLLs, this hotfix includes the hotfix for the
	problem that is described in the following Microsoft Knowledge Base article:
	
	  Q299435 Cannot Run SMS Service Manager After You Apply a Hotfix
	
	Hotfix Installation Instructions
	--------------------------------
	
	Apply the fix in this article to all primary sites in the SMS hierarchy by using
	one of the following methods.
	
	How to Use the Hotfix Installer:
	
	NOTE: You can use this method only on Intel-based computers.
	
	1. Copy the hotfix folder structure to a share on your network. Note that
	  Q310127.exe is a Microsoft SMS Installer file that updates specific files on
	  your site server.
	
	2. Log on to the site server by using an account with administrative privileges.
	
	3. On the site server, close the SMS Administrator console and the SMS Service
	  Manager.
	
	4. Run the Q310127.exe tool, and then follow the directions in the wizard. You
	  can run the file in Quiet mode by using the "/S" (without the quotation
	  marks) switch.
	
	How to Manually Install the Hotfix:
	
	1. On the site server, close the SMS Administrator console and the SMS Service
	  Manager.
	
	2. Stop the SMS Site Component Manager, SMS Executive, Windows Management, and
	  SMS SQL Monitor services on the site server.
	
	3. Replace the Basesvr.dll file in the
	  <Sms_root_folder>\Bin\<Platform> folder with the version of the
	  file that is included with the hotfix.
	
	4. Replace the Cmprov.dll file in the
	  <Sms_root_folder>\Bin\<Platform> folder with the version of the
	  file that is included with the hotfix.
	
	5. Replace the Compmgr.exe file in the
	  <Sms_root_folder>\Bin\<Platform> folder with the version of the
	  file that is included with the hotfix.
	
	6. Restart the SMS Site Component Manager, SMS Executive, Windows Management,
	  and SMS SQL Monitor services.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbenv kbnetwork kbtool kbui kbsms200 kbsms200bug kbDiscovery 
	Technology        : kbSMSSearch kbSMS200
	Version           : :2.0
	Hardware          : x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
