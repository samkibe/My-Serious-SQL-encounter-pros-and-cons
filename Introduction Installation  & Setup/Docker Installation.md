# Docker Installation for this instance is now optional 
# Because as of May 2023 - they moved the entire course data platform to Google BigQuery !!
The first problem I encountered was at docker installation process while manually turning Windows features on and off, first of all my windows and user folders had the compressed double blue icon on the right, which I thought was the main problem however after many effortless googling I realized most window users had same problem. So, it was not the problem!


Window features: Virtual Machine Platform and Windows Subsystem for Linux
For error: An error has occurred. Not all features were successfully changed.-

However, I came across “can’t enable Windows Subsystem for Linux” and a simple solution was to fire PowerShell as an Administrator and run below codeS

SOLVED ERROR : “can’t enable Windows Subsystem for Linux”
SOLUTION : (Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux)
OR
(dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart)

For Virtual Machine Platform
Error: Can't enable"Virtual Machine Platform" on windows features
DISM /Online /Enable-Feature /All /FeatureName:Microsoft-Hyper-V

Then did some tests 

Wrong - DISM /Online /Enable-Feature /All /FeatureName:Microsoft-Virtual-Machine-Platform

Wrong - Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Virtual-Machine-Platform

SOLVED ERROR : “enable the Virtual Machine Platform optional feature.”
SOLUTION : (dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart)

When it came to installing ubuntu, well, my Microsoft store was missing, however after some intensive research I came across a life hack, 
SOLVED: If you are missing Microsoft store on your pc first download Xbox APP, and at the bottom of the environment they prompt a user to install Microsoft store and ta-daa!!!

# BigQuery SETUP! EASY
Visit the official Google guide to setup a free BigQuery Sandbox instance – you can use an existing Gmail account or setup a new one just for the Serious SQL course.

https://cloud.google.com/bigquery/docs/sandbox

