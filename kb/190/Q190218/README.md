---
layout: page
title: "Q190218: HOWTO: Retrieve Settings From a Printer Driver"
permalink: /kb/190/Q190218/
---

## Q190218: HOWTO: Retrieve Settings From a Printer Driver

{% raw %}

	Article: Q190218
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbprint kbAPI kbPrinting kbSDKWin32 kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB kbDSuppo
	Last Modified: 11-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Visual Basic Printer object allows you to get to many of a printer driver's
	properties, but it does not give you access to all of them. The following sample
	demonstrates how to retrieve information from a printer driver using the WIN32
	API.
	
	MORE INFORMATION
	================
	
	A printer's settings are stored in a structure called the DEVMODE. This sample
	retrieves the DEVMODE for the current default printer and displays its settings
	in a ListBox. Note that these are numeric values that must be compared to
	constants to determine their meaning. This article only includes the constants
	for the values the code actually displays. Other constants can be found in the
	REFERENCES section at the end of this article.
	
	The sample below contains two custom functions, StripNulls and ByteToString.
	StripNulls simply takes a String and removes all characters starting at the
	first Null. This is used in place of the RTrim function because in Visual Basic
	5.0, fixed-length strings are padded with Nulls instead of the spaces used in
	Visual Basic 4.0. The ByteToString function converts an array of Bytes into a
	String. The DEVMODE contains two such arrays.
	
	There are two special notes about the following sample when running under Windows
	NT. First, many monochrome drivers have their dmColor property set to 2, which
	means they report being capable of color printing, but really are not. Also,
	some settings for the "Generic / Text Only" printer driver may not be accurate
	under NT.
	
	
	Step-by-Step Example
	--------------------
	
	1. Open a new Standard EXE project. Form1 is created by default.
	
	2. Add a CommandButton and a ListBox to the Form.
	
	3. Add the following code to the Form's module:
	
	        Option Explicit
	
	        Private Const NULLPTR = 0&
	        ' Constants for DEVMODE
	        Private Const CCHDEVICENAME = 32
	        Private Const CCHFORMNAME = 32
	        ' Constants for DocumentProperties
	        Private Const DM_MODIFY = 8
	        Private Const DM_COPY = 2
	        Private Const DM_IN_BUFFER = DM_MODIFY
	        Private Const DM_OUT_BUFFER = DM_COPY
	        ' Constants for dmOrientation
	        Private Const DMORIENT_PORTRAIT = 1
	        Private Const DMORIENT_LANDSCAPE = 2
	        ' Constants for dmPrintQuality
	        Private Const DMRES_DRAFT = (-1)
	        Private Const DMRES_HIGH = (-4)
	        Private Const DMRES_LOW = (-2)
	        Private Const DMRES_MEDIUM = (-3)
	        ' Constants for dmTTOption
	        Private Const DMTT_BITMAP = 1
	        Private Const DMTT_DOWNLOAD = 2
	        Private Const DMTT_DOWNLOAD_OUTLINE = 4
	        Private Const DMTT_SUBDEV = 3
	        ' Constants for dmColor
	        Private Const DMCOLOR_COLOR = 2
	        Private Const DMCOLOR_MONOCHROME = 1
	        ' Constants for dmCollate
	        Private Const DMCOLLATE_FALSE = 0
	        Private Const DMCOLLATE_TRUE = 1
	        Private Const DM_COLLATE As Long = &H8000
	        ' Constants for dmDuplex
	        Private Const DM_DUPLEX = &H1000&
	        Private Const DMDUP_HORIZONTAL = 3
	        Private Const DMDUP_SIMPLEX = 1
	        Private Const DMDUP_VERTICAL = 2
	
	        Private Type DEVMODE
	            dmDeviceName(1 To CCHDEVICENAME) As Byte
	            dmSpecVersion As Integer
	            dmDriverVersion As Integer
	            dmSize As Integer
	            dmDriverExtra As Integer
	            dmFields As Long
	            dmOrientation As Integer
	            dmPaperSize As Integer
	            dmPaperLength As Integer
	            dmPaperWidth As Integer
	            dmScale As Integer
	            dmCopies As Integer
	            dmDefaultSource As Integer
	            dmPrintQuality As Integer
	            dmColor As Integer
	            dmDuplex As Integer
	            dmYResolution As Integer
	            dmTTOption As Integer
	            dmCollate As Integer
	            dmFormName(1 To CCHFORMNAME) As Byte
	            dmUnusedPadding As Integer
	            dmBitsPerPel As Integer
	            dmPelsWidth As Long
	            dmPelsHeight As Long
	            dmDisplayFlags As Long
	            dmDisplayFrequency As Long
	                  
	        End Type
	
	        Private Declare Function OpenPrinter Lib "winspool.drv" Alias _
	        "OpenPrinterA" (ByVal pPrinterName As String, phPrinter As Long, _
	        ByVal pDefault As Long) As Long
	
	        Private Declare Function DocumentProperties Lib "winspool.drv" _
	        Alias "DocumentPropertiesA" (ByVal hwnd As Long, _
	        ByVal hPrinter As Long, ByVal pDeviceName As String, _
	        pDevModeOutput As Any, pDevModeInput As Any, ByVal fMode As Long) _
	        As Long
	
	        Private Declare Function ClosePrinter Lib "winspool.drv" _
	        (ByVal hPrinter As Long) As Long
	
	        Private Declare Sub CopyMemory Lib "KERNEL32" Alias "RtlMoveMemory" _
	        (hpvDest As Any, hpvSource As Any, ByVal cbCopy As Long)
	
	        Function StripNulls(OriginalStr As String) As String
	           If (InStr(OriginalStr, Chr(0)) > 0) Then
	              OriginalStr = Left(OriginalStr, InStr(OriginalStr, Chr(0)) - 1)
	           End If
	           StripNulls = Trim(OriginalStr)
	        End Function
	
	        Function ByteToString(ByteArray() As Byte) As String
	          Dim TempStr As String
	          Dim I As Integer
	
	          For I = 1 To CCHDEVICENAME
	              TempStr = TempStr & Chr(ByteArray(I))
	          Next I
	          ByteToString = StripNulls(TempStr)
	        End Function
	
	        Function GetPrinterSettings(szPrinterName As String, hdc As Long) _
	        As Boolean
	        Dim hPrinter As Long
	        Dim nSize As Long
	        Dim pDevMode As DEVMODE
	        Dim aDevMode() As Byte
	        Dim TempStr As String
	
	          If OpenPrinter(szPrinterName, hPrinter, NULLPTR) <> 0 Then
	             nSize = DocumentProperties(NULLPTR, hPrinter, szPrinterName, _
	             NULLPTR, NULLPTR, 0)
	            If nSize < 1 Then
	              GetPrinterSettings = False
	              Exit Function
	            End If
	            ReDim aDevMode(1 To nSize)
	            nSize = DocumentProperties(NULLPTR, hPrinter, szPrinterName, _
	            aDevMode(1), NULLPTR, DM_OUT_BUFFER)
	            If nSize < 0 Then
	              GetPrinterSettings = False
	              Exit Function
	            End If
	           Call CopyMemory(pDevMode, aDevMode(1), Len(pDevMode))
	
	           List1.Clear   ' empty the ListBox
	           List1.AddItem "Printer Name: " & _
	           ByteToString(pDevMode.dmDeviceName)
	
	           If pDevMode.dmOrientation = DMORIENT_PORTRAIT Then
	              TempStr = "PORTRAIT"
	           ElseIf pDevMode.dmOrientation = DMORIENT_LANDSCAPE Then
	              TempStr = "LANDSCAPE"
	           Else
	              TempStr = "UNDEFINED"
	           End If
	           List1.AddItem "Orientation: " & TempStr
	
	           Select Case pDevMode.dmPrintQuality
	              Case DMRES_DRAFT
	                  TempStr = "DRAFT"
	              Case DMRES_HIGH
	                  TempStr = "HIGH"
	              Case DMRES_LOW
	                  TempStr = "LOW"
	              Case DMRES_MEDIUM
	                  TempStr = "MEDIUM"
	              Case Else   ' positive value
	                  TempStr = CStr(pDevMode.dmPrintQuality) & " dpi"
	           End Select
	           List1.AddItem "Print Quality: " & TempStr
	
	           Select Case pDevMode.dmTTOption
	              Case DMTT_BITMAP    ' default for dot-matrix printers
	                  TempStr = "TrueType fonts as graphics"
	              Case DMTT_DOWNLOAD  ' default for HP printers that use PCL
	                  TempStr = "Downloads TrueType fonts as soft fonts"
	              Case DMTT_SUBDEV    ' default for PostScript printers
	                  TempStr = "Substitute device fonts for TrueType fonts"
	              Case Else
	                  TempStr = "UNDEFINED"
	           End Select
	           List1.AddItem "TrueType Option: " & TempStr
	
	           ' Windows NT drivers often return COLOR from Monochrome printers
	           If pDevMode.dmColor = DMCOLOR_MONOCHROME Then
	              TempStr = "MONOCHROME"
	           ElseIf pDevMode.dmColor = DMCOLOR_COLOR Then
	              TempStr = "COLOR"
	           Else
	              TempStr = "UNDEFINED"
	           End If
	           List1.AddItem "Color or Monochrome: " & TempStr
	
	           If pDevMode.dmScale = 0 Then
	              TempStr = "NONE"
	           Else
	              TempStr = CStr(pDevMode.dmScale)
	           End If
	           List1.AddItem "Scale Factor: " & TempStr
	
	          If pDevMode.dmFields And DM_COLLATE Then
	              If pDevMode.dmCollate = DMCOLLATE_FALSE Then
	                 TempStr = "Collating is supported, but turned off"
	              ElseIf pDevMode.dmCollate = DMCOLLATE_TRUE Then
	                 TempStr = "Collating is supported and turned on"
	              End If
	           Else
	              TempStr = "Collating is unsupported"
	           End If
	           List1.AddItem TempStr        
	           If pDevMode.dmFields And DM_DUPLEX Then
	              If pDevMode.dmDuplex = DMDUP_SIMPLEX Then
	                 TempStr = "Duplex is supported, but turned off (1)"
	              ElseIf pDevMode.dmDuplex = DMDUP_VERTICAL Then
	                 TempStr = "Duplex is set to VERTICAL (2)"
	              ElseIf pDevMode.dmDuplex = DMDUP_HORIZONTAL Then
	                 TempStr = "Duplex is set to HORIZONTAL (3)"
	              Else
	                 TempStr = "Duplex is set to undefined value of " & _
	                    pDevMode.dmDuplex
	              End If
	           Else
	              TempStr = "Duplex is unsupported"
	           End If
	           List1.AddItem TempStr
	
	           List1.AddItem "Y Resolution: " & pDevMode.dmYResolution & " dpi"
	           List1.AddItem "Copies: " & CStr(pDevMode.dmCopies)
	           ' Add any other items of interest ...
	
	           Call ClosePrinter(hPrinter)
	           GetPrinterSettings = True
	        Else
	           GetPrinterSettings = False
	        End If
	        End Function
	
	        Private Sub Command1_Click()
	        If GetPrinterSettings(Printer.DeviceName, Printer.hdc) = False Then
	           List1.AddItem "No Settings Retrieved!"
	           MsgBox "Unable to retrieve Printer settings.", , "Failure"
	        End If
	        End Sub
	
	4. Run the project and click on Command1. The current default printer's settings
	  will be displayed in the ListBox.
	
	REFERENCES
	==========
	
	To find additional constants, please search on DEVMODE in either the Win32
	Programmer's Reference or the Microsoft Developer Network (MSDN) Library CD-ROM.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbprint kbAPI kbPrinting kbSDKWin32 kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400
	Version           : :4.0,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
