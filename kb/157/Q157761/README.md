---
layout: page
title: "Q157761: HOWTO: Use the ActiveX Control SS Tab Object Properties"
permalink: /kb/157/Q157761/
---

## Q157761: HOWTO: Use the ActiveX Control SS Tab Object Properties

{% raw %}

	Article: Q157761
	Product(s): Microsoft FoxPro
	Version(s): 
	Operating System(s): 
	Keyword(s): kbinterop kbDatabase kbvfp500 kbvfp600
	Last Modified: 12-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The SS Tab control is very similar to the PageFrame control, although there are
	some important differences. Some properties of the SS Tab control cannot be
	accessed at design time but can be changed at run time.
	
	MORE INFORMATION
	================
	
	The PageFrame control has a separate property sheet for each page. The SS Tab
	control has only one property sheet. If different tabs are selected, the Tab
	property changes number. At run time the different tabs may be accessed by
	setting the tab number as follows:
	
	     * OleControl1 is the default name of the control.
	     ThisForm.OleControl1.Object.Tab = 1
	
	There is a Picture property that cannot be accessed via a property sheet. If the
	property is double-clicked, a dialog box appears but a picture cannot be
	selected. A picture can be assigned to a tab at run time by using the
	LoadPicture function. Pictures cannot be assigned to pages of a PageFrame.
	
	The following code placed in the Init event of the form assigns the Fox.bmp to
	the tab area of the second tab. Tabs are numbered starting with 0 (zero):
	
	     * The name of the control was changed to sstab.
	     ThisForm.Olecontrol1.Object.Tab = 1
	     ThisForm.Olecontrol1.Object.Picture = LoadPicture(Home()+"fox.bmp")
	
	One reason you may want to use the SS tab control instead of the PageFrame is the
	TabOrientation property. The tabs of the SS tab control can be placed at the
	bottom, or on the left or right sides.
	
	Like the PageFrame the tabs can spread across the entire length of the object or
	can be shortened. The Style property offers two choices: Windows 95 or Microsoft
	Office. These are the equivalent of the PageFrame choices of unjustified or
	justified under the TabStyle property. If you choose Windows 95 for the SS Tab
	control, the tab strip area not occupied by a tabs has the same BackColor as the
	control instead of the BackColor of the form. This looks messy, but you can
	change it easily by issuing the following command in the Init of the form. (The
	BackColor of form is assumed to be green here.)
	
	     ThisForm.Olecontrol1.Object.BackColor=RGB(0,255,0)
	
	The BackColor of the SS Tab control is not available at design time.
	
	Each of the pages within a PageFrame control has its own setting for BackColor
	and ForeColor, so they can be set individually. BackColor and ForeColor in the
	SS Tab control apply to the whole control and cannot be set individually for the
	separate tabs. ForeColor, like BackColor is not available at design time.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbinterop kbDatabase kbvfp500 kbvfp600 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP600
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
