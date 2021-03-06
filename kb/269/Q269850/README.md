---
layout: page
title: "Q269850: TN5250 Service Stops Responding and Logs Event 9 Error Messages"
permalink: /kb/269/Q269850/
---

## Q269850: TN5250 Service Stops Responding and Logs Event 9 Error Messages

{% raw %}

	Article: Q269850
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:4.0,4.0 SP1,4.0 SP2,4.0 SP3; :
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3 
	- Microsoft Host Integration Server 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The SNA Server TN5250 Service stops responding (hangs) after logging an Event
	18, which indicates that someone it trying to connect by using an IBM-3278-2
	device type:
	
	  Source: SNA TN5250 Server
	  Event ID: 18
	  Description: A TN5250 client attempting to connect from 172.18.83.17 with
	  terminal type IBM-3278-2 was rejected.
	
	When the Event 18 occurs, Performance Monitor shows that Tn5250.exe is using 100
	percent of the processor. After the loop starts, all subsequent client
	connection attempts result in Event 9 error messages until the TN5250 Service is
	stopped and restarted:
	
	  Source: SNA TN5250 Server
	  Event ID: 9
	  Description: The SNA TN5250 Service detected a scheduling timeout while
	  attempting to accept an incoming client.
	  File = ..\shared\tn5tnstb.c
	  Line = 574
	
	CAUSE
	=====
	
	The following internal TN5250 traces show that the TN5250 Service is looping
	within an internal memory management routine, which cause the service to become
	unresponsive:
	
	  
	
	  nbammgr.c   150: 21:09:07.89 nba_mm_alloc                    bubble up generation with free blocks
	  nbammgr.c   150: 21:09:07.90 nba_mm_alloc                    bubble up generation with free blocks
	  nbammgr.c   150: 21:09:07.90 nba_mm_alloc                    bubble up generation with free blocks
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft SNA Server 4.0 service pack or Microsoft Host Integration
	Server 2000 service pack that contains this fix.
	
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
	
	The SNA Server 4.0 version of this fix should have the following file attributes
	or later:
	
	+---------------------------------+
	| File name  | Date       | Time  | 
	+---------------------------------+
	| Tn5250.exe | 07/24/2000 | 8:02a | 
	+---------------------------------+
	
	The Host Integration Server 2000 version of this fix should follow the general
	availability of Host Integration Server 2000.
	
	NOTE: Because of file dependencies, the most recent fix that contains the above
	files may also contain additional files.
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft SNA Server 4.0, 4.0
	SP1, 4.0 SP2 and 4.0 SP3.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbHostIntegServ2000 kbSNAServ400 kbSNAServ400SP1 kbSNAServ400SP2 kbSNAServ400SP3
	Version           : WINDOWS:4.0,4.0 SP1,4.0 SP2,4.0 SP3; :
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
