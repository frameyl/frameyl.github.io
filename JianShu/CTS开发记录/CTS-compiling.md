Compile STC at first

```
For CTS BLL Release
run `.\scons.cmd -j 8 -f SConstruct.bll debug=0 target=cts-bll-win32 -c` to clean the old builds
run `.\scons.cmd -j 8 -f SConstruct.bll debug=0 target=cts-bll-win32`
For CTS BLL Debug
run `.\scons.cmd -j 8 -f SConstruct.bll debug=1 target=cts-bll-win32 -c` to clean the old builds
run `.\scons.cmd -j 8 -f SConstruct.bll debug=1 target=cts-bll-win32`
```
##### 编译GUI
Go to your STC source code, e.g. `cd D:\dev\TestCenter\integration`
Run 

```
pushd C:\Program Files (x86)\Microsoft Visual Studio\2017\Professional\Common7\Tools
call VsDevCmd.bat -arch=x86
popd
msbuild.exe CTS.UI.Gen.sln /t:build /p:Configuration=Debug
```
For GUI Release
```
msbuild.exe CTS.UI.Gen.sln /t:build /p:Configuration=Release
```
For GUI Debug
```
msbuild.exe CTS.UI.Gen.sln /t:build /p:Configuration=Debug
```
