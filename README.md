# My-Serious-SQL-encounter-pros-and-cos
The first problem I encountered was at docker installation process while manually turning Windows features on and off, first of all my windows and user folders had the compressed double blue icon on the right, which I thought was the main problem however after many effortless googling I realized most window users had same problem. So, it was not the problem!
Window features: Virtual Machine Platform and Windows Subsystem for Linux
For error: An error has occurred. Not all features were successfully changed.
However, I came across “can’t enable Windows Subsystem for Linux” and a simple solution was to fire PowerShell as an Administrator and run a code snippet:
SOLVED “can’t enable Windows Subsystem for Linux”
:SOLUTION (Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux)

