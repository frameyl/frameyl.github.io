Restart Table Gateway:
```
su table (password is tabletable)
cd /usr/bin/table
ls -ltr start*
nohup ./startTABLEGateway.sh
```
Alternative Table Gateway:
```
D:\prog\table\Release\TABLE.properties

# Raleigh
# gateway.server=rtp-tableLin01.ad.spirentcom.com

# Calabasas
# gateway.server=bllbldlnx-10.cal.ci.spirentcom.com

# Honolulu
#gateway.server=hnl-tableLin01.ad.spirentcom.com

```

Trigger a table build on Linux
```
Table.exe submit -build clean -dir . -debug no -target bll-el3-64 -server-selection Linux -runUnitTests yes -archive yes -changelist 908005
Table.exe submit -build incremental -dir . -debug no -target bll-el3-64 -server-selection Linux -runUnitTests yes -archive yes -changelist 908005
```
Trigger a table build for release branch
```
set P4CLIENT=cyang_BEJ-5M6GHG2_rel
Table.exe submit -build clean -dir . -debug no -server-selection Windows -runUnitTests yes -archive yes -changelist 909432
Table.exe submit -build incremental -dir . -debug no -server-selection Windows -runUnitTests yes -archive yes -changelist 899191
```
