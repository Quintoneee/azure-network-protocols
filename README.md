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

- Create a Resource Group and two Virtual Machines
- Observe ICMP Traffic
- Configure a Firewall (Network Security Group)
- Observe SSH, DNS, DHCP, and RDP traffic 

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/9JRyo6V.jpeg" height="80%" width="80%" alt="Resource Group"/>
  <img src="https://i.imgur.com/ZQWyRUm.jpeg" height="80%" width="80%" alt="Virtual Machines"/>
</p>
First step in this process is to create a Resource Group. This going to help monitor and maintain the two Virtual Machines we are going to create as well. When creating this, make sure to place it in the region where your located. Once this is finsihed, we will the start on the VMs. Head over to your home screen and click on create VM, we need a windows and a linux VM. While the first VM is creating it will also generate a new virtual network/subnet. When the second VM is created, we will put that one on the previous vnet/subnet mask that was generated. Lets make sure to place both VMs on the same resource group and in the same region. Authenicate your username/password for both and write them down so you don't forget.  
<p>
  
</p>
<br />

<p>
<img src="https://i.imgur.com/bVDOA4e.jpeg" height="50%" width="50%" alt="ICMP filtered"/>
<img src="https://i.imgur.com/83m9GwC.jpeg" height="50%" width="50%" alt="ICMP filtered"/>
<img src="https://i.imgur.com/8xWSvVD.jpeg" height="80%" width="80%" alt="Linux Private Address"/> 
</p>
<p>
Now its time to get into the remote desktop. go to your start menu and pull it up. once there you will go the windows virtaul machine and get the public ip address. which you can find by going to windows vm and it will pull up certain things such as the public ip address, private address, and settings etc; Take that public ip address and put it in the remote destop, it will ask you for the usernaem/password you created for the windows vm. Inside of the windows vm we will pull up wirehsark. wireshark will help us open a packet capture as well as filter for icmp traffic between both vms. 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
