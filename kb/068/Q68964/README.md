---
layout: page
title: "Q68964: Control Panel Can List Same Printer Twice"
permalink: /kb/068/Q68964/
---

## Q68964: Control Panel Can List Same Printer Twice

{% raw %}

	Article: Q68964
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.0,3.0a,3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.0, 3.0a, 3.1, 3.11 
	- Microsoft Windows for Workgroups versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	You can have two different instances of a printer driver in the Control Panel of
	Microsoft Windows version 3.0. For example, you can have a PostScript driver
	configured as a NEC LC 890 on COM2 with legal size paper, and a PostScript
	driver configured as a QMS PS-810 on LPT2 with letter size paper.
	
	MORE INFORMATION
	================
	
	You may want to have the two printers listed separately so you won't need to
	change all printer settings each time you want to send a print job to the other
	printer. You can install a second configuration of the same printer as follows:
	
	1. From the Main group of Program manager, choose Control Panel.
	
	2. From Control Panel, choose Printers.
	
	3. From Printers, select the Add Printer option.
	
	4. From the list of printers, choose the new printer desired and select the
	  Install option.
	
	5. From the dialog box, choose current printer driver.
	
	6. Configure the new printer for the port, status, and settings desired.
	
	The above process uses the same printer driver file for multiple printer
	configurations. You may prefer to have separate printer driver files for each
	printer configuration. To do this, create a second copy of the printer driver
	under a different name as follows:
	
	1. From the Main group of Program manager, select the MS-DOS prompt.
	
	2. From MS-DOS, change to the SYSTEM subdirectory where the printer drivers is
	  located. For example, type "CD\WINDOWS\SYSTEM" (without the quotation marks)
	  to change to the WINDOWS\SYSTEM directory.
	
	3. At the MS-DOS prompt, make a copy of your printer driver. For example, "COPY
	  PSCRIPT.DRV PSCRIPT2.DRV" (without the quotation marks) will make a copy of
	  the PostScript driver file named PSCRIPT2.DRV.
	
	4. Type "EXIT" (without the quotation marks) to return to Windows.
	
	5. In Windows, use a text editor such as Notepad or SysEdit to edit your WIN.INI
	  file as follows:
	
	        [PrinterPorts]
	        Generic / Text Only=TTY,LPT1:,15,45
	        PostScript Printer=PSCRIPT,COM1:,15,45
	        Alternate Printer=PSCRIPT2,LPT2:,15,45
	
	        [devices]
	        Generic / Text Only=TTY,None
	        PostScript Printer=PSCRIPT,COM1:
	        Alternate Printer=PSCRIPT2,LPT2:
	
	  Alternate Printer refers to the second copy of the printer driver.
	
	6. Exit Windows and restart it so Windows will reread the WIN.INI file and cause
	  these entries to appear in Printer Setup under the Control Panel.
	
	NOTE: Although you can add a different name for a printer driver, you may not see
	the expected Setup dialogue box. For example, after adding a name for a
	Hewlett-Packard (HP) LaserJet IIIsi PostScript driver, the Apple Laser Writer
	Plus Setup dialog box may appear instead of HP's.
	
	Additional query words: 3.00 3.0 3.0a 3.00a win30 wfw wfwg
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWin3xSearch kbWFWSearch kbZNotKeyword3 kbWin300 kbWin300a kbWin310 kbWin311 kbWFW310 kbWFW311
	Version           : WINDOWS:3.0,3.0a,3.1,3.11
	
	=============================================================================
	

{% endraw %}
