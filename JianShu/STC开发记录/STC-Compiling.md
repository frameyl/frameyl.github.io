####代码编译
#####编译IL
```
#yocto1.5 32bit
scons target=stc_yocto arch=yocto_ccpu_x86_64    -j16 yocto_ver=1.5
#yocto1.5 64bit
scons target=ccpu_yocto arch=yocto_ccpu_x86_64 -j16 yocto_ver=1.5  APP_ARCH=x86_64
scons target=stc_yocto arch=yocto_ccpu_x86_64 -j16 yocto_ver=1.5  APP_ARCH=x86_64
#
export APP_ARCH=i686
./build/il/scripts/phxbld -j16 yocto_ver=1.5 yocto_vm 2>&1 | tee yocto_vm.log Output == y1.5/32bit
export APP_ARCH=x86_64
./build/il/scripts/phxbld -j16 yocto_ver=1.5 yocto_vm 2>&1 | tee yocto_vm.log Output - y1.5/64bit 
```
BLL CharFix
copy \\spcbejfs01\shares\departments\STCDev\Common\STC\STC GUI Development Configuration Environment to local disk
```
..\..\charfix . *.cpp;*.h;*.hpp;*.c
```
#####编译BLL
Go to your STC source code, e.g. cd D:\dev\TestCenter\integration
```
run “genSln.bat”
```
For BLL Release
run `.\scons.cmd -j 8 -f SConstruct.bll debug=0 target=bll-win32 -c` to clean the old builds
run `.\scons.cmd -j 8 -f SConstruct.bll debug=0 target=bll-win32`
For BLL Debug
run `.\scons.cmd -j 8 -f SConstruct.bll debug=1 target=bll-win32 -c` to clean the old builds
run `.\scons.cmd -j 8 -f SConstruct.bll debug=1 target=bll-win32`

#####修改DataModel
```
scons -f SConstruct_Autogen.bll
```
Checkin 生成的xml文件

#####编译GUI
Go to your STC source code, e.g. `cd D:\dev\TestCenter\integration`
Run 
```
pushd C:\Program Files (x86)\Microsoft Visual Studio\2017\Professional\Common7\Tools
call VsDevCmd.bat -arch=x86
popd
msbuild.exe TestCenter.UI.Gen.sln /t:build /p:Configuration=Debug
```
For GUI Release
```
msbuild.exe TestCenter.UI.Gen.sln /t:build /p:Configuration=Release
```
For GUI Debug
```
msbuild.exe TestCenter.UI.Gen.sln /t:build /p:Configuration=Debug
```
Clean GUI Build
```
msbuild.exe TestCenter.UI.Gen.sln /t:clean /p:Configuration=Debug
```
####调试技巧
#####Proxy Brower
How to enable proxy browser.
Put the following code to the file TestCenterCategory.xml in your STC installed directory. Eg C:\Program Files (x86)\Spirent Communications\Spirent TestCenter 9.90\Spirent TestCenter Application
```
<Section Name="Debugging">
      <Modules>
        <ModuleInfo AssemblyFile="Framework.UI.DebugPlugin.dll" />
        <ModuleInfo AssemblyFile="Framework.UI.EotResultViewPlugin.dll" />    
      </Modules>
</Section>
```
Delete files in C:\Users\chwang\AppData\Local\Application Data\Application Data\Spirent_Communications
Restart STC, choose View menu to enable proxy bowser.
#####部分编译
```
scons.cmd -j 8 -f SConstruct.bll debug=1 target=bll-win32-framework
```
