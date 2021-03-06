---
layout: page
title: "Q272321: Windows 2000 Network Infrastructure Administration Training Kit"
permalink: /kb/272/Q272321/
---

## Q272321: Windows 2000 Network Infrastructure Administration Training Kit

{% raw %}

	Article: Q272321
	Product(s): Microsoft Press
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdocfix kbdocerr
	Last Modified: 14-JAN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- MSPRESS MCSE Training Kit, Windows 2000 Network Infrastructure Administration ISBN 1-57231-904-6 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains comments, corrections, and information about known errors
	relating to the Microsoft Press book MCSE Training Kit: Windows 2000 Network
	Infrastructure Administration, ISBN 1-57231-904-6.
	
	The following topics are covered:
	
	- Page xxxix: Windows 2000 Server Evaluation Software Is Not Included
	
	- Page 9: Upgradeable Operating System Not Listed
	
	- Page 9: Remove Fault Tolerance As An Advanced Feature
	
	- Page 11: Remove Reference To Alpha-Based Computers
	
	- Pages 21 & 375: Change "Alpha Server" To "Intel-Compatible Server"
	
	- Page 31-32: Incorrect Description Of Figure 2.2
	
	- Pages 55 & 59: Should Reference Novell Directory Services
	
	- Page 75: Incorrect Step
	
	- Page 95: Incorrect Title Bar In Figure 4.7
	
	- Page 137: Incorrect Terms For WINS
	
	- Page 140: Incorrect Information About Host Name And Computer NetBIOS Name
	
	- Page 155, Incorrect Zone Name In Figure 7.3
	
	- Page 159: Incorrect Arrow Direction In Figure 7.4
	
	- Page 163: Incomplete Description Of Recursive Request
	
	- Page 166, 168, 170: Incorrect References To Windows 2000 Professional Client
	  Computers
	
	- Page 243: Duplicate Entries In Table 10.3
	
	- Page 246: Incorrect Description of DHCP/DNS Integration Behavior
	
	- Page 247: Incorrect Steps In "To allow dynamic updates for DHCP clients that
	  do not support Dynamic DNS updates"
	
	- Page 253: Incorrect APIPA Value
	
	- Page 257: Incorrect Reference To Performance/System Monitors
	
	- Page 311: Incorrect Wording
	
	- Page 312: Correction To Figure 12.4
	
	- Page 325: Invalid IP Address In Figure 12.6
	
	- Page 332: Remove The Last Sentence In Lesson Summary
	
	- Page 334: CSP stands for "Cryptograhic Service Provider"
	
	- Page 337: "Stand-Alone Subordinate CA" Should Be "Stand-Alone Root CA"
	
	- Page 375, Question 2: Windows 2000 Server Supports 4 GB Of RAM, not 2
	
	MORE INFORMATION
	================
	
	Page xxxix: Windows 2000 Server Evaluation Software Is Not Included
	-------------------------------------------------------------------
	
	On page xxxix, the "Evaluation Edition Software Support" section should be
	removed. This book does not come with an evaluation edition of Windows 2000
	Server.
	
	
	Page 9: Upgradeable Operating System Not Listed
	-----------------------------------------------
	
	On page 9, under the Windows 2000 Professional sub-heading,
	
	Change:
	"Windows 2000 Professional can be upgraded from Windows NT Workstation 3.51 and
	greater, or Windows 98."
	
	To:
	"Windows 2000 Professional can be upgraded from Windows NT Workstation 3.51 and
	greater, Windows 95, or Windows 98."
	
	
	Page 9: Remove Fault Tolerance As An Advanced Feature
	-----------------------------------------------------
	
	On page 9, in the first sentence under the heading Windows 2000 Professional,
	remove the words "and fault tolerance".
	
	
	Page 11: Remove Reference To Alpha-Based Computers
	--------------------------------------------------
	
	Windows 2000 does not support Alpha-based computers. Under Windows 2000
	Datacenter Server on page 11, remove:
	
	"32 GB of RAM on Alpha-based computers"
	
	
	Pages 21 & 375: Change "Alpha Server" To "Intel-Compatible Server"
	------------------------------------------------------------------
	
	On pages 21 and 375, question 2, change:
	"You have an Alpha server with ..."
	
	To:
	"You have an Intel-compatible server with..."
	
	
	Page 31-32: Incorrect Description Of Figure 2.2
	-----------------------------------------------
	
	On page 31-32, the bulleted items at the bottom of page 31 and the top of page
	32, incorrectly describe Figure 2.2.
	
	Change:
	
	- Networks 1 and 2 represent two routed networks.
	
	- Network 3 represents the WAN connection between the routers
	
	- Network 3 requires a network ID so that...
	
	To:
	
	- Networks 1 and 3 represent two routed networks.
	
	- Network 2 represents the WAN connection between the routers
	
	- Network 2 requires a network ID so that...
	
	
	Pages 55 & 59: Should Reference Novell Directory Services
	---------------------------------------------------------
	
	Page 55, line 9 and the caption for Figure 3.1, as well as page 59, line 11,
	incorrectly reference NetWare Domain Services.
	
	Change:
	"NetWare Domain Services"
	
	To:
	"Novell Directory Services"
	
	
	Page 75: Incorrect Step
	-----------------------
	
	On page 75, in step 3,
	
	Change:
	"3. Click Add"
	
	To:
	"3. Click Install"
	
	
	Page 95: Incorrect Title Bar In Figure 4.7
	------------------------------------------
	
	On page 95, in Figure 4.7, the title bar in the screenshot incorrectly reads
	"RDP-Tcp Properties". It should read "username Properties".
	
	
	Page 137: Incorrect Terms For WINS
	----------------------------------
	
	On page 137, in the "About This Chapter" paragraph,
	
	Change:
	"Windows Interface Name Service (WINS)"
	
	To:
	"Windows Internet Name Service (WINS)"
	
	
	Page 140: Incorrect Information About Host Name And Computer NetBIOS Name
	-------------------------------------------------------------------------
	
	On page 140, in the first paragraph under "Understanding Host Names" and in the
	first paragraph under "Purpose of Host Names", it states that the host name does
	not have to match the NetBIOS computer name when running Windows 2000. This is
	incorrect. In Windows 2000, you cannot specify different host (Directory Naming
	Service, or DNS) and computer (NetBIOS) names.
	
	Under "Understanding Host Names" change:
	"For computers running Windows 2000, the host name does not have to match the
	Windows 2000 computer name."
	
	To:
	"For computers running Windows 2000, the host name always matches the Windows
	2000 computer name."
	
	Under "Purpose of Host Names" change:
	"The host name does not have to match the NetBIOS computer name"
	
	To:
	"The host name always matches the NetBIOS computer name in Windows 2000"
	
	
	Page 155, Incorrect Zone Name In Figure 7.3
	-------------------------------------------
	
	On page 155, in Figure 7.3, in Zone 2,
	
	Change:
	
	  "R&D"
	
	To:
	
	  "DEV"
	
	
	Page 159: Incorrect Arrow Direction In Figure 7.4
	-------------------------------------------------
	
	On page 159, in Figure 7.4, the arrows' directions for step 1 and step 8 are
	transposed. They should be reversed, with step 1 pointing upwards to the Local
	Name Server, and step 8 pointing downwards to the DNS Client.
	
	
	Page 163: Incomplete Description Of Recursive Request
	-----------------------------------------------------
	
	On page 163, in Lesson Summary,
	
	Change:
	"A DNS server will only return the information it has in cache, including the
	potential of an error, when a client makes a recursive request."
	
	To:
	"A DNS server will only return the information it has in its zones or cache,
	including the potential of an error, when a client makes a recursive request"
	
	
	Page 166, 168, 170: Incorrect References To Windows 2000 Professional Client Computers
	--------------------------------------------------------------------------------------
	
	On page 166 in Table 7.3, on page 168 in Table 7.4, and on page 170 in Table 7.5,
	the "Clients" row refers to 386 and 486 computers running Windows 2000
	Professional. Windows 2000 Professional does not run on 386 and 486 computers.
	Please remove the references to 386 and 486 computers in these tables.
	
	
	Page 243: Duplicate Entries In Table 10.3
	-----------------------------------------
	
	On page 243, in Table 10.3, "044 WINS/NBNS servers" is listed twice. Please
	remove the top entry.
	
	
	Page 246: Incorrect Description of DHCP/DNS Integration Behavior
	----------------------------------------------------------------
	
	Change:
	"The DHCP server never registers the name-to-address (A-type records) mapping
	information for DHCP clients."
	
	To:
	"The DHCP server never registers both the forward (A-type records) and reverse
	lookups (PTR-type records) with DNS."
	
	
	Page 247:  Incorrect Steps In "To allow dynamic updates for DHCP clients that do not support Dynamic DNS updates"
	-----------------------------------------------------------------------------------------------------------------
	
	On page 247, in the first bulletted section, there is a list of the steps for
	enabling the "dynamic update for DHCP clients that do not support dynamic DNS
	updates" option through the DNS managment console. This is incorrect, as this
	option is enabled through the DHCP, not DNS, managment console.
	
	Change:
	"1. Click Start, point to Program, point to Administrative Tools, then click
	DNS.
	2. In the console tree, click the applicable zone."
	...
	
	"5. Select Only Secure Updates If Your Zone Type is Active
	Directory-Integrated."
	
	To:
	"1. Click Start, point to Program, point to Administrative Tools, then click
	DHCP.
	2. In the console tree, click the applicable server."
	...
	
	"5. Click Start, point to Program, point to Administrative Tools, then click
	DNS.
	6. In the console tree, click the applicable zone.
	7. In the General property tab, select Only Secure Updates if your zone type is
	Active Directory-integrated."
	
	
	Page 253: Incorrect APIPA Value
	-------------------------------
	
	On page 253, in the third line,
	
	Change:
	"168.254.x.x"
	
	To:
	"169.254.x.x"
	
	
	Page 257: Incorrect Reference To Performance/System Monitors
	------------------------------------------------------------
	
	On page 257, under Monitoring Server Performance, change:
	
	"To access these counters, you must use System Monitor (formerly Performance
	Monitor)."
	
	To:
	"To access these counters, you must use Performance Monitor (formerly System
	Monitor)."
	
	
	Page 311: Incorrect Wording
	---------------------------
	
	On page 311, under "Inbound Internet Traffic",
	
	Change:
	"For traffic from the private network that is inbound on the Internet interface"
	
	To:
	"For traffic to the private network that is inbound on the Internet interface"
	
	
	Page 312: Correction To Figure 12.4
	-----------------------------------
	
	On page 312, in Figure 12.4, remove the arrow that flows from "Discard packet" to
	"Yes".
	
	
	Page 325: Invalid IP Address In Figure 12.6
	-------------------------------------------
	
	On page 325, in Figure 12.6, the Valid External Address Pool lists invalid IP
	addresses.
	
	Change:
	"17230.188.10
	17230.188.11"
	
	To:
	"172.30.188.10
	172.30.188.11"
	
	
	Page 332: Remove The Last Sentence In Lesson Summary
	----------------------------------------------------
	
	On page 332, under "Lesson Summary", remove the last sentence.
	
	Remove:
	"In this lesson, you also learned how to install and configure certificates."
	
	This topic is not covered until the next lesson.
	
	
	Page 334: CSP stands for "Cryptograhic Service Provider" (CSP)
	--------------------------------------------------------------
	
	On page 334, line 3 in the "Key management" section, CSP should be spelled out as
	Cryptographic Service Provider. This acronym (CSP) is introduced on this page,
	then referenced again on pages 338, 339, and 340, without an explanation of what
	it stands for. There is not an entry in the Glossary section for it.
	
	Change:
	"(accessible to Certificate Services through a CryptoAPI CSP)"
	
	To:
	"(accessible to Certificate Services through a CryptoAPI Cryptographic Service
	Provider (CSP))"
	
	
	Page 337: "Stand-Alone Subordinate CA" Should Be "Stand-Alone Root CA"
	----------------------------------------------------------------------
	
	On page 337, "Stand-Alone Subordinate CA" should be "Stand-Alone Root CA".
	
	Change:
	"Practice: Installing a Stand-Alone Subordinate CA"
	
	To:
	"Practice: Installing a Stand-Alone Root CA"
	
	Also change:
	"To install a stand-alone subordinate CA"
	
	To:
	"To install a stand-alone root CA"
	
	
	Page 375, Question 2: Windows 2000 Server Supports 4 GB Of RAM, not 2
	---------------------------------------------------------------------
	
	On page 375, Question 2
	
	Change:
	"Windows 2000 Server only supports 2 GB of RAM"
	
	To:
	"Windows 2000 Server only supports 4 GB of RAM"
	
	
	Microsoft Press is committed to providing informative and accurate books. All
	comments and corrections listed above are ready for inclusion in future
	printings of this book. If you have a later printing of this book, it may
	already contain most or all of the above corrections.
	
	Additional query words: TKBOOK WIN2000 W2K 1-57231-904-6 0-7356-1388-5
	
	======================================================================
	Keywords          : kbdocfix kbdocerr 
	Technology        : kbMSPressSearch
	Version           : :
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
