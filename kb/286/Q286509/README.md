---
layout: page
title: "Q286509: Error Message: No GPS Device Found on This Machine..."
permalink: /kb/286/Q286509/
---

## Q286509: Error Message: No GPS Device Found on This Machine...

{% raw %}

	Article: Q286509
	Product(s): Microsoft Automap
	Version(s): 
	Operating System(s): 
	Keyword(s): kbimu
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MapPoint 2001 
	- Microsoft Streets and Trips 2001 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to enable the Global Positioning System (GPS) features in
	Streets and Trips 2001 or Microsoft MapPoint 2001, you may receive the following
	error message:
	
	  No GPS device found on this machine. Verify your GPS device is connected and
	  turned on. Choose Configure GPS Receiver from the GPS menu to ensure that
	  your device is attached properly.
	
	CAUSE
	=====
	
	This behavior can occur if any of the following conditioning is true:
	
	- The GPS Device is not plugged into your computer.
	
	- The GPS add-in is not configured to the correct port.
	
	- The GPS device is not set to NMEA 2.0 compliance.
	
	- The GPS device is plugged into the communications (COM) port that is in use
	  by another program.
	
	- The computer has infrared ports that have the same interrupt request (IRQ) as
	  the COM port.
	
	RESOLUTION
	==========
	
	To resolve this issue, follow the troubleshooting steps below.
	
	Make Sure the GPS Device Is Configured Properly
	-----------------------------------------------
	
	The GPS device should be configured to the following settings:
	
	1. On the Tools menu in Expedia Streets and Trips 2001 or in MapPoint 2001,
	  point to GPS, and then click Configure GPS Receiver.
	
	2. Select an available communications (COM) port from the list, and then click
	  Next.
	
	3. Click OK.
	
	The device should meet the following requirements:
	
	- INTERFACE should be NMEA/NMEA.
	
	- The Standard should be NMEA 0183 2.0.
	
	- The baud rate should be 4800.
	
	Check the GPS Device in HyperTerminal
	-------------------------------------
	
	1. Start HyperTerminal.
	
	2. On the "Make new connection" screen, type 'test' into the field name and
	  click OK.
	
	3. On the next screen, in the "connect using" box, select "Direct to Com X"
	  where X is either 1 or 2. Click OK.
	
	4. On the Port Setting screen, change "Bits per second" to 4800 and "flow
	  control" to "none".
	
	5. Click OK.
	
	At this point you should start seeing a continual stream of data, which looks
	something like this:
	
	$GPRMB,A,,,,,,,,,,,,V*71
	$GPGGA,225224,3400.000,N,06854.375,E,1,07,2.0,638.3,M,-37.5,M,,*6D
	$GPGSA,A,3,06,10,17,,22,23,,26,30,,,,4.3,2.0,3.0*33
	$GPGSV,3,1,09,06,86,096,51,10,18,043,40,17,49,307,47,21,04,225,00*74
	$GPGSV,3,2,09,22,14,310,39,23,40,223,46,24,04,081,00,26,37,119,45*7B
	$GPGSV,3,3,09,30,24,202,42,,,,,,,,,*43
	$PGRME,15.0,M,22..5,M,15.0,M*1B
	$PGRMM,WGS 84*06
	
	If the data is obviously garbled, as in the following
	
	lkdxflkhglkjhflkllkj^%^%#$*(%)%)()($)()(___$%()*)#$%___%(*)#(*()*
	#*#$(*)(*$^________$^(
	*($*$(^________$#*^%)$
	#$*(!%*($_^++$+OI{*U{NE(R(){E09[b*%}*$#+NB*6NB8646n__*^4n0b5e796n3876
	__%*($N+BW)$_^N^N0964w--___#(*^%NB+W{$=6n0BW(*n4){)(Wu6n
	
	there is probably a communication problem between the GPS and the computer.
	
	Occasionally, problems such as these can be resolved by modifying the settings of
	the GPS or the serial port. If this does not resolve the issue, contact your GPS
	manufacturer.
	
	Clean Boot the Computer
	-----------------------
	
	Clean boot your computer. To do this, use the appropriate method for your version
	of Microsoft Windows.
	
	Microsoft Windows Millennium Edition (Me):
	
	1. Click Start, click Run, type "msconfig" (without the quotation marks) in the
	  Open box, and then click OK.
	
	2. On the General tab, click "Selective startup".
	
	3. Click to clear all of the check boxes under "Selective startup".
	
	4. On the "Startup" tab, click to select the *StateMgr check box.
	
	
	5. Click OK. When you are prompted to restart your computer, click Yes. After
	  the computer restarts, click Start, click Run, type "msconfig" (without the
	  quotation marks) in the Open box, and then click OK.
	
	  IMPORTANT: Look closely at the General tab to ensure that the check boxes you
	  cleared are still cleared. Proceed to step 6 if none of the check boxes is
	  selected. If you see an unavailable check box (appears dimmed), your computer
	  is not truly "clean-booted" and you may need assistance from the manufacturer
	  of the program that places a check mark back into Msconfig.
	
	6. After you verify that your computer is clean-booted in step 5, you can
	  isolate the issue. If the original issue does not reoccur after the clean
	  boot, select one item at a time under "Selective startup", and then restart
	  the computer to see if the additional entry reproduces the original issue.
	
	How to Return from a Clean Boot State
	-------------------------------------
	
	1. Click Start, click Run, type "msconfig" (without the quotation marks) in the
	  Open box, and then click OK.
	
	2. On the General tab, click "Normal startup".
	
	3. Click OK. Click Yes when you are prompted to restart your computer.
	
	Microsoft Windows 98:
	
	1. Click Start, and then click Run.
	
	2. In the Open box, type "msconfig" (without the quotation marks), and then
	  click OK.
	
	3. On the General tab, click Selective Startup, and then click to clear the
	  following check boxes:
	   - Process Config.sys File
	
	   - Process Autoexec.bat File
	
	   - Process Winstart.bat File (if available)
	
	   - Process Win.ini File
	
	   - Load Startup Group Items
	
	4. Click OK. When you are prompted to restart the computer, do so.
	
	For additional information about how to clean boot Windows 98, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q192926 How to Perform Clean-Boot Troubleshooting for Windows 98
	
	Microsoft Windows 95:
	
	1. Restart the computer. When you see the "Starting Windows 95" message, press
	  the F8 key, and then select Command Prompt Only from the Startup menu.
	
	2. At the command prompt, type "win" (without the quotation marks), and then
	  press ENTER. Press and hold down the SHIFT key until the Windows startup
	  sequence is complete.
	
	3. Disable any anti-virus or disk tool programs installed on the computer.
	
	  For information about how to disable these programs, see the printed or online
	  documentation for the program.
	
	4. Quit all running programs except Explorer and Systray. To do this, press
	  CTRL+ALT+DELETE, click the program that you want to quit, and then click End
	  Task. If you receive a message that the program is busy or not responding,
	  click End Task again. Repeat this step to quit all programs except Explorer
	  and Systray.
	
	For additional information about how to clean boot Windows 95, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q177604 Multimedia: Troubleshooting Using Clean Boot of Windows 95
	
	Decrease the COM Port Buffer
	----------------------------
	
	The buffer settings are located in the Device Manager under the appropriate COM
	port's "Advanced Settings" button. Decreasing these settings may allow a GPS to
	be seen or to function more reliably within the application.
	
	Issues That Are BIOS Related
	----------------------------
	
	The following contains suggestions for changing settings in the basic
	input/output system (BIOS). Improperly setting some options in the BIOS could
	cause significant problems on the system. Please consult your reference manual
	when working in the BIOS and use caution.
	
	Some BIOS support what is called "serial timeout." If this is turned on, problems
	may arise. Set this to OFF. Make sure that the resource hexadecimal address and
	IRQ match those in Device Manager as well.
	Also note that Infrared ports can often cause trouble with GPS detection. If the
	option is available, DISABLE the infrared port.
	
	Check IR Port and Modem Settings
	--------------------------------
	
	In some cases, it may be necessary to disable the IR port or to disable or remove
	an internal modem (scanner card, bus mouse card, and so on) which may be sharing
	a virtual COM port with the computers external serial port. For example, if a
	modem that is installed uses COM3, it may not be possible for a GPS device to be
	seen within the software if the GPS is attached to COM1.
	
	Check for and Remove Ghost Devices
	----------------------------------
	
	To remove ghost devices, follow the steps below in the order given.
	
	Check Device Manager:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click System.
	
	3. Click the Device Manager tab.
	
	4. Double-click Human Interface Devices.
	
	5. Make note of the entries listed under this type.
	
	6. Double-click "Sound, video and game controllers".
	
	7. Make note of the entries listed under this type.
	
	8. Double-click "Universal Serial Bus controllers".
	
	9. Make note of the entries listed under this type.
	
	10. Click Cancel to close the Device Manager.
	
	Restart Your Computer in Safe Mode:
	
	Follow the steps below for your operating system.
	
	Windows 95
	
	1. Click Start, then click Shut Down.
	
	2. Click Restart The Computer, and then click Yes.
	
	3. As soon as you see the message "Starting Windows 95," press F5.
	
	4. When Windows finishes loading, close the message about Safe Mode.
	
	Windows 98 and Windows Millennium Edition (Me)
	
	1. Click Start, then click Shut Down.
	
	2. Click Restart The Computer, and then click Yes.
	
	3. Press and hold the SHIFT key as soon as the POST (Power on Self Test) has
	  completed.
	
	4. When Windows finishes loading, close the message "Safe Mode" message.
	
	Check Device Manager and Remove Duplicate Devices:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click System.
	
	3. Click the Device Manager tab.
	
	4. Double-click Human Interface Devices.
	
	5. Remove any duplicate device from the list made in section 1 above.
	
	6. Double-click "Sound, video and game controllers".
	
	7. Remove any duplicate device from the list made in section 1 above.
	
	8. Double-click "Universal Serial Bus controllers".
	
	9. Remove any duplicate device from the list made in section 1 above.
	
	10. Click Close to close the Device Manager.
	
	11. Restart the system if not prompted.
	
	NOTE: Let the system reboot in normal mode.
	
	Check Installation of the Add-on
	--------------------------------
	
	Remove and reinstall the GPS add-0n. To do this, follow these steps.
	
	Remove GPS Add-on:
	
	1. Click Start, point to Settings, and then click Add/Remove Programs.
	
	2. Double-click Microsoft GPS Add-on V1.01.
	
	3. Follow the prompts to remove.
	
	NOTE: If the program is not listed, skip to the next steps to install the
	program.
	
	Install GPS Add-on:
	
	1. With the installation disk in the drive, double-click My Computer.
	
	2. Right-click on the CD (CD1) and then click Install GPS.
	
	3. Follow the prompts.
	
	Try a Different COM Port
	------------------------
	
	- Try setting up the GPS on a different COM port.
	
	- Remove any conflicting software in Add/Remove Programs. This could include
	  modem software and infrared support software, specifically infrared support
	  for Windows 95 version 2.0.
	
	- Look for and remove any software that is for infrared or COM port use.
	
	
	Additional query words: Map GPS Automap Expedia Streets Trips Point track position multi multi-media media mm
	
	======================================================================
	Keywords          : kbimu 
	Technology        : kbHomeProdSearch kbExpediaSearch kbMapptSearch kbMapPoint2001 kbExpediaStreets2001
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
