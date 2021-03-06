---
layout: page
title: "Q191588: BUG: Create Report w/ SYS(1037) Saves Old Printer Information"
permalink: /kb/191/Q191588/
---

## Q191588: BUG: Create Report w/ SYS(1037) Saves Old Printer Information

{% raw %}

	Article: Q191588
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Running a CREATE REPORT after executing SYS(1037) saves old printer information
	to the Tag and Tag2 fields of the report.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. We are researching this bug and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Make sure that you have at least two printers installed. For this example,
	  the following printers are used:
	
	  HP LJ4L (called "LaserJet")
	  Panasonic KX-P1624 (called "Panasonic KX-P1624").
	  The LaserJet is the default Windows printer.
	
	2. Execute the following code and follow the commented instructions:
	
	        =SYS(1037) && choose the Panasonic.
	        =SYS(1037) && choose the LaserJet.
	        CREATE REPORT Test
	
	3. Save the report and close it.
	
	4. Run the following code from the Command window and note the contents of the
	  memo fields:
	
	        USE Test.FRX
	        MODIFY MEMO Tag, Tag2
	
	After the name "LaserJet", there are some left over letters from the Panasonic
	printer. Please note that if the second printer chosen has a longer name than
	the first, this does not seem to happen.
	
	Additional query words: kbVFp600bug kbReportWriter kbPrinting
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
