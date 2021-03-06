---
layout: page
title: "Q129887: Introducing the Powerful New Picture Object in VB 4.0"
permalink: /kb/129/Q129887/
---

## Q129887: Introducing the Powerful New Picture Object in VB 4.0

{% raw %}

	Article: Q129887
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In Visual Basic version 3.0, you had only the Picture property of the PictureBox
	control. Now, in Visual Basic version 4.0, you have a new Picture object that
	adds many capabilities. This article details some of these new capabilities.
	
	MORE INFORMATION
	================
	
	Array of Picture Objects
	------------------------
	
	You can use an array of Picture objects to keep a series of graphics in memory
	without using a form that contains multiple PictureBox or Image controls. For
	example, the following code loads a Picture object with a bitmap and uses that
	bitmap to set the Picture property of a PictureBox control:
	
	     Private Sub Command1_Click()
	        Dim x As Picture
	        Set x = LoadPicture("cars")
	        Set Picture1.Picture = x
	     End Sub
	
	Handle Property of Picture Object Differs from hDC Property of PictureBox
	-------------------------------------------------------------------------
	
	There is no direct relationship between a Picture.Handle and a PictureBox.hDC.
	The hDC property of the PictureBox is the handle provided by the operating
	system to the device context of the PictureBox control. The Handle property of
	the Picture object is actually the handle of the GDI object that is contained in
	the Picture object. If the Picture property contains a bitmap, its an HBITMAP.
	If it contains an icon, then its an HICON, or if it contains a metafile, then
	its an HMETAFILE.
	
	Use the Picture Object Instead of the Windows API
	-------------------------------------------------
	
	There are lots of things you can do with an HBITMAP, an HICON, or an HMETAFILE in
	the Windows API, but the Picture object already does most of them for you. This
	means that you are better off using the Picture object instead of the Windows
	API whenever possible.
	
	There are now two completely different ways to paint graphics on a window (or
	blit). You can use BitBlt or StretchBlt on the hDC of an object, or you can use
	the PaintPicture method on the Picture Object or Property. If you have an Image
	control, you can only use PaintPicture because Image controls do not have an
	hDC. For example:
	
	     Private Sub Command1_Click()
	        Dim x as Picture
	        Set x = LoadPicture("cars.bmp")
	        PaintPicture x, 0, 0
	        PaintPicture Picture1.Picture, 0, 200
	        PaintPicture Image1.Picture, 0, 500
	     End Sub
	
	The link between the Picture object and the PictureBox control is the Image
	property. You can draw something into the hDC of the PictureBox (with BitBlt,
	Polygon, LineTo, or other API functions), and then assign its Image property to
	the Picture property. This gives the PictureBox a bitmap with the same content
	as the hDC. This is useful for operations such as converting an icon or a
	metafile into a bitmap. However, you can only use raster operation (ROP) codes
	with PaintPicture on bitmaps, so this conversion is necessary for many blitting
	operations.
	
	NOTE: For a list of Raster Operation (ROP) codes for use with PaintPicture, see
	WIN32API.TXT in your VB\WINAPI directory.
	
	Additional query words: 4.00 vb4win vb4all
	
	======================================================================
	Keywords          :  
	Technology        : kbVBSearch kbAudDeveloper kbVB400Search kbVB400 kbVB16bitSearch
	
	=============================================================================
	

{% endraw %}
