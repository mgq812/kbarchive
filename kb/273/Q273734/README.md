---
layout: page
title: "Q273734: SMS: How to Set Up Unattended Installation Scripts"
permalink: /kb/273/Q273734/
---

## Q273734: SMS: How to Set Up Unattended Installation Scripts

{% raw %}

	Article: Q273734
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): kbinterop kbsetup kbConfig kbSecurity kbServer kbsms200 kbsmsUtil kbUpgrade
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to set up unattended installation scripts. You can
	use unattended installation scripts to install either a primary or secondary
	site.
	
	MORE INFORMATION
	================
	
	Before you install Systems Management Server (SMS) version 2.0, ensure that
	either Microsoft Windows NT Server version 4.0, Service Pack 4, or Microsoft
	Windows 2000 Server is installed on the computers that are going to be either
	the site servers or the site database servers. Microsoft SQL Server 7.0 or
	Microsoft SQL Server 2000 must be installed prior to Systems Management Server
	installation remotely or locally.
	
	To perform an unattended installation of SMS 2.0, use the following steps.
	
	NOTE: The following sample script is a general script for an unattended
	installation. This script must be modified to suit your specific purpose.
	
	1. Create a user account that you can use as the SMS service account, give the
	  account logon privileges as a service right, and then make the account a
	  member of the Domain Administrator group.
	
	2. Create an initialization file (Filename.ini) that contains the following
	  text. Ensure that you supply your own values for the variables, such as,
	  site, domain, and server.
	
	A sample script:
	
	  [Identification]
	  Action=<InstallPrimarySite or InstallSecondarySite>
	
	  [Options]
	  FullName=<My Full Name>
	  OrgName=<YourCompanyName>
	  ProductID=<123-4567890>
	  SiteCode=<LA1> The site code is a three-character code that SMS uses to
	  identify a site.
	  SiteName=<My Site> The site name is any text that describes the site.
	  SiteDomain=<domain1> The site domain is the Windows NT domain that the
	  site server is in.
	  ServiceAccount=<SMSService >
	  ServiceAccountDomain=<domain1> The domain that the service account is
	  in.
	  ServiceAccountPassword=<YourPassword>
	
	  PublicKey=
	  NumOfClients=<100> The number of clients is the total number of client
	  and server computers that are in the current site and all child sites. The
	  number of clients is used by Setup to calculate the size of the SMS site
	  database device and transaction log device.
	  ServerPlatforms=<X86>
	  NetworkEnvironments=
	  OptionalUnits= <Licensing Metering, Remote Control, Nwbind, Nwnds>
	  SMSInstallDir=<D:\SMS>
	  InstallSQLServer=<0 0:SQL installation not included>.
	  ParentSiteCode=
	  ParentSiteServer=
	  AddressType= <MS_LAN, MS_ASYNC_RAS, MS_ISDN_RAS, MS_X25_RAS,
	  MS_SNA_RAS>
	  LanUser= <Domain\User> This specifies the Windows NT account that the
	  SMS service on this child site must use to connect to the parent site.
	  LanUserPassword=
	  RasUser= This field can be omitted if the Address Type is MS_LAN.
	  RasUserDomain=
	  RasUserPassword=
	  RasPhoneBook=
	  NumberOfAdminUI=<5>
	  SDKServer=<testsms> The server in which you want to place the SMS
	  Software Development Kit (SDK) provider. This server can be either the SMS
	  site server or the SQL server. In the case of a secondary site installation,
	  you do not have to specify a server name.
	
	  [SQLInstallOptions]
	  SQLInstallDir=<E:\SmsSQL7>
	  SAPassword=
	  SQLDevicePath=<E:\Smsdata>
	
	  [SQLConfigOptions]
	  SQLServerName=<testsms>
	  SQLServerVersion=<7.0>
	  UseSQLIntegratedSecurity=<0> (1 for Yes, 0 for No)
	  SQLLoginID=<sa> This field can be omitted if UseSQLIntegratedSecurity is
	  set to 1.
	  SQLLoginPassword= This field can be omitted if UseSQLIntegratedSecurity is set
	  to 1.
	  CreateSQLDevice=1 If you want SMS Setup to automatically create the devices on
	  SQL 6.5 or create the database on SQL 7.0. (1 for Yes, 0 for No)
	  DatabaseName=<SMS_sitecode>
	  DatabaseDevice=<SMS_sitecode_Data>
	  LogDevice=<SMS_sitecode_Log>
	  SQLDevicePath=<E:\Smsdata>
	  NumberOfSqlConnections=<75>
	  AutoConfigSqlConnections=<1>
	
	  [LicenseServer]
	  SQLServerName=<testsms>
	  SQLServerVersion=<7.0>
	  UseSQLIntegratedSecurity=<0>
	  SQLLoginID=<sa>
	  SQLLoginPassword=
	  CreateSQLDevice=<1>
	  DatabaseName=<LicDb>
	  DatabaseDevice=<LicData>
	  LogDevice=<LicLog>
	  SQLDevicePath=<E:\Smsdata>
	
	  [Bootstrap]
	  SetupPath=
	  Action=
	  BuildNumber= 1493 for Service Pack 2 (SP2) or Service Pack 3 (SP3)
	
	3. At a command prompt, run SMS 2.0 Setup by using the initialization file that
	  you created in step 1 of this article. (The Setup file can be located in the
	  SMSsetup\Bin\I386 folder on the SMS CD-ROM.) For example, you can use the
	  setup /script filename.ini /nouserinput command.
	
	4. If the unattended Setup is unsuccessful, check the SMSsetup.log on the root
	  folder of drive C.
	
	REFERENCES
	==========
	
	Refer to Appendix E in the Microsoft Systems Management Server 2.0 Resource
	Guide for further information about unattended installations.
	
	Additional query words: prodsms unattended installation
	
	======================================================================
	Keywords          : kbinterop kbsetup kbConfig kbSecurity kbServer kbsms200 kbsmsUtil kbUpgrade 
	Technology        : kbSMSSearch kbSMS200
	Version           : :2.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
