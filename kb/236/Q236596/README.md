---
layout: page
title: "Q236596: SMS: Client Components Fail to Install with SMS 2.0 SP1"
permalink: /kb/236/Q236596/
---

## Q236596: SMS: Client Components Fail to Install with SMS 2.0 SP1

{% raw %}

	Article: Q236596
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0
	Operating System(s): 
	Keyword(s): kbsms200 kbsms200bug kbsms200sp2fix
	Last Modified: 25-JUN-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Systems Management Server 2.0 client component installation may fail after
	applying Systems Management Server 2.0 Service Pack 1 if all of the following
	conditions are true:
	
	- Multiple Systems Management Server 2.0 sites share the same Windows NT
	  domain.
	
	- At least one of the sites in this hierarchy has been upgraded.
	
	- The client being installed belongs to a site that has not been upgraded yet.
	
	Looking at the %Windir%\Ms\Sms\Logs\Ccim32.log file on the client, you may see
	entries similar to the following:
	
	  Component "Available Programs Manager Win32" install/verify/upgrade last done
	  at 01:25:22 June 22, 1999 $$<CCIM32<Tue Jun 22 01:26:12.050
	  1999><thread=4294798339 (0xFFFD6C03)>
	  Component "Available Programs Manager Win32" needs to be verified
	  $$<CCIM32><Tue Jun 22 01:26:12.050 1999><thread=4294798339
	  (0xFFFD6C03)>
	  Warning: \\SERVER1\CAP_MS1\clicomp.box\smsapm32.CFG version () out of sync
	  with offer file version (2.00.1239.0000); skipping operations
	  $$<CCIM32><Tue Jun 22 01:26:12.270 1999><thread=4294798339
	  (0xFFFD6C03)>
	  Checking if component "Software Distribution" needs to be installed, upgraded
	  or verified (offer index [5]) $$<CCIM32><Tue Jun 22 01:26:12.270
	  1999><thread=4294798339 (0xFFFD6C03)>
	  Component "Software Distribution" needs to be installed
	  $$<CCIM32><Tue Jun 22 01:26:12.270 1999><thread=4294798339
	  (0xFFFD6C03)>
	  Warning: \\SERVER1\CAP_MS1\clicomp.box\SWDist.CFG version () out of sync with
	  offer file version (2.00.1239.0000); skipping operations
	  $$<CCIM32><Tue Jun 22 01:26:12.440 1999><thread=4294798339
	  (0xFFFD6C03)>
	  Checking if component "Software Inventory Agent" needs to be installed,
	  upgraded or verified (offer index [4]) $$<CCIM32><Tue Jun 22
	  01:26:12.440 1999><thread=4294798339 (0xFFFD6C03)>
	  Component "Software Inventory Agent" needs to be installed
	  $$<CCIM32><Tue Jun 22 01:26:12.490 1999><thread=4294798339
	  (0xFFFD6C03)>
	  Warning: \\SERVER1\CAP_MS1\clicomp.box\sinv.CFG version () out of sync with
	  offer file version (2.00.1239.0000); skipping operations
	  $$<CCIM32><Tue Jun 22 01:26:12.660 1999><thread=4294798339
	  (0xFFFD6C03)>
	  Checking if component "Hardware Inventory Agent" needs to be installed,
	  upgraded or verified (offer index [3]) $$<CCIM32><Tue Jun 22
	  01:26:12.660 1999><thread=4294798339 (0xFFFD6C03)>
	  Component "Hardware Inventory Agent" needs to be installed
	  $$<CCIM32><Tue Jun 22 01:26:12.660 1999><thread=4294798339
	  (0xFFFD6C03)>
	  Warning: \\SERVER1\CAP_MS1\clicomp.box\hinv.CFG version () out of sync with
	  offer file version (2.00.1239.0000); skipping operations
	  $$<CCIM32><Tue Jun 22 01:26:12.820 1999><thread=4294798339
	  (0xFFFD6C03)>
	  Done processing active client components $$<CCIM32><Tue Jun 22
	  01:26:12.880 1999><thread=4294798339 (0xFFFD6C03)>
	
	CAUSE
	=====
	
	The issue can occur when the service pack has not been applied to all the sites
	that share a given set of logon points (that is, all domain controllers within a
	Windows NT domain). Installation of the service pack updates the files for the
	base components on all logon points for the site. This means that clients that
	get the base components from the logon point will be running the Service Pack 1
	version of the base components. When the client then attaches to the client
	access point (CAP) server to install the optional components, there is a version
	mismatch and the optional components are not installed.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Systems Management
	Server version 2.0. For additional information, please see the following article
	in the Microsoft Knowledge Base:
	
	  Q236325 How to Obtain the Latest Systems Management Server 2.0 Service Pack
	
	WORKAROUND
	==========
	
	To avoid this problem, try either of the following:
	
	- Ensure that all sites sharing the logon points are upgraded simultaneously.
	
	  -or-
	
	- Disable logon discovery and installation for affected sites.
	
	In a situation where one of the sites has already been updated but the others
	have not, another option is to upgrade the remaining sites to Systems Management
	Server 2.0 Service Pack 1.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 2.0. This problem was first corrected in Systems Management Server
	version 2.0 Service Pack 2.
	
	MORE INFORMATION
	================
	
	This issue only affects clients for sites that have not been upgraded, because
	the base components that the clients get from the logon point are not
	synchronized with the CAP(s) for the site.
	
	Although this issue does not cause an error condition on clients, it does prevent
	the client from having full functionality. Microsoft recommends that you upgrade
	all sites that share logon points as closely together as possible, to avoid
	experiencing this issue.
	
	The upgrade process is:
	
	1. If the Client Configuration Installation Manager (CCIM) wakes up before the
	  client logs on again, the upgrade will occur solely from the CAP. Thus,
	  clients who belong to a site that has been upgraded and therefore are meant
	  to receive the upgrade will run Clicore from their upgraded CAP. Clients that
	  belong to a site that has not yet been upgraded (and therefore are not meant
	  to be upgraded) will not in this instance.
	
	2. If the client logs on before the next CCIM wakeup cycle and Windows NT Client
	  Logon Discovery/Installation is enabled, the Clicore on the logon point will
	  run, updating part of the base components (that is, the parts needed by Logon
	  Discovery and Installation). CCIM will finish the base installation at its
	  next wakeup cycle.
	
	Additional query words: prodsms SP SP1 smsfaqtop
	
	======================================================================
	Keywords          : kbsms200 kbsms200bug kbsms200sp2fix 
	Technology        : kbSMSSearch kbSMS200
	Version           : winnt:2.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
