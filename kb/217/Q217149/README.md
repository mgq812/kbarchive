---
layout: page
title: "Q217149: XFOR: Chat Service May Terminate Unexpectedly"
permalink: /kb/217/Q217149/
---

## Q217149: XFOR: Chat Service May Terminate Unexpectedly

{% raw %}

	Article: Q217149
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5 SP2
	Operating System(s): 
	Keyword(s): exc55sp2 EXC55SP3Fix
	Last Modified: 01-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 SP2 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The Microsoft Exchange Chat Service version 5.5 Service Pack 2 may terminate
	unexpectedly when sending a zero byte privmsg or whisper. A call stack similar
	to the following may appear in the Drwtsn32.log file:
	
	  
	
	  FramePtr  RetAddr   Param1   Function Name
	  02ffe894  0042030d  02ffeb20 CHATSVC!CIrcUser::SendMsg+0x5b4
	  02ffea7c  0042d691  02ffeb20 CHATSVC!CChannel::SendMsg+0x7bd
	  02ffec0c  00443685  02ffec2c CHATSVC!CIrcUser::CommandMessage+0x701
	  02ffed44  00442f68  02ffedcc CHATSVC!CIrcUser::MessageInt+0x655
	  02ffed98  00442b58  02ffedcc CHATSVC!CIrcUser::Message+0x288
	  02fffdf0  00471d42  01d57050 CHATSVC!CIrcUser::Incoming+0x198
	  02ffff5c  00471674  00000000 CHATSVC!CSocket::IOCompletionRead+0x642
	  02ffff80  0047833c  00000000 CHATSVC!CSocket::IOCompletion+0x94
	  02ffffb0  0047837b  02ffffec CHATSVC!CService::ThreadPool+0x13c
	  02ffffb8  77f04f3e  01d4de5c CHATSVC!CService::ThreadPoolThunk+0xb
	  02ffffec  00000000  00000000 0x77f04f3e
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: Chat Service
	
	+--------------------------+
	| File name   | Version    | 
	+--------------------------+
	| Chatsvc.exe | 5.5.2549.0 | 
	+--------------------------+
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft Exchange Chat
	Service that is included with Microsoft Exchange Server version 5.5 Service Pack
	2. This problem was first corrected in Exchange Server 5.5 Service Pack 3.
	
	MORE INFORMATION
	================
	
	Most IRC and IRCX clients prohibit sending a zero byte whisper or privmsg but
	this problem can occur when you use Telnet. The problem can occur with any of
	the following functions:
	
	- PRIVMSG
	- NOTICE
	- WHISPER
	- DATA
	- REQUEST
	- REPLAY
	
	
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55sp2 EXC55SP3Fix 
	Technology        : kbExchangeSearch kbZNotKeyword2 kbExchange550SP2
	Version           : winnt:5.5 SP2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
