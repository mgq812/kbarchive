---
layout: page
title: "Q111769: BUG: NMAKE May Incorrectly Think Targets are up to Date"
permalink: /kb/111/Q111769/
---

## Q111769: BUG: NMAKE May Incorrectly Think Targets are up to Date

{% raw %}

	Article: Q111769
	Product(s): Microsoft Programming Utilities
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft NMAKE Utility for MS-DOS 
	- Microsoft NMAKE Utility for Windows NT 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Running NMAKE on a very fast computer system and using the /B switch may not
	force NMAKE to build a target if the target has the same time stamp as it's
	dependent files.
	
	RESOLUTION
	==========
	
	The build process may need to be modified so that a target is deleted when
	it[ASCII 146]s dependents are updated. This could be done in the command block
	for the dependents.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in NMAKE versions 1.3, 1.4, and
	1.5. We are researching this problem and will post new information here in the
	Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	The /B switch tells NMAKE to execute a dependency even if time stamps are equal.
	However, on very fast systems, NMAKE may incorrectly determine that a target is
	up to date, even when the /B switch is used. The following information is taken
	from NMAKE.WRI from the MSVC\HELP directory:
	
	"/B Tells NMAKE to execute a dependency even if time stamps are equal. Most
	operating systems assign time stamps with a resolution of 2 seconds. If your
	commands execute quickly, NMAKE may conclude that a file is up-to-date when in
	fact it is not. This option may result in some unnecessary build steps but is
	recommended when running NMAKE on very fast systems."
	
	The sample below shows that on very fast system, the reverse case can occur, and
	that some build steps may not be executed.
	
	The makefile and looping batch file shown below can be used to illustrate this
	behavior. When the looping batch file is executed, the following output should
	be repeatedly generated:
	
	  del target1
	  del target2
	  del target3
	  echo "target2" > target2
	  echo "target3" > target3
	  echo "Creating target1!" > target1
	
	  del target2
	  del target3
	  echo "target2" > target2
	  echo "target3" > target3
	  echo "Creating target1!" > target1
	
	However, on a very fast machine, the following output is periodically generated:
	
	  del target1
	  del target2
	  del target3
	  echo "target2" > target2
	  echo "target3" > target3
	  echo "Creating target1!" > target1
	
	  del target2
	  del target3
	  echo "target2" > target2
	  echo "target3" > target3
	  'target1' is up-to-date
	
	Using the makefile shown below it is not possible for target1 to be up to date
	since both of it[ASCII 146]s dependents were deleted and recreated after target1
	already existed. The file target1 would have to have a time stamp that was at
	least equal to the time stamp for it[ASCII 146]s dependents. Since NMAKE was
	invoked with the /B switch, target1 should have been rebuilt. The batch file may
	need to be run at least 10-20 times for the problem to show up. It may also be
	necessary to supress output from NMAKE and the batch file in order to allow
	NMAKE to run fast enough to reproduce the problem.
	
	Sample Makefile
	---------------
	
	  target1: target2 target3
	      echo "Creating target1!" > target1
	
	  target2:
	      echo "target2" > target2
	
	  target3:
	      echo "target3" > target3
	
	  clean:
	      del target2
	      del target3
	
	  reset:
	      del target1
	      del target2
	      del target3
	
	Looping Batch File
	------------------
	
	  :start
	  nmake /B reset target1
	  nmake /B clean target1
	  goto start:
	
	Additional query words: 1.30 1.40 1.50
	
	======================================================================
	Keywords          :  
	Technology        : kbVCsearch kbAudDeveloper kbNMAKESearch
	Version           : :
	
	=============================================================================
	

{% endraw %}
