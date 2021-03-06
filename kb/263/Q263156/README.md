---
layout: page
title: "Q263156: SNA Server Event IDs 4, 13, and 38 Message Sequence Errors"
permalink: /kb/263/Q263156/
---

## Q263156: SNA Server Event IDs 4, 13, and 38 Message Sequence Errors

{% raw %}

	Article: Q263156
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.11 (all SP),3.0 (all SP),4.0,4.0 SP1,4.0 SP2,4.0 SP3
	Operating System(s): 
	Keyword(s): kbsna211sp1 kbsna211sp2 kbsna300sp1 kbsna300sp2 kbsna300sp3 kbsna300sp4 sna4 kbsna400sp
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.11 SP1, 2.11 SP2, 3.0 SP1, 3.0 SP2, 3.0 SP3, 3.0 SP4, 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A computer running SNA Server that has the Data Link Control (DLC) bound to
	teamed IBM Netfinity 10/100 Ethernet adapters to communicate with the host may
	experience dropped LU-LU sessions. The following events may appear in the
	Application event log.
	
	  Event Source: SNA Server
	  Event ID: 4
	  Description:
	  (1133) Message Sequence Error
	
	  Event Source: SNA Server
	  Event ID: 13
	  Description:
	  (1141) Message Sequence Error (SENSE = 0)
	
	  Event Source: SNA Server
	  Event ID: 38
	  Description:
	  APPC session deactivated abnormally
	
	CAUSE
	=====
	
	A packet arrives at the SNA Server link service that is corrupt, causing a
	sequence number to be skipped. Because the next packet that arrives has a
	sequence number that is not one greater than the previous, SNA Server sends an
	UNBIND to the host with sense code 2001, which means there is a sequence error.
	
	RESOLUTION
	==========
	
	The teaming function for the adapters that are bound to the DLC must be
	configured for Fault Tolerance mode, rather than Fast Ether Channel.
	
	WORKAROUND
	==========
	
	Disable teaming for the DLC, and use a single NIC for the SNA Server-to-host
	link.
	
	MORE INFORMATION
	================
	
	An SNA Server trace of this problem contains the following messages (data is
	truncated for simplicity). The sequence numbers, noted by ^^^^ in each RU, are
	009B, 009C, and 009E:
	
	  
	
	  ----------------------------------------------- 11:41:17.0878
	  04160000->01020101 DLC DATA
	                  DAF:01 OAF:02 ODAI:off Normal
	                  RQE FMD MC DR1
	
	  ---- Header  at address 012054F4, 2 elements ----
	  0B050000 00002C00 0102009B 01009000     <......,.........>
	                     ^^^^
	  ---- Element at address 01BF7460, start 10, end 268 ----
	  009000F0 A140F0F0 F0F0F0F0 F0F0F04B     <...0.@000000000K>
	  F0F0A140 F0F0F0F0 F0F0F0F0 F04BF0F0     <00.@000000000K00>
	  ----------------------------------------------- 11:41:17.0878
	  04160000->01020101 DLC DATA
	                  DAF:01 OAF:02 ODAI:off Normal
	                  RQE FMD MC DR1
	
	  ---- Header  at address 012049FC, 2 elements ----
	  0B050000 00002C00 0102009C 01009000     <......,.........>
	                     ^^^^
	  ---- Element at address 01BF6468, start 10, end 268 ----
	  009000F0 F0F0F0F0 F04BF0F0 A140F0F0     <...000000K00.@00>
	  F0F0F0F0 F0F0F04B F0F0A140 F0F0F0F0     <0000000K00.@0000><BR/>
	  ----------------------------------------------- 11:41:17.0894
	  04160000->01020101 DLC DATA
	                  DAF:01 OAF:02 ODAI:off Normal
	                  RQE FMD MC DR1
	
	  ---- Header  at address 012043B0, 2 elements ----
	  1E040000 00002C00 0102009E 01009000     <......,.........>
	                     ^^^^
	  ---- Element at address 01BF7460, start 10, end 268 ----
	  009000F0 F0A14F40 A1404040 4040A140     <...00.O@.@@@@@.@>
	  F0F0F0F0 F0F0F0F0 F04BF0F0 A140F0F0     <000000000K00.@00>
	
	The following message appears in the trace where the RU with sequence number 009D
	needs to be:
	
	  
	
	  ----------------------------------------------- 11:41:17.0894
	  04160000->01020101 DLC DATA
	                  INVALID TH !!
	
	  ---- Header  at address 012054F4, 1 elements ----
	  1E040000 00000000 00000000 01009000     <................>
	
	  ---- Element at address 01BF3EC4, start 10, end 45 ----
	  00000000 00000000 00000000 00000000     <................>
	  00000000 00000000 00000000 00000000     <................>
	
	A network trace captured on an independent computer displayed a good RU with
	sequence 009D arriving at the Ethernet switch to which SNA Server was
	connected.
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsna211sp1 kbsna211sp2 kbsna300sp1 kbsna300sp2 kbsna300sp3 kbsna300sp4 sna4 kbsna400sp1 kbsna400sp2 kbsna400sp3 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ400 kbSNAServ211SP1 kbSNAServ211SP2 kbSNAServ300SP3 kbSNAServ300SP1 kbSNAServ400SP1 kbSNAServ400SP2 kbSNAServ400SP3 kbSNAServ300SP2 kbSNAServ300SP4
	Version           : WINDOWS:2.11 (all SP),3.0 (all SP),4.0,4.0 SP1,4.0 SP2,4.0 SP3
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
