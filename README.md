# Bypass UAC
This project can bypass UAC on an administrator account with default UAC settings  
 
## Disclaimer
This application is for educational purposes only.  
Using this tool without understanding how it's working can lead to negative consequences  
I'm not responsible for the consequences of using this tool!  
Only run it on a computer you have permission to!
## How it works
The bypass has 2 main parts  
1. Copy a fake dll to System32  
This can be done with IFileOperation  
2. Execute the fake dll with Admin privs  
pkgmgr.exe with the `/n:` options calls Dism.exe which has dll hijacking vuln  
pkgmgr is an autoelevating .exe, it requires no uac prompt or admin privs, but runs on High IL  
The executing is done by running: `pkgmgr.exe /quiet /n:unattend.xml`  
After this the High IL Dll executes the R.A.T client with admin privs  
**testDll**: the fake DismCore.dll which will be copied to System32  
**testAnything**: a launcher, which executes the dll  
**copyFile**: copies a file to the destination, without the uac prompt  

## System requirements  
### On 32 bit (x86) Machine
**x86 Release** build of testDll  
**x86 Release** build of testAnything  
**x86 Release** build of copyFile  
### On 64 bit (x64) Machine  
**x64 Release** build of testDll  
**x64 Release** build of testAnything  
**x64 Release** build of copyFile  

The tool was tested on a Windows7  and  Windows10 x64 bits machine  
The source code in this form only works with the c# R.A.T client, but you can modify it for your own project  
