
Each service in SQL Server represents a process or a set of processes to manage authentication of SQL Server operations 
with Windows. 

[Windows Privileges and Rights]

The account assigned to start a service needs the Start, stop and pause permission for the service. The SQL Server Setup program automatically assigns this. First install Remote Server Administration Tools (RSAT). See Remote Server Administration Tools for Windows 7.

The following table shows permissions that SQL Server Setup requests for the per-service SIDs or local Windows groups used by SQL Server components.
SQL Server Service 	Permissions granted by SQL Server Setup
SQL Server Database Engine:

(All rights are granted to the per-service SID. Default instance: NT SERVICE\MSSQLSERVER. Named instance: NT SERVICE\MSSQL$InstanceName.) 	Log on as a service (SeServiceLogonRight)

Replace a process-level token (SeAssignPrimaryTokenPrivilege)

Bypass traverse checking (SeChangeNotifyPrivilege)

Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)

Permission to start SQL Writer

Permission to read the Event Log service

Permission to read the Remote Procedure Call service
SQL Server Agent: *

(All rights are granted to the per-service SID. Default instance: NT Service\SQLSERVERAGENT. Named instance: NT Service\SQLAGENT$InstanceName.) 	Log on as a service (SeServiceLogonRight)

Replace a process-level token (SeAssignPrimaryTokenPrivilege)

Bypass traverse checking (SeChangeNotifyPrivilege)

Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)
SSAS:

(All rights are granted to a local Windows group. Default instance: SQLServerMSASUser$ComputerName$MSSQLSERVER. Named instance: SQLServerMSASUser$ComputerName$InstanceName. Power Pivot for SharePoint instance: SQLServerMSASUser$ComputerName$PowerPivot.) 	Log on as a service (SeServiceLogonRight)

For tabular only:

Increase a process working set (SeIncreaseWorkingSetPrivilege)

Adjust memory quotas for a process (SeIncreaseQuotaSizePrivilege)

Lock pages in memory (SeLockMemoryPrivilege) – this is needed only when paging is turned off entirely.

For failover cluster installations only:

Increase scheduling priority (SeIncreaseBasePriorityPrivilege)
SSRS:

(All rights are granted to the per-service SID. Default instance: NT SERVICE\ReportServer. Named instance: NT SERVICE\ReportServer$InstanceName.) 	Log on as a service (SeServiceLogonRight)
SSIS:

(All rights are granted to the per-service SID. Default instance and named instance: NT SERVICE\MsDtsServer130. Integration Services does not have a separate process for a named instance.) 	Log on as a service (SeServiceLogonRight)

Permission to write to application event log.

Bypass traverse checking (SeChangeNotifyPrivilege)

Impersonate a client after authentication (SeImpersonatePrivilege)
Full-text search:

(All rights are granted to the per-service SID. Default instance: NT Service\MSSQLFDLauncher. Named instance: NT Service\ MSSQLFDLauncher$InstanceName.) 	Log on as a service (SeServiceLogonRight)

Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)

Bypass traverse checking (SeChangeNotifyPrivilege)
SQL Server Browser:

(All rights are granted to a local Windows group. Default or named instance: SQLServer2005SQLBrowserUser$ComputerName. SQL Server Browser does not have a separate process for a named instance.) 	Log on as a service (SeServiceLogonRight)
SQL Server VSS Writer:

(All rights are granted to the per-service SID. Default or named instance: NT Service\SQLWriter. SQL Server VSS Writer does not have a separate process for a named instance.) 	The SQLWriter service runs under the LOCAL SYSTEM account which has all the required permissions. SQL Server setup does not check or grant permissions for this service.
SQL Server Distributed Replay Controller: 	Log on as a service (SeServiceLogonRight)
SQL Server Distributed Replay Client: 	Log on as a service (SeServiceLogonRight)
PolyBase Engine and DMS 	Log on as a service (SeServiceLogonRight)
Launchpad: 	Log on as a service (SeServiceLogonRight)

Replace a process-level token (SeAssignPrimaryTokenPrivilege)

Bypass traverse checking (SeChangeNotifyPrivilege)

Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)
R Services: SQLRUserGroup 	Allow Log on locally

### References
https://docs.microsoft.com/en-us/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions?view=sql-server-2017

