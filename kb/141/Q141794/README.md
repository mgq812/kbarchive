---
layout: page
title: "Q141794: BUG: UNLOCK Command Commits Changes to Row-Buffered Records"
permalink: /kb/141/Q141794/
---

## Q141794: BUG: UNLOCK Command Commits Changes to Row-Buffered Records

{% raw %}

	Article: Q141794
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS: 3.0b,5.0,6.0
	Operating System(s): 
	Keyword(s): kbbuglist
	Last Modified: 26-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0b, 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When using either optimistic or pessimistic row buffering, if you use the UNLOCK
	command to release a record, any changes to the record are committed.
	
	WORKAROUND
	==========
	
	Do not use an UNLOCK command prior to committing or discarding the changes
	through a TABLEUPDATE() or TABLEREVERT command.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. We are researching this problem and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	The following code demonstrates the noted behavior. Place the code into a new
	program and execute it. All results will be displayed on the desktop.
	
	     SET DEFAULT TO C:\VFP
	     CLEAR
	     CLOSE DATA ALL
	     IF FILE('test.dbc')
	       DELETE DATA test
	       ERASE "XXX.DBF"
	     ENDIF
	
	     CREATE DATA test
	     CREATE TABLE xxx (dbkey i, field1 c(10))
	     USE IN xxx
	     USE xxx SHARED
	
	     INSERT INTO xxx VALUES (1, 'string1')
	     INSERT INTO xxx VALUES (2, 'string2')
	     INSERT INTO xxx VALUES (3, 'string3')
	
	     && Turn on optimistic row buffering
	     SET MULTILOCKS ON
	     =CURSORSETPROP('buffering', 3)
	
	     GO 2
	     ?' Before RLOCK() GETFLDSTATE():' + CHR(9) + GETFLDSTATE(-1)
	
	     && Lock the record for update, show that nothing has changed
	     && as far as the record is concerned.
	     =RLOCK()
	     ?' After RLOCK() GETFLDSTATE():' + CHR(9) + GETFLDSTATE(-1)
	
	     && Update the second record.
	     REPLACE field1 WITH 'changed'
	     ?' After REPLACE GETFLDSTATE():' + CHR(9) + GETFLDSTATE(-1)
	
	     && Release the lock - note that the changes are now
	     && committed even though there was no explicit update done,
	     && either through an =TABLEUPDATE(.T.) command or SKIP 1/SKIP -1
	     && command.
	     UNLOCK RECORD (RECNO())
	     ?' AFTER UNLOCK GETFLDSTATE():' + CHR(9) + GETFLDSTATE(-1)
	
	     && Go back to old data.
	     =TABLEREVERT(.T.)
	     BROWSE NOWAIT
	
	     && The data is not rolled back to its original state because the
	     && UNLOCK command has committed the revisions to the record. Rather
	     && than using an UNLOCK() command, use a SKIP command to move the
	     && record pointer or issue the TABLEREVERT/TABLEUPDATE commands.
	
	Additional query words: VFoxWin kbbuglist5.00 buglist3.00b multi user error
	
	======================================================================
	Keywords          :  kbbuglist
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300b kbVFP500 kbVFP600
	Version           : WINDOWS: 3.0b,5.0,6.0
	
	=============================================================================
	

{% endraw %}
