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

### In the Virtual machine
#### If you have this error:
VM Name: Tails

VirtualBox can't operate in VMX root mode. Please disable the KVM kernel extension, recompile your kernel and reboot (VERR_VMX_IN_VMX_ROOT_MODE).

Result Code:

NS_ERROR_FAILURE (0X80004005)

Component:

ConsoleWrap

Interface:

IConsole {6ac83d89-6ee7-4e33-8ae6-b257b2e81be8}

![image](https://github.com/user-attachments/assets/0f3dc171-2a0b-4641-a876-c93e9c60413a)

#### Execute this
vboxmanage startvm --type headless deb12-lab-10e-build

lsmod | grep kvm

sudo modprobe -r kvm_intel 

#### Normal/similar output

┌──(kali㉿kali)-[~]

└─$ vboxmanage startvm --type headless deb12-lab-10e-build

VBoxManage: error: Could not find a registered machine named 'deb12-lab-10e-build'

VBoxManage: error: Details: code VBOX_E_OBJECT_NOT_FOUND (0x80bb0001), component VirtualBoxWrap, interface IVirtualBox, callee nsISupports

VBoxManage: error: Context: "FindMachine(Bstr(pszVM).raw(), machine.asOutParam())" at line 867 of file VBoxManageMisc.cpp
                                                                             
┌──(kali㉿kali)-[~]

└─$ lsmod | grep kvm

kvm_intel             413696  0
kvm                  1396736  1 kvm_intel
                                                                             
┌──(kali㉿kali)-[~]
└─$ sudo modprobe -r kvm_intel 

[sudo] password for kali:

![image](https://github.com/user-attachments/assets/3f1f0fdd-283f-4a14-9c81-982b2978c1b1)

