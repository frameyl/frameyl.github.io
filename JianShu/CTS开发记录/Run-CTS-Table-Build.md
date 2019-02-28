Windows
```
D:\
cd d:\stc\table

Table.exe submit -build clean -dir . -debug no -server-selection Windows -runUnitTests yes -archive yes -changelist 889174
Table.exe submit -build clean -dir . -debug no -server-selection Windows -runUnitTests yes -archive yes -changelist 889331



http://bdc-table-win01.ad.spirentcom.com/user/cyang/logs/log20180810_01/report.html

release branch:
set P4CLIENT=cyang_BEJ-5M6GHG2_rel
Table.exe submit -build clean -dir . -debug no -server-selection Windows -runUnitTests yes -archive yes -changelist 899191
Table.exe submit -build incremental -target cts-bll-win32 -sln Cts -dir . -debug no -server-selection Windows -runUnitTests no -archive yes -changelist 899191
```

Linux
```
Table.exe submit -build clean -dir . -debug no -server-selection Linux -runUnitTests yes -archive yes -changelist 909736
Table.exe submit -build incremental -target cts-bll-el3 -sln Cts -dir . -debug no -server-selection Linux -runUnitTests no -archive yes -changelist 909736
```
