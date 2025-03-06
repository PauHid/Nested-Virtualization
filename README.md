# Nested-Virtualization
For VMWare

Go to "enable or disable windows features" in your search bar
You´ll need to Disable HyperV and Virtual Machine Platform

Execute CMD in administrator mode and paste this command

bcdedit /set hypervisorlaunchtype off

Execute Powershell in administrator mode and paste this command

Disable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V-All

### I dont´t know if this is necesarry but 

Go to setting -> Privacy and security -> Windows Security -> Device Security

Click on Core isolation details under the Core isolation heading Toggle the Memory integrity setting to Off and restart your machine

https://www.ryanchapin.com/solved-virtualized-intel-vt-x-ept-is-not-supported-on-this-platform-continue-without-virtualized-intel-vt-x-ept-on-windows-11-host/ 


The commands that you execute are neccesary, if you dont do it, not work!!!

Restart your machine and enjoy :D
