<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Actions and Observations</h2>
Welcome to my tutorial on Network Security Groups and Inspecting Network Protocols. You will need to create a resource group plus two VMs on Azure, one of which will be a Linux machine, and the other will be a Windows 10 machine. Both will have two CPUs, and they must be on the same VNET. Now go into the Azure portal and create a resource group and name it RG-Network-Activities, set it to East US 2, and click create. Now you'll have to create a Windows 10 virtual machine. Set the resource group to RG-Network-Activities, which is the resource group you just created. Then the virtual machine name is windows-vm, and the region is East US 2. Then, for the image, set it as Windows 10 Pro, and for the size, pick one that has at least 2 CPUs. For the username, put labuser and the password Cyberlab123! and confirm the licensing, and hit next until you get to networking, and for Virtual network, hit create new and set it as Lab2-Vnet. Afterwards, click review and create. Next, you have to create a Linux VM. Set the resource group to RG-Network-Activities and name the machine as linux-vm. Next, set the region to East US 2, and then, for the image, set it to Ubuntu Server 2022. After that, set the username to labuser and the password to Cyberlab123! and confirm the license agreement. Now, click next until you go to Networking and for Virtual network, and make sure it is set to Lab2-Vnet, then hit create. 
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br /># azure-network-protocols
