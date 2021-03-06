---
layout: page
title: "Q138519: PRB: Arguments Are Evaluated from Right to Left in Some Cases"
permalink: /kb/138/Q138519/
---

## Q138519: PRB: Arguments Are Evaluated from Right to Left in Some Cases

{% raw %}

	Article: Q138519
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0
	Operating System(s): 
	Keyword(s): kbprogramming kbVBp400
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Visual Basic 4.0 allows you to pass a variable number of arguments to a
	subroutine or function by using a parameter array (ParamArray). Although,
	arguments passed to another function or subroutine are evaluated from right to
	left when a parameter array is used in the 32-bit version, the 16-bit version
	evaluates arguments from left to right when a parameter array is used.
	
	Arguments are evaluated from left to right if a set number of arguments is passed
	to a function or subroutine in both the 16-bit and 32-bit versions.
	
	Arguments are evaluated from right to left when using the switch function in both
	the 16-bit and 32-bit versions of Visual Basic.
	
	WORKAROUND
	==========
	
	Code that relies on the order of evaluation of arguments passed to another
	function is dangerous code in any language. To correct code that fails because
	of the order of evaluation, Microsoft recommends that arguments be explicitly
	calculated before being passed to a function or subroutine.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	The following table summarizes the order in which arguments are evaluated:
	
	Version   Parameter Array   Set Number of Arguments   Switch Function
	---------------------------------------------------------------------
	16-bit    Left to Right     Left to Right             Right to Left
	32-bit    Right to Left     Left to Right             Right to Left
	
	The following example illustrates the danger of relying on the order of
	evaluation of arguments. In all cases, you can fix the code by first calculating
	the arguments and then passing the results to the function.
	
	Steps to Reproduce Behavior When Using a ParamArray Argument
	------------------------------------------------------------
	
	This example was constructed in Visual Basic 4.0 using the 32-bit version, but
	the 16-bit or 32-bit version can be used.
	
	1. Create a new project. On Form1 (the default form), place one command button
	  (Command1).
	
	2. In the Click event for the Command1 button, place this code:
	
	     Private Sub Command1_Click()
	        y = Test(inc(1), inc(2), inc(3))
	        Debug.Print y
	     End Sub
	
	3. In the General section for Form1, place these two code segments:
	
	     Function Test(ParamArray z()) As Integer
	        Test = z(2)
	     End Function
	
	     Public Function inc(y As Integer) As Integer
	        Static x As Integer
	        x = x + 1
	        inc = x + y
	     End Function
	
	4. Run the program by pressing the F5 key, and click the Command1 button.
	
	  The debug window prints out the number 4. If the arguments were evaluated from
	  left to right, the same code would print out the number 6 because x would be
	  incremented twice before the third argument was evaluated in the inc
	  function.
	
	  If a set number of arguments are passed to the Test function, then the
	  arguments are evaluated from left to right. This is illustrated by rewriting
	  the function Test as follows:
	
	     Function Test(z0, z1, z2) As Integer
	        Test = z2
	     End Function
	
	  In this case, the debug window prints out 6.
	
	  To fix the code, and still use a parameter array, you could change the code in
	  the Click event of Command1 to evaluate the arguments first as in this
	  example:
	
	     Private Sub Command1_Click()
	        X1 = inc(1)
	        X2 = inc(2)
	        x3 = inc(3)
	        y = Test(X1, X2, X3)
	        Debug.Print y
	     End Sub
	
	Steps to Reproduce Behavior When Using the Switch Function
	----------------------------------------------------------
	
	1. Create a new project. On Form1 (the default form), place one command button
	  (Command1).
	
	2. In the Click event for the Command1 button, place this code:
	
	     Private Sub Command1_Click()
	        Test
	     End Sub
	
	3. In the General section for Form1, place these two code segments:
	
	     Public Function inc(x As Integer, ByVal y As Integer) As Integer
	        x = x + 1
	        inc = x
	        Debug.Print "x: "; x; "evaluated at position"; y
	     End Function
	
	     Public Sub Test()
	        Dim x As Integer
	        x = -1
	        y = Switch(False, inc(x, 1), False, inc(x, 2), True, inc(x, 3))
	        Debug.Print y
	     End Sub
	
	4. Run the program by pressing the F5 key, and click the Command1 button. From
	  the output, you can see that inc(x,3) evaluates first, then inc(x,2)
	  evaluates, and finally inc(x,1) evaluates.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbprogramming kbVBp400 
	Technology        : kbVBSearch kbAudDeveloper kbVB400Search kbVB400 kbVB16bitSearch
	Version           : WINDOWS:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
