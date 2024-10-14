## Windows Server Installation

Welcome to your first hands-on experience with Windows Server if you've never used it before. Here I will be going through the installation process with you to get an idea as to what to look for. We will be installation Windows Server 2022 as it's currently the one I'm most comfortable with. I will going a blog write up of Windows Server 2025 when time permits.

First things first. Let's grab a copy of Windows Server 2022. You can find that here: [Download Windows Server 2022](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2022)

As with my opnsense router. I will be creating a Virtual Machine using my ESXi server.

## Creating a Virtual Machine for Windows Server 2022

Click Create/Register VM

[![Select creation type](images/create-vm1.jpg)](images/create-vm1.jpg)

Select **Create a new virtual machine** and then click **NEXT**

**Select a name and guest OS**

I'm planning on making this server my domain controller so I will call it DC-01. The rest of the details are as follows:

- **Compatibility**: ESXi 8.0 U2 virtual machine
- **Guest OS family**: Windows
- **Guest OS Version**: Microsoft Windows Server 2022 (64-bit)








