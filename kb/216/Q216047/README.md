---
layout: page
title: "Q216047: Activating Numerous DLC Connections Results in Inactive LUs"
permalink: /kb/216/Q216047/
---

## Q216047: Activating Numerous DLC Connections Results in Inactive LUs

{% raw %}

	Article: Q216047
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0,3.0SP1,3.0SP2,3.0SP3,4.0,4.0SP1,4.0SP2
	Operating System(s): 
	Keyword(s): kbsna300sp4fix kbsna400sp3fix
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0SP1, 3.0SP2, 3.0SP3, 4.0, 4.0SP1, 4.0SP2 
	-------------------------------------------------------------------------------
	
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	An SNA Server that has numerous DLC 802.2 connections may experience symptoms
	similar to the following if the connections are activated concurrently:
	
	- All of the connections are in an Active state, but some of the connections
	  have Inactive 3270 Logical Units (LUs).
	
	- Some of the connections stay in an Inactive state.
	
	- The Windows NT application event log contains numerous occurrences of the
	  following message:
	
	  Event ID: 266
	  Source: SNA DLC Link Service
	  Description: The DLC 802.2 link service could not allocate a DLC buffer for an
	  outgoing message, message type 16.
	
	The number of connections that can be activated before experiencing this problem
	will vary. In general, this may occur in environments that have 50 or more DLC
	802.2 connections where each connection has many 3270 LUs defined.
	
	
	CAUSE
	=====
	
	The SNA Server DLC 802.2 link service uses an internal buffer pool to handle
	messages that it has to process. If this buffer pool is exhausted, the link
	service may discard some of the messages that is it receiving from the SNA
	Server service or from the DLC protocol stack. If the link service discards
	these messages, the symptoms described above can occur.
	
	RESOLUTION
	==========
	
	SNA Server 4.0
	--------------
	
	To resolve this problem, obtain the latest service pack for SNA Server version
	4.0. For additional information, click the following article number to view the
	article in the Microsoft Knowledge Base:
	
	  Q215838 How to Obtain the Latest SNA Server Version 4.0 Service Pack
	
	
	SNA Server 3.0
	--------------
	
	To resolve this problem, obtain the latest service pack for SNA Server version
	3.0. For additional information, click the following article number to view the
	article in the Microsoft Knowledge Base:
	
	  Q184307 How to Obtain the Latest SNA Server Version 3.0 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in Microsoft SNA Server versions
	3.0, 3.0 SP1, 3.0 SP2, 3.0 SP3, 4.0, 4.0 SP1, 4.0 SP2. This problem was first
	corrected in SNA Server version 3.0 Service Pack 4 and SNA Server version 4.0
	Service Pack 3.
	
	MORE INFORMATION
	================
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	By default, the size of the internal buffer pool used by the DLC 802.2 link
	service is 1 MB (1,024,000 bytes). SNA Server 3.0 Service Pack 1 and later
	allows this buffer pool to be increased by adding the following Registry
	parameter:
	
	  HKEY_LOCAL_MACHINE/SYSTEM/CurrentControlSet/Services/<snadlcX>
	  /Parameters/ExtraParameters/LlcBufferPoolSize
	
	<snadlcX> is the name of the DLC 802.2 link service (that is, snadlc1) that
	the buffer pool is being increased for.
	
	This parameter may need to be increased on SNA Servers that have a large number
	of DLC 802.2 connections and 3270 LUs. This buffer can be exhausted by
	simultaneously starting a large number of these connections because of the large
	number of messages that have to be processed by the link service during the
	startup sequence. The following is a list of messages that have to be processed
	by the link service when connections containing 3270 LUs are started:
	
	- XID exchanges
	
	- ACTPU (Activate PU) and ACTPU Responses for each per connection
	
	- ACTLU (Activate LU) and ACTLU Responses for each LU on each connection
	
	- Notify and Notify Responses for each LU on each connection
	
	After applying the update, the DLC 802.2 link service will allocate additional
	memory outside of the LLC buffer pool whenever this buffer pool is exhausted.
	This prevents the case where the link service discards messages when the buffer
	pool is exhausted. It is recommended that the LLC buffer pool is large enough to
	prevent the allocation of memory outside of this pool under normal operating
	conditions as using memory outside the LLC buffer pool for transmit buffers
	effects performance to some extent.
	
	For additional information about another DLC 802.2 link service problem related
	to exhausting the LLC buffer pool, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q198398 Access Violation in Snalink.exe Activating Numerous Connections
	
	The previously referenced article also includes information on how to add and
	change the LLCBufferPoolSize registry parameter.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsna300sp4fix kbsna400sp3fix 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ400
	Version           : WINDOWS:3.0,3.0SP1,3.0SP2,3.0SP3,4.0,4.0SP1,4.0SP2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
