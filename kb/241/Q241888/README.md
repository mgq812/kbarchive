---
layout: page
title: "Q241888: Unable to Obtain DHCP Lease When Using a Cable Modem"
permalink: /kb/241/Q241888/
---

## Q241888: Unable to Obtain DHCP Lease When Using a Cable Modem

{% raw %}

	Article: Q241888
	Product(s): Microsoft Windows NT
	Version(s): WINDOWS:95; winnt:4.0
	Operating System(s): 
	Keyword(s): kberrmsg kbhw kbnetwork kbHardwarekbfixlist
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft Windows 98 
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you connect to a network using a cable modem, you may be unable to obtain a
	Dynamic Host Configuration Protocol (DHCP) address from a Windows NT-based DHCP
	server. The Windows NT-based DHCP client may generate the following error
	message:
	
	  The DHCP client was unable to obtain an IP network address from a DHCP
	  server.
	
	Also, the Windows NT-based DHCP server may generate the following error message:
	
	  WSAEMSGSIZE - Error 10040
	
	CAUSE
	=====
	
	This issue occurs because the cable modem DHCP client is sending a DHCPDISCOVER
	packet that is larger than 576 bytes, and the Windows NT-based DHCP server is
	not able to correctly process the large packet. The WSAEMSGSIZE error message
	may appear when the buffer size is not large enough to accommodate the receiving
	datagram.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0. For
	additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	STATUS
	======
	
	This problem was first corrected in Windows NT 4.0 Service Pack 6.
	
	MORE INFORMATION
	================
	
	Microsoft Windows NT DHCP server is in compliance with RFC 2131, which specifies
	the maximum length of a DHCP packet to be 576 bytes. This fix is being
	implemented as a proactive step to prevent this issue. This is a server fix, and
	it should only be applied to Windows NT-based DHCP servers.
	
	Additional query words: winsock 2.0 4.00
	
	======================================================================
	Keywords          : kberrmsg kbhw kbnetwork kbHardware kbfixlist
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400 kbWin95search kbWin98search kbZNotKeyword3 kbWin98
	Version           : WINDOWS:95; winnt:4.0
	Hardware          : ALPHA x86
	Issue type        : kbprb
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
