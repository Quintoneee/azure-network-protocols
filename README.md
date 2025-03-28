<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this Project, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


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
- Observe DNS, DHCP, SSH, and RDP traffic 

<h2>Actions and Observations</h2>

<h4>Create a Resource Group and two Virtual Machines:</h4>

<p>
<img src="https://i.imgur.com/jJAVRlY.jpeg" height="80%" width="80%" alt="Resource Group"/>
<img src="https://i.imgur.com/ZQWyRUm.jpeg" height="80%" width="80%" alt="Virtual Machines"/>
</p>
<p>
The first step in this process is to create a Resource Group. This going to help monitor and maintain the two Virtual Machines we are going to create as well. When creating this, make sure to place it in the region where you're located. Once this is finished, we will start on the VMs. Head over to your home screen and click on Create VM. We need a Windows and a Linux VM. While the first VM is creating, it will also generate a new virtual network/subnet. When the second VM is created, we will put that one on the previous vnet/subnet mask that was generated. Let's make sure to place both VMs in the same resource group and the same region. Authenticate your username/password for both and write them down so you don't forget.  
</p>
<br />

<p>
  <img src="https://i.imgur.com/mu2o8Za.png" height="45%" width="45%" alt="Remote Desktop"/>  <img src="https://i.imgur.com/PHi6H7M.jpeg" height="45%" width="45%" alt="Remote Desktop"/>
</p>
<p>
  Now its time to get into the remote desktop. go to your start menu and pull it up. Once there, you will go to the Windows virtual machine and get the public ip address. which you can find by going to windows vm and it will pull up certain things such as the public ip address, private address, and settings, etc Take that public IP address and put it in the remote destop, it will ask you for the username/password you created for the windows vm.
</p>
<br />

<h4>Observe ICMP Traffic:</h4>
<p>
<img src="https://i.imgur.com/bVDOA4e.jpeg" height="35%" width="35%" alt="ICMP filtered"/>  <img src="https://i.imgur.com/83m9GwC.jpeg" height="45%" width="45%" alt="ICMP filtered"/>
<img src="https://i.imgur.com/8xWSvVD.jpeg" height="80%" width="80%" alt="Linux Private Address"/> 
</p>
<p>
 Inside the Windows VM, we will pull up Wireshark. That will help us open a packet capture as well as filter for ICMP traffic between both VMs. Next, we are going to get the private address from the Linux VM and ping it in PowerShell, and see how the traffic is on Wireshark.  Once you ping the private address, you will be able to see the reply and request between the two VMs as well as where it's coming from. The traffic is between a Windows 10 machine and a Linux machine.
</p>
<br />

<p>
<img src="https://i.imgur.com/DgFkG1n.jpeg" height="40%" width="40%" alt="Nonstop Ping"/>
</p>
<p>
  Here we are initiating a nonstop ping, observing the ping continuously as it goes down the page. To make this happen, we enter ping 10.0.0.0 -t in the PowerShell. 
</p>
<br />

<h4>Configure a Firewall (Network Security Group):</h4>

<p>
  <img src="https://i.imgur.com/gLuHcWN.jpeg" height="80%" width="80%" alt="Inbound rule"/>
</p>
<p>
  In the picture above, we are going to deny the traffic for ICMP by going to the network security group and changing the rule to deny. For the port, source, and destination, there's no specific one, so we will put any. When this is finished, in PowerShell, the ping will look different in the command line, and the traffic will look different in Wireshark.   
</p>
<br />

<p>
  <img src="https://i.imgur.com/Nf4olHq.jpeg" height="50%" width="50%" alt="Inbound rule"/> <img src="https://i.imgur.com/9vxLTkO.jpeg" height="60%" width="60%" alt="Inbound rule"/> 
</p>
<p>
  Observing the ping and the traffic, you can see the request timed out on the command line in PowerShell since the inbound rule was denied. In Wireshark, you'll notice that between the VMs' private addresses, there's only a request. Because we changed the rule, there won't be a reply or request with the traffic. Denying any traffic for the ICMP protocol. 
</p>
<br />

<p>
  <img src="https://i.imgur.com/p9znFwj.jpeg" height="50%" width="50%" alt="Inbound rule"/>
</p>
<p>
We are going to change the inbound rule again to allow the ICMP traffic to resume. Now, whenever this happens, you will see the ping start to go down the page again as well as the reply and request start to resume with the ICMP traffic. 
</p>
<br />

<h4> Observe DNS, DHCP, SSH, and RDP traffic:</h4>
<p>
  <img src="https://i.imgur.com/S5OUaSB.jpeg" height="50%" width="50%" alt="RDP Traffic"/>
  <img src="https://i.imgur.com/K2ncQGm.jpeg" height="50%" width="50%" alt="DNS Traffic"/>
  <img src="https://i.imgur.com/9EGw44k.jpeg" height="50%" width="50%" alt="DHCP Traffic"/>
  <img src="https://i.imgur.com/6HM3nvR.jpeg" height="50%" width="50%" alt="SSH Traffic"/>
</p>
<p>
Here, we are filtering traffic for four different protocols: RDP, DNS, and DHCP. Watching the traffic being sent and received from private IP addresses/IP addresses. For RDP, you can either type just RDP or tcp.port==3389. For DNS, which is TCP and UDP port 53, typing DNS will work. Lastly, for DHCP typing udp.port==68 and udp.port==67 will work as well. For SSH, you can just type in SSH and that will work.  
</p>
<br />

