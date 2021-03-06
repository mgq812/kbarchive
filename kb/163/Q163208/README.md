---
layout: page
title: "Q163208: Downstream PU Fails to Activate After Short ACTLU Response"
permalink: /kb/163/Q163208/
---

## Q163208: Downstream PU Fails to Activate After Short ACTLU Response

{% raw %}

	Article: Q163208
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.0,2.1,2.11,2.11 SP1
	Operating System(s): 
	Keyword(s): kbnetworkkbbuglist
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.0, 2.1, 2.11, 2.11 SP1 
	-------------------------------------------------------------------------------
	
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When a downstream PU2.0 emulator attempts to activate a session through an SNA
	Server, SNA Server may never send a NOTIFY (available) request to the host,
	causing the LU session to fail to activate.
	
	This problem was observed when attempting to configure an ASCII-3270 protocol
	converter (SyncResearch SDLC/LLC2 converter) to use an SNA Server downstream PU
	connection.
	
	CAUSE
	=====
	
	SNA Server automatically sends NOTIFY (unavailable) when the upstream host
	connection becomes active, and it depends on the downstream PU2.0 client to send
	a NOTIFY (available) or a "long" ACTLU response later on. However, some
	downstream clients do not send a NOTIFY message and send "short" ACTLU
	responses, and so SNA Server never sends a NOTIFY(available) to the host.
	
	RESOLUTION
	==========
	
	An update to Snaservr.exe is available for SNA Server 2.11; the update supports
	a new registry parameter to correct this problem. This update is newer than SNA
	Server 2.11 Service Pack 1.
	
	Once you have applied this update, you must also add the following registry
	entry. This will cause SNA Server to respond to the downstream client connection
	request. To add the registry entry:
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall Windows NT. Microsoft cannot guarantee that problems
	resulting from the incorrect use of Registry Editor can be solved. Use Registry
	Editor at your own risk.
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Under the HKEY_LOCAL_MACHINE subtree, go to the following subkey:
	
	     SYSTEM\CurrentControlSet\Services\SnaServr\Parameters
	
	3. Tab to the right-hand window and press the <Insert> key. In the Add
	  Value dialog box, type:
	
	  Value Name: SHORTACTLU
	  Data Type: REG_SZ
	
	  and click OK.
	
	4. In the String Editor dialog box, type:
	
	  String: <any value>
	
	  Once entered, the value will appear in REGEDT32 as follows:
	
	  SHORTACTLU: REG_SZ: <any value>
	
	5. Quit Registry Editor.
	
	The SHORTACTLU registry entry causes SNA Server to respond to the downstream
	client connection request the above behavior, regardless of the value the entry
	is set to. When this registry entry is present, SNA Server sends a
	NOTIFY(available) to the host when it receives a short ACTLU response from the
	downstream client.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server versions 2.0, 2.1,
	2.11, and 2.11 Service Pack 1 (this feature is implemented in 3.0).
	
	
	A supported fix to 2.11 is now available, but has not been fully regression-
	tested and should be applied only to systems experiencing this specific problem.
	Unless you are severely impacted by this specific problem, Microsoft recommends
	that you wait for the next Service Pack that contains this fix. Contact
	Microsoft Technical Support for more information.
	
	
	
	Additional query words: prodsna dspu
	
	======================================================================
	Keywords          : kbnetwork kbbuglist
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ200 kbSNAServ211 kbSNAServ210 kbSNAServ211SP1
	Version           : WINDOWS:2.0,2.1,2.11,2.11 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
