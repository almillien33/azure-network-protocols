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
Welcome to my tutorial on Network Security Groups and Inspecting Network Protocols. You will need to create a resource group plus two VMs on Azure, one of which will be a Linux machine, and the other will be a Windows 10 machine. Both will have two CPUs, and they must be on the same VNET. Now, go into the Azure portal and create a resource group named RG-Network-Activities. Set it to East US 2 and click Create. Now you'll have to create a Windows 10 virtual machine. Set the resource group to RG-Network-Activities, which is the resource group you just created. Then the virtual machine name is windows-vm, and the region is East US 2. Then, for the image, set it as Windows 10 Pro, and for the size, pick one that has at least 2 CPUs. For the username, enter 'labuser' and the password 'Cyberlab123!'. Confirm the licensing and click 'Next' until you reach the networking section. For the Virtual Network, click 'Create New' and set it to 'Lab2-Vnet'. Afterwards, click review and create. 
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, you have to create a Linux VM. Set the resource group to RG-Network-Activities and name the machine as linux-vm. Next, set the region to East US 2, and then, for the image, select Ubuntu Server 2022. After that, set the username to labuser and the password to Cyberlab123! and confirm the license agreement. Now, click Next until you reach Networking, and for Virtual Network, ensure it is set to Lab2-Vnet. Then, click Create. 
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After that, use Remote Desktop to connect to the Windows VM you just created and download Wireshark. I will attach a link to the Wireshark download https://www.wireshark.org/download.html. Once installed, open Wireshark and filter for ICMP Traffic only. ICMP (Internet Control Message Protocol) is a network layer protocol; it's like the messenger of the internet. Its job is to send quick updates about network problems. Ping uses ICMP to check if a device is reachable, plus traceroute uses ICMP to see the path your data takes. When we filter Wireshark to only capture ICMP packets and ping the private IP address of our Linux machine, we can visually see the packets on Wireshark.
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We can inspect each packet and see the actual data that is being sent in each ping. The picture below demonstrates just that.
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now we are going to initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM by pinging the private IP address of the Linux machine with the command ping -t. While the Windows machine is pinging the Linux machine, we will go to the Linux machine and block inbound ICMP traffic on its firewall. Now, go to Virtual machines on the Azure Portal and click on your Linux VM. Then select networking -> network settings -> Network security group -> settings -> inbound security rules _> add to create a rule. Put * for destination port ranges and pick ICMPv4 for Protocol. Then, for action select Deny, and for Priority put 290 and click add. We can allow the traffic by allowing ICMP on the Linux Network Security Groups page on Azure. After that, stop the nonstop ping from the Windows VM PowerShell or command prompt, or whichever you chose to ping from the Windows VM to the Linux VM, by putting the command control c on Windows.   
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, we go back to Wire Shark on the Windows VM and start a packet capture and filter out ssh traffic only. SSH (Secure Shell) is like  a secure, encrypted tunnel that lets you remotely control and transfer files between computers over the internet, as if you were sitting right in front of the other machine. Then Open PowerShell, and type: ssh labuser@<private IP address>. Ex: ssh labuser@10.00.5 and they answer yes to the question and enter Cyberlab123! for the password. Now you will see ssh traffic in Wireshark, and when you're done, go back to PowerShell and type exit in the command line to end the ssh connection.
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now we will use Wireshark to filter for DHCP. DHCP is the Dynamic Host Configuration Protocol this works on ports 67/68. It is used to assign IP addresses to machines. Open PowerShell as admin and run: ipconfig /renew and observe the DHCP traffic appearing in Wireshark.
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Time to filter DNS traffic. We will set Wireshark to filter DNS traffic. We will initiate DNS traffic by typing in the command "nslookup www.google.com". This command essentially asks our DNS server what Google's IP address.
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lastly, we will filter for RDP traffic. When we enter tcp.port==3389, traffic is spammed nonstop because we are using the Remote Desktop Protocol to connect to our Virtual Machine.

