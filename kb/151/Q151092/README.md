---
layout: page
title: "Q151092: PRB: Mismatched Pushjmp/Popjmp Call Message from Modify Form"
permalink: /kb/151/Q151092/
---

## Q151092: PRB: Mismatched Pushjmp/Popjmp Call Message from Modify Form

{% raw %}

	Article: Q151092
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:3.0b; WINDOWS:3.0b
	Operating System(s): 
	Keyword(s): 
	Last Modified: 15-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Macintosh, version 3.0b 
	- Microsoft Visual FoxPro for Windows, version 3.0b 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you load a Visual FoxPro form for editing, the process stops before the
	form appears on the Visual FoxPro desktop and an error dialog box appears
	stating:
	
	  "Mismatched pushjmp/popjmp call"
	
	Clicking the OK button causes the Visual FoxPro session to terminate. The
	subsequent action depends on the operating system.
	
	In Windows 95, the user is sent back to the Windows desktop. However, the Visual
	FoxPro session remains hidden, but does show in the Windows 95 task list if you
	press ALT+TAB, and presents a small, modal dialog box when Visual FoxPro for
	Windows 3.0b is restarted. This dialog box appears behind the Visual FoxPro
	Desktop of the newer session, remaining hidden until the second Visual FoxPro
	session is terminated.
	
	In the Windows NT operating system environment, the same error message appears,
	and Visual FoxPro 3.0b is terminated with no residual processes.
	
	In the Windows for Workgroups and the Windows 3.1x operating systems, the error
	message is the same. Visual FoxPro is terminated and Windows is locked so the
	user must use a "Cold" boot, pushing the reset button or power off/on, to resume
	normal operations.
	
	In Visual FoxPro for the Macintosh version 3.0b, the error message returned
	states
	
	  "Error loading file - Row Source Type - Record <n>. Property value is
	  out of bounds"
	
	where <n> is the row number of the offending control in the .scx table.
	
	CAUSE
	=====
	
	This behavior occurs when the form has been saved with the Row Source property
	of a Listbox or ComboBox containing any command or reference which has more than
	254 characters. An example of a command that is too long is an SQL Select
	command that has too many characters in the command expression.
	
	While the limit for a command length in Visual FoxPro for Windows 3.0 is 8092
	characters, the limit is only 254 characters when the command is a property of a
	control on a form.
	
	If the RowSourceType property is "3 - SQL Statement" for either a Listbox or
	Combobox control, the actual SQL SELECT command can be keyed into the RowSource
	property in the Property Window.
	
	The Property window of the form limits the number of characters keyed into the
	box to 254. However, the acceptable length of the string comprising the
	SELECT-SQL statement is 253 bytes.
	
	When an incorrect SELECT is the RowSource of the control, the form is saved and
	then restored to the desktop with a MODIFY FORM or a DO FORM. Visual FoxPro then
	presents an information dialog box stating:
	
	  "Mismatched pushjmp/popjmp call"
	
	WORKAROUND
	==========
	
	To work around this behavior, reduce the length of the SQL SELECT statement. If
	you have a copy of Visual FoxPro for Windows 3.0, the form can be modified, the
	RowSource SELECT statement modified, and the form can be loaded for editing
	and/or execution in Visual FoxPro for Windows release 3.0b.
	
	If the method above is unavailable, the .scx table can be loaded into a work area
	with a USE command and then browsed. Each control on the form is described in a
	row. The control name is located in a memo field named "Objname", and the actual
	SELECT statement is in a memo field named "Properties." When the incorrect
	statement is found, it can be edited to the correct length and then saved.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. In the Visual FoxPro Command window, type "MODIFY FORM testerr" (without the
	  quotation marks).
	
	2. From the Form Control toolbar, select Listbox ,and click the form to place a
	  listbox.
	
	3. Click the right mouse button on the listbox, and select Properties from the
	  Context menu. From the Property menu, choose RowSourceType, and select "3 -
	  SQL statement."
	
	4. Click the RowSource property in the row above the RowSourceType.
	
	5. In the Property window, type "SELECT . . . SQL command." The program limits
	  the statement to 254 bytes, truncating the last word at DESCEND, as follows:
	
	     SELECT ".." + PADR(CDOW(td_end),12) + DTOC(td_end) ;
	        + "-.-" + PADR( ALLTRIM(STR( kl_prt_ct )) ;
	        + " LEADS ",10) ;
	        +IIF(kl_type="P","..Printed "," UNPRINTED") ;
	        AS day, td_end,kl_type ;
	     FROM trakdate, keylead ;
	     WHERE DTOS(td_end)=keylead.kl_code ;
	     INTO CURSOR te ;
	     ORDER BY td_date DESCENDING
	
	6. From the File menu, select Save, and then close the form.
	
	7. In the Command window, enter the command "MODIFY FORM testerr."
	
	Additional query words: VFoxWin error freeze terminate list box combo
	
	======================================================================
	Keywords          :  
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbVFP300bMac kbVFP300b
	Version           : MACINTOSH:3.0b; WINDOWS:3.0b
	
	=============================================================================
	

{% endraw %}
