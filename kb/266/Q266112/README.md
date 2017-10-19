---
layout: page
title: "Q266112: Microsoft SQL Server 7.0 Data Warehousing Training Kit Comments"
permalink: kb/266/Q266112/
---

## Q266112: Microsoft SQL Server 7.0 Data Warehousing Training Kit Comments

	Article: Q266112
	Product(s): Microsoft Press
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdocfix kbdocerr
	Last Modified: 13-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- MSPRESS Microsoft SQL Server 7.0 Data Warehousing Training Kit ISBN 0-7356-0670-6 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains comments, corrections, and information about known errors
	relating to the Microsoft Press book Microsoft SQL Server 7.0 Data Warehousing
	Training Kit, ISBN 0-7356-0670-6.
	
	The following topics are covered:
	
	- Page 107: Correct Questions 3 And 4 To Match Answers In Appendix A
	
	- Page 198: Statement In Step 10 Should Be "USE PullSubs"
	
	- Page 200: Statement In Step 7 Contains Errors
	
	- Page 239: Remove Step 7
	
	- Page 336: Change First/Second/Third View To First/Second/Third Review
	
	- Page 382: Correction To The Sample Code
	
	- Page 440: Change "expand 1997" To "expand 1998"
	
	- Page 493: Missing Answers To Questions On Page 92
	
	MORE INFORMATION
	================
	
	Page 107: Correct Questions 3 And 4 To Match Answers In Appendix A
	------------------------------------------------------------------
	
	Questions 3 and 4 on page 107 should be reversed to match their answers on page
	493 in Appendix A. Also, to match the answer on page 493, question 3 must be
	changed. The following changes should be applied to page 107.
	
	Change:
	3. Why are aggregate schemas included in OLAP system designs?
	4. Are aggregate schemas always necessary in OLAP system design?
	
	To:
	3. Are aggregate schemas always necessary in OLAP system design?
	4. What are the disadvantages of using an OLTP system to conduct analytical
	processing?
	
	
	Page 198: Statement In Step 10 Should Be "USE PullSubs"
	-------------------------------------------------------
	
	On Page 198, in Step 10, change:
	"USE PublSubs"
	
	To:
	"USE PullSubs"
	
	
	Page 200: Statement In Step 7 Contains Errors
	---------------------------------------------
	
	On page 200, the statement in Step 7 contains two errors.
	
	Change:
	USE PublSubs
	SELECT * FROM Products WHERE ProductID = 1
	
	To:
	USE PullSubs
	SELECT * FROM ReplProducts WHERE ProductID = 1
	
	
	Page 239: Remove Step 7
	-----------------------
	
	On page 239, remove the first step 7:
	
	"On the Queries tab, select Update in the Query Type drop-down list. Repeat steps
	2 to 6 for the Update query. Select ProductID in the Destination column for
	Parameter 9."
	
	This step is incorrect and cannot be performed. The Update query is created in
	the next section.
	
	
	Page 336: Change First/Second/Third View To First/Second/Third Review
	---------------------------------------------------------------------
	
	On page 336, under the "To read a cube definition" section, change:
	
	1. Locate the comment labeled ***First View*** and examine...
	
	2. Locate the comment labeled ***Second View*** and examine...
	
	3. Locate the comment labeled ***Third View*** and examine...
	
	To:
	
	1. Locate the comment labeled ***First Review*** and examine...
	
	2. Locate the comment labeled ***Second Review*** and examine...
	
	3. Locate the comment labeled ***Third Review*** and examine...
	
	
	Page 382: Correction To The Sample Code
	---------------------------------------
	
	On page 382, change:
	"Crossjoin ( [USA].Children, [Q1]:[Q3])"
	
	To:
	"Crossjoin ( [USA].Children, [Q1]:[Q4])"
	
	
	Page 440: Change "expand 1997" To "expand 1998"
	-----------------------------------------------
	
	On page 440, under the "To browse the updated Sales cube" section, in step 3,
	change:
	"expand 1997"
	
	To:
	"expand 1998"
	
	
	Page 493, Missing Answers To Questions On Page 92
	-------------------------------------------------
	
	On page 493, there are no answers provided for the exercise questions found on
	page 92. Here are the missing answers:
	
	1. What would be the appropriate grain for this data mart? Why?
	
	Because the Northwind database is not very large, select the lowest grain your
	system supports. This way, you can better support unexpected queries and your
	schema will be more adaptable.
	
	2. Which tables would be appropriate dimension tables? Why?
	
	Product, to analyze product sales trends.
	Customer, to analyze what the customers typically buy and what the regional
	trends are.
	Employee, to find out which employees are most productive.
	In addition, you might want to include the Time dimension, to analyze how trends
	change over time.
	
	3. Which tables in the Northwind database would best represent the fact table?
	
	Orders, because it contains transaction facts.
	Order Details, because it contains line-item facts.
	
	4. Which measures would you include in the fact table?
	
	You need quantity, discount, line item total, and line item freight.
	
	Question 5 is not applicable here and should be removed.
	
	
	Microsoft Press is committed to providing informative and accurate books. All
	comments and corrections listed above are ready for inclusion in future
	printings of this book. If you have a later printing of this book, it may
	already contain most or all of the above corrections.
	
	Additional query words: TKBOOK BKOFFICE SQL 0-7356-0670-6
	
	======================================================================
	Keywords          : kbdocfix kbdocerr 
	Technology        : kbMSPressSearch
	Version           : :
	Issue type        : kbinfo
	
	=============================================================================
	