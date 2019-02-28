1. Copy TestCenter.Linux.x64.tar.gz to /home/thot/
2. ssh to the agent
3. Run The following command
```
cd /home/thot/Spirent_Communications/Spirent_TestCenter/
mv bin bin_orig
mkdir bin
cd bin
tar -xzf ../../../TestCenter.Linux.x64.tar.gz
cp -R ../bin_orig/STAKCommands/* STAKCommands/
```
4. Change stcbll.ini to add your log preferrence
```
level=ALL:INFO,user:ALL,perf:DEBUG,fmwk.bll.base.script:DEBUG,fmwk.bll.base.cmdStatus:DEBUG
```
