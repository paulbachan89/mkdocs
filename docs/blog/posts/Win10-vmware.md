## Creating a Windows 10 Virtual Machine on VMWare ESXi

This guide will walk you through creating a Windows 10 Virtual Machine inside of VMWare ESXi.

### Download the Windows 10 ISO file

My VMWare Server is located at the IP Address: https://10.10.10.50.

This is a small diagram as the how my network is connected.

[![Windows 10 Install](images/Win10-vmware/win10-1.jpg)](images/Win10-vmware/win10-1.jpg)

First you're going to need to Download the Windows 10 Virtual Machine. You can get a free copy of Windows 10 from: https://www.microsoft.com/en-ca/software-download/windows10

Simply download the Windows 10 Media Creation tool:

[![Windows 10 Install](images/Win10-vmware/win10-2.jpg)](images/Win10-vmware/win10-2.jpg)

Open the tool and then hit Accept at the first option:

[![Windows 10 Install](images/Win10-vmware/win10-3.jpg)](images/Win10-vmware/win10-3.jpg)

Then next on **Create Installation media (USB Flash Drive, DVD, or ISO File) for another PC** to begin the download.

[![Windows 10 Install](images/Win10-vmware/win10-4.jpg)](images/Win10-vmware/win10-4.jpg)

Select next on the **Select language, architecture, and edition**

[![Windows 10 Install](images/Win10-vmware/win10-5.jpg)](images/Win10-vmware/win10-5.jpg)

Select **ISO file** and click next.

[![Windows 10 Install](images/Win10-vmware/win10-6.jpg)](images/Win10-vmware/win10-6.jpg)

Choose the location for your download and click next to begin the download.

[![Windows 10 Install](images/Win10-vmware/win10-7.jpg)](images/Win10-vmware/win10-7.jpg)

Click **Finish** once the download is completed

[![Windows 10 Install](images/Win10-vmware/win10-8.jpg)](images/Win10-vmware/win10-8.jpg)

### Uploading the ISO to VMWare

Log into your ESXi instance. For me, all of my ISO files are stored in: **Storage > VMware-ISO-Storage**, then click upload

[![Windows 10 Install](images/Win10-vmware/win10-9.jpg)](images/Win10-vmware/win10-9.jpg)

Find the location for the Windows 10 ISO and click **Open**

[![Windows 10 Install](images/Win10-vmware/win10-10.jpg)](images/Win10-vmware/win10-10.jpg)

Once the upload is completed, your ISO file will be available for use.

[![Windows 10 Install](images/Win10-vmware/win10-11.jpg)](images/Win10-vmware/win10-11.jpg)

### Creating a Windows 10 Virtual Machine

Ensure you're at the Virtual Machine Tab, then click **Create/Register VM**

[![Windows 10 Install](images/Win10-vmware/win10-12.jpg)](images/Win10-vmware/win10-12.jpg)

At the **Select creation type** click **Create a new virtual machine** then click **NEXT**

[![Windows 10 Install](images/Win10-vmware/win10-13.jpg)](images/Win10-vmware/win10-13.jpg)

Enter and select the following:

- Name: Win10-1
- Compatibility: ESXi 8.0.U2 Virtual Machine
- Guest OS family: Windows
- Guest OS version: Microsoft Windows 10 (64-bit)

[![Windows 10 Install](images/Win10-vmware/win10-14.jpg)](images/Win10-vmware/win10-14.jpg)

Select a storage location for your Virtual Machine and click next:

[![Windows 10 Install](images/Win10-vmware/win10-15.jpg)](images/Win10-vmware/win10-15.jpg)

