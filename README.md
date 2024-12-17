# Azure-Network-Protocols
<p align="center">
<img src="https://i.imgur.com/3ASB3WY.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups and Inspecting Traffic Between Azure Virtual Machines</h1>
We will observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Resources)
- Remote Desktop  (RDP)
-  Command-Line Tools (CMD)
-  Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Observe ICMP Traffic , SSH Traffic, DHCP Traffic, DNS Traffic, RDP Traffic


<h2></h2>


 In Azure we are going  create a resource group so we can initalize both of our virtual machines. Once we have our resource group made we then want to make our first virtual machine. The first virtual machine we are going to make is a Windows 10 virtual machine. Select the resource group you made,  and then name the virtual machine windows-vm ,put in the region as east-us 2. Under image make sure you select Windows 10 Pro, version 22H as the operating system. As for the size of the machine we are going to want to use atleast 2 vcpus, and 8 gb of memory. Create a username and password , click next and advance to the Networking tab.

<p>
<img src="https://i.imgur.com/0BJ4CEM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  

<p>
<img src="https://i.imgur.com/JKvpQo7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<p>
  
 After this step we are going to click on next until we get to the networking page and it should automatically create a virtual network and subnet for us. 
  

<p>
<img src="https://i.imgur.com/tt5dKZF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Click review and create .
  
  Now we will create the second Virtual Machine, but this time it will be a Ubuntu Server 20.04 LTS machine. It will be the same process as creating our first machine but instead we are going to switch the SSH public key to password instead. 
  
<p>
<img src="https://i.imgur.com/s0GxVvx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <img src="https://i.imgur.com/mLrA4C6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<p>
 <img src="https://i.imgur.com/bikM8P2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/g9LWesz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Click next until we get to the networking .
  </p>
<br />
</p>


  
  The networking should automatically give us the virtual network from the Virtual Machine as well as the subnet. 
  
<p>
<img src="https://i.imgur.com/Gsy2yVC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  Click review and create, We have created our second Virtual Machine.
</p>
<br />

 </p>
<p>
 </p>
<p>
 
 Now that we have both virtual machines up and running we are going to connect to our Windows 10 vm using the remote desktop connection (RDP).

 </p>
<br />

 <img src="https://i.imgur.com/KcQkkyV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 </p>
<br />

 
 Once we are connected we are going to go to our browser and download and install Wireshark. https://www.wireshark.org
 <b/>
 
 </p>
<p>
 </h1>
 </p>
<p>
 
 "Wireshark is a free and open-source packet analyzer. It is used for network troubleshooting, analysis, software and communications protocol development, and education." 
 </p>
<br />
</p>
<br />
<p>
 
 Open wireshark and filter for ICMP traffic only.
 </p>
<br />

 
 <p>
<img src="https://i.imgur.com/ZyOZ0qS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 </p>
<br />

   We are going to want to retrieve the private IP address of our Ubuntu Virtual Machine and then attempt to ping it from within our Windows 10 Virtual Machine using wireshark. To ping the private IP address of the Ubuntu machine open Powershell on the Windows machine and type: ping 10.0.0.5 or your private IP address from the Ubuntu machine.
 
<p>
<img src="https://i.imgur.com/kWg0lBE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 
<p>
<img src="https://i.imgur.com/UeTa7Ns.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 
  In  Powershell ping www.google.com and observe the traffic in wireshark.
 
   We then are going to initiate a non-stop ping from our Windows 10 Virtual Machine to our Ubuntu Virtual Machine.
 
   Open the Network Security Group of our Ubuntu machine and disable incoming (inbound) ICMP traffic. To disable incoming ICMP traffic click "Add" new rule and copy everything exactly from the picture. Once that is done you can create the rule and it will create automatically and show up as a new rule.
 
 <p>
<img src="https://i.imgur.com/iMHClQN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <img src="https://i.imgur.com/lKGTmIY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
<img src="https://i.imgur.com/cucYV87.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 
 Now that we have disabled incoming ICMP traffic from VM2 if we go back to VM1 you can see the ping request is timing out. 
 <br />
</p>
<img src="https://i.imgur.com/0PpPJ5Y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p>
   Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)
Stop the ping activity
 
  The next thing we are going to do is Observe SSH Traffic.
 
 
 

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
  
  
