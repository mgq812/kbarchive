---
layout: page
title: "Q184549: Service Fails Unexpectedly with Access Violation in s1ppcass()"
permalink: /kb/184/Q184549/
---

## Q184549: Service Fails Unexpectedly with Access Violation in s1ppcass()

{% raw %}

	Article: Q184549
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.11,2.11 SP1,2.11 SP2,3.0,3.0 SP1,3.0 SP2,3.0 SP3,4.0
	Operating System(s): 
	Keyword(s): kbbuglist
	Last Modified: 02-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.11, 2.11 SP1, 2.11 SP2, 3.0, 3.0 SP1, 3.0 SP2, 3.0 SP3, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The SNA Server service may fail unexpectedly, resulting in an application
	exception on function s1ppcass(). When this occurs, an
	<ntroot>\drwtsn32.log file may be created, indicating a "FAULT" in the
	following routine:
	
	  Application exception occurred:
	  App: exe\snaservr.dbg (pid= <process ID>)
	  Exception number: c0000005 (access violation)
	
	[...]
	
	function: s1ppcass
	       01050c92 8b4924           mov     ecx,[ecx+0x24]
	ds:0130ea06=????????
	       01050c95 80491804         or      byte ptr [ecx+0x18],0x4
	ds:0130ea06=??
	       01050c99 8b14b5bcb00b01
	ds:00000325=????????
	                                 mov     edx,[s1rcb+0xe25c
	(010bb0bc)+esi*4]
	       01050ca0 33ff             xor     edi,edi
	       01050ca2 894228           mov     [edx+0x28],eax
	ds:02c70f82=????????
	       01050ca5 eb4e             jmp     s1ppcass+0x1d5
	(01050cf5)
	       01050ca7 8b0cb5bcb00b01
	ds:00000325=????????
	                                 mov     ecx,[s1rcb+0xe25c
	(010bb0bc)+esi*4]
	       01050cae 33ff             xor     edi,edi
	       01050cb0 57               push    edi
	       01050cb1 8b4928           mov     ecx,[ecx+0x28]
	ds:0130ea06=????????
	FAULT ->01050cb4 8911             mov     [ecx],edx
	ds:00000000=????????
	       01050cb6 8b14b5bcb00b01
	ds:00000325=????????
	                                 mov     edx,[s1rcb+0xe25c
	(010bb0bc)+esi*4]
	       01050cbd 894228           mov     [edx+0x28],eax
	ds:02c70f82=????????
	       01050cc0 8b04b5bcb00b01
	ds:00000325=????????
	                                 mov     eax,[s1rcb+0xe25c
	(010bb0bc)+esi*4]
	       01050cc7 8b4c2414         mov     ecx,[esp+0x14]
	ss:0249e913=????????
	       01050ccb 8b4024           mov     eax,[eax+0x24]
	ds:02c70f82=????????
	       01050cce 8a5108           mov     dl,[ecx+0x8]
	ds:0130ea06=??
	       01050cd1 8a4808           mov     cl,[eax+0x8]
	ds:02c70f82=??
	       01050cd4 02ca             add     cl,dl
	       01050cd6 8d542414         lea     edx,[esp+0x14]
	ss:0249e913=????????
	       01050cda 884808           mov     [eax+0x8],cl
	ds:02c70f82=??
	       01050cdd 8b442414         mov     eax,[esp+0x14]
	ss:0249e913=????????
	
	*----> Stack Back Trace <----*
	
	FramePtr ReturnAd Param#1  Param#2  Param#3  Param#4  Function
	Name
	00000020 00000000 00000000 00000000 00000000 00000000
	snaservr!s1ppcass
	(FPO: [EBP 0x00000000] [3,1,4])
	00000034 00000000 00000000 00000000 00000000 00000000
	snaservr!<nosymbols>
	
	CAUSE
	=====
	
	The application exception in Snaservr.exe occurs if SNA Server receives a
	Request Unit (RU) marked MC (Middle Chain) that contains no actual data. The SNA
	Server service does not correctly handle this occurrence, resulting in the
	application exception shown above.
	
	RESOLUTION
	==========
	
	SNA Server 3.0
	--------------
	
	To resolve this problem, obtain the latest service pack for SNA Server version
	3.0. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q184307 How to Obtain the Latest SNA Server Version 3.0 Service Pack
	
	
	
	SNA Server 4.0
	--------------
	
	This problem has been corrected in the latest U.S. Service Pack for SNA Server
	version 4.0. For information on obtaining the Service Pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server, versions 2.11, 2.11
	SP1, 2.11 SP2, 3.0, 3.0 SP1, 3.0 SP2, 3.0 SP3, and 4.0. This problem was first
	corrected in SNA Server 3.0 Service Pack 4.
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  kbbuglist
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ211 kbSNAServ400 kbSNAServ211SP1 kbSNAServ211SP2 kbSNAServ300SP3 kbSNAServ300SP1 kbSNAServ300SP2
	Version           : WINDOWS:2.11,2.11 SP1,2.11 SP2,3.0,3.0 SP1,3.0 SP2,3.0 SP3,4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
