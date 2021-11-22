# Helpful Windows privilege escalation tips

## User enumeration
Current user’s privileges: ```whoami /priv```

List users: ```net users```

List details of a user: ```net user username``` (e.g. net user Administrator)

Other users logged in simultaneously: ```qwinsta``` (the query session command can be used the same way) 

User groups defined on the system: ```net localgroup```

List members of a specific group: ```net localgroup groupname``` (e.g. net localgroup Administrators)

System info : ```systeminfo | findstr /B /C:"OS Name" /C:"OS Version"```

find configuration files: ```findstr /si password *.txt```, or ```.xls, .xml, .ini , etc```

List updates installed on the target system: ```wmic qfe get Caption,Description,HotFixID,InstalledOn```

## Network Connections
```netstat -ano```

## Scheduled tasks
```schtasks /query /fo LIST /v```

## Drivers
```driverquery```

## Antivirus
windows defender: ```sc query windefend```
or another services ```sc queryex type=service```
