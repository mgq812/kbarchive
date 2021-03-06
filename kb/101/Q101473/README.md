---
layout: page
title: "Q101473: Replication Overview in the Windows NT Operating System"
permalink: /kb/101/Q101473/
---

## Q101473: Replication Overview in the Windows NT Operating System

{% raw %}

	Article: Q101473
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.1,3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.1 
	- Microsoft Windows NT Workstation version 3.1 
	- Microsoft Windows NT Advanced Server, version 3.1 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Windows NT supports replication to maintain specific, identical sets of files
	and directories on different computers. Changes to information on one computer
	is automatically replicated to other computers configured to receive those
	changes. One common use for replication maintains identical login scripts for
	all servers that process login requests in a domain. It can also be used to
	replicate changes to other files, such as database files that are updated
	regularly and must be duplicated exactly on other servers to maintain a copy of
	the database.
	
	MORE INFORMATION
	================
	
	To support replication, Windows NT requires an export server and an import
	server. The export server must maintain the master copy of the files and
	directories to replicate in an export directory (by default,
	C:\WINNT\SYSTEM32\REPL\EXPORT). An export server can replicate directory trees
	that contain as many as 32 subdirectories. After configuring a server to
	replicate files, the EXPORT directory on the export server is automatically
	shared as follows:
	
	- Repl$ as a hidden administrative share that allows the Administrators local
	  group access with Full Control permission and the Replicator local group
	  account access with Read permission.
	
	Import servers can be computers with Windows NT Advanced Server, Windows NT, or
	OS/2 LAN Manager 2.x servers. Import servers receive the master copy of the
	files and directories from the export directory on the export server and place
	them into an import directory (by default, C:\WINNT\SYSTEM32\REPL\IMPORT). After
	configuring the system for replication, the IMPORT directory on each import
	server is automatically shared as the IMPORT share that allows the Everyone
	account access with Full Control permissions.
	
	Replication goes from the export server to the import server(s), not the other
	direction, unless an Advanced Server has been configured as both an export and
	an import server. (A Windows NT workstation cannot be configured as an export
	server.) At regular intervals, the import server establishes a session by
	logging onto the export server. If the export server contains files or
	directories that have been modified since the last update, these files are
	replicated to the import server. If any files or directories have been deleted
	from the import server or if new files have been created on the export server,
	the export server replicates the files and directories not present and
	resynchronizes the import directory.
	
	Replication can occur between specific computers or between domains. If you
	activate replication on the import server without specifying the name of a
	computer or of a domain, the import server automatically replicates files from
	the export server in its domain. An export server can also export files to a
	specified domain. Any computer configured for import replication in the domain
	receives any changes to files and directories. You can also configure
	replication to occur between machines if a trust relationship exists between
	their domains.
	
	Additional Information:
	
	See article Q104204 in the Microsoft Knowledge Base for more information.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTW310 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS310 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS351search kbWinNTS350search kbWinNTS310search kbWinNT310Search kbWinNTW310Search
	Version           : WinNT:3.1,3.5,3.51,4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
