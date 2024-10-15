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

Click Next once you're done:

[![Select creation type](images/create-vm2.jpg)](images/create-vm2.jpg)

Next it will ask me where I would like to storae my virtual machine files. I have a few option but I will choose DS2-1TB and then click next:

[![Select creation type](images/create-vm3.jpg)](images/create-vm3.jpg)

Next it will want me to customize my settings. Here's what I want:

- **CPU** - 4 vCPU
- **Memory** - 8196MB or 8GB
- **Hard Disk1** - 90GB
- **Network Adapter 1** - PGroup19100 - This network is connected to my opnsense LAN.
- **CD/DVD Drive1** - Select the Windows Server 2022 ISO file.

Once you're done with everything, click **Next**

[![Select creation type](images/create-vm4.jpg)](images/create-vm4.jpg)

Then **Finish**

[![Select creation type](images/create-vm5.jpg)](images/create-vm5.jpg)

## Installing Windows Server 2022

Once you're done with the creating the virtual machine. It's time to start it up and install Windows Server

[![Select creation type](images/install-win1.jpg)](images/install-win1.jpg)

**Press any key to boot from CD or DVDs**

[![Select creation type](images/install-win2.jpg)](images/install-win2.jpg)

The installation process is fairly simple and straight-forward. First you will be asked the following:

- **Language to Install** - English (United States)
- **Time and currency format** - English (United States)
- **Keyboard or input method** - US

[![Select creation type](images/install-win3.jpg)](images/install-win3.jpg)

Click **Install now** to begin the installation

[![Select creation type](images/install-win4.jpg)](images/install-win4.jpg)

On the **Select the operating system you want to install** I will choose Windows Server 2022 Datacenter (Desktop Experience) has a GUI whereas the ones without is only a command prompt.

[![Select creation type](images/install-win5.jpg)](images/install-win5.jpg)

Accept the License terms and agreement and proceed

[![Select creation type](images/install-win6.jpg)](images/install-win6.jpg)

For **Which type of installation do you want?** Choose **Custom: Install Microsoft Server Operating System only (advanced)** to install a fresh copy of Windows Server.

[![Select creation type](images/install-win7.jpg)](images/install-win7.jpg)

Next we're ask **Where do you want to install the operating system?** I only have one drive available so I will click **Next**

[![Select creation type](images/install-win8.jpg)](images/install-win8.jpg)

Click next will begin the installation process

[![Select creation type](images/install-win9.jpg)](images/install-win9.jpg)

Once the installation is completed, it will automatically reboot the System within 10 seconds, you can also, click restart to reboot right away.

[![Select creation type](images/install-win10.jpg)](images/install-win10.jpg)

## Windows Server 2022 Initial Configuration

Once Windows Reboot it will ask you to create an Administrator password. Enter and Re-enter your password and click finish.

[![Select creation type](images/install-win11.jpg)](images/install-win11.jpg)

Windows will then then you to the log in screen. Press CTRL+ALT+Delete to bring up the login prompt

[![Select creation type](images/config-win1.jpg)](images/config-win1.jpg)

Enter the password you create to log into Windows

When I logged in, I'm asked if I want my PC to be discoverable by other PCs, since this is a server I will say no. You might or may not get this prompt.

[![Select creation type](images/config-win2.jpg)](images/config-win2.jpg)

Next I am asked if I want to Manage my Windows using Windows Admin Center. I will say **Don't show this message again** and close it

[![Select creation type](images/config-win3.jpg)](images/config-win3.jpg)

Now that I'm in my operating system. they are a few things I would like to do as part of my initial configurations:

- Change the Timezone Zone
- Enable Remote Desktop
- Change the name
- Perform Updates
- Set a Static IP address

Thankfully I can do most of these directly from my Server Manager. I simply click on **Local Server** below **Dashboard** to begin:

[![Select creation type](images/config-win4.jpg)](images/config-win4.jpg)

First I will change my Timezone, I can click on the link next to **Timezone** to change this. I will select **Eastern Time** as my timezone. 

[![Select creation type](images/config-win5.jpg)](images/config-win5.jpg)

[![Select creation type](images/config-win6.jpg)](images/config-win6.jpg)

[![Select creation type](images/config-win7.jpg)](images/config-win7.jpg)

[![Select creation type](images/config-win8.jpg)](images/config-win8.jpg)

[![Select creation type](images/config-win9.jpg)](images/config-win9.jpg)

[![Select creation type](images/config-win10.jpg)](images/config-win10.jpg)

Next I woud like to configure my IP address. Back inside of Server Manager. My Network adapter is called Ehternet0, so I will click on the link next to it to configure my IP address.

[![Select creation type](images/config-net1.jpg)](images/config-net1.jpg)

I will use the following IP address for this server:

- **IP address**: 192.168.100.20
- **Subnet Mask**: 255.255.255.0
- **Gateway**: 192.168.100.254
- **DNS Server**: 192.168.100.20
- **DNS Server**: 192.168.100.21

After click on the link, you will be bring to your network connections. Right click on your network adapter and click properties

[![Select creation type](images/config-net2.jpg)](images/config-net2.jpg)

Then I will click on **Internet Protocol Version 4 (TCP/IPv4)** and click **Properties**

[![Select creation type](images/config-net3.jpg)](images/config-net3.jpg)

And here I will enter my IP address information

[![Select creation type](images/config-net4.jpg)](images/config-net4.jpg)

Once I'm done, I will click OK then click the Properties of Ethernet0 and lastly, I will close to network connections window.

From here I will Enable Remote Desktop by clicking on the link next to **Remote Desktop** 

**Allow Remote Connections to this computer**

**Allow Connections only from computers running Remote Desktop with Network Level Authentication (recommended)** - I will uncheck this box as I will be remote into my Server through a computer that is not a part of the Domain.

Once I've made from choices I will click **Apply** then **OK**

[![Select creation type](images/config-rdp1.jpg)](images/config-rdp1.jpg)

[![Select creation type](images/config-rdp2.jpg)](images/config-rdp2.jpg)

To change the name of my server I will click on the link next to computer name:

[![Select creation type](images/config-cn1.jpg)](images/config-cn1.jpg)

Then I will click on **Change**

[![Select creation type](images/config-cn2.jpg)](images/config-cn2.jpg)

And enter the name **dc-01** as my computer name. My naming scheme comes from what role my server will fulfill. Since this server will be a First Domain Controller it will be called dc-01.

[![Select creation type](images/config-cn3.jpg)](images/config-cn3.jpg)

Once I am done it will tell me that I need to reboot to apply the changes and will give me to option to reboot now or later. I will reboot now.

[![Select creation type](images/config-cn4.jpg)](images/config-cn4.jpg)

[![Select creation type](images/config-cn5.jpg)](images/config-cn5.jpg)

[![Select creation type](images/config-cn6.jpg)](images/config-cn6.jpg)

