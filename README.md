# My-Serious-SQL-encounter-pros-and-cos
The first problem I encountered was at docker installation process while manually turning Windows features on and off, first of all my windows and user folders had the compressed double blue icon on the right, which I thought was the main problem however after many effortless googling I realized most window users had same problem. So, it was not the problem!

Window features: Virtual Machine Platform and Windows Subsystem for Linux
For error: An error has occurred. Not all features were successfully changed.

However, I came across “can’t enable Windows Subsystem for Linux” and a simple solution was to fire PowerShell as an Administrator and run below codeS

SOLVED ERROR : “can’t enable Windows Subsystem for Linux”
SOLUTION : (Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux)
OR
(dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart)

For Virtual Machine Platform
Error: Can't enable"Virtual Machine Platform" on windows features
DISM /Online /Enable-Feature /All /FeatureName:Microsoft-Hyper-V

Then test
Wrong - DISM /Online /Enable-Feature /All /FeatureName:Microsoft-Virtual-Machine-Platform
Wrong - Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Virtual-Machine-Platform
SOLVED ERROR : “enable the Virtual Machine Platform optional feature.”
SOLUTION : (dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart)


