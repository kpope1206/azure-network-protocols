# azure-network-protocols<p align="center"> 
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1> 
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

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

Part 2
https://portal.azure.com/
(Observe ICMP Traffic)
6. If using Mac, install Microsoft Remote Desktop
7. Use Remote Desktop to connect to your Windows 10 Virtual Machine
8. Within your Windows 10 Virtual Machine, Install Wireshark
9. Open Wireshark and start packet capture
10. Within Wireshark, filter for ICMP traffic only
11. Retrieve the private IP address of the Ubuntu VM (linux-vm) and attempt to ping it from within the Windows 10 VM
   1. Observe ping requests and replies within WireShark
12. From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark
   
13. Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM
   1. Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic
   2. Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity
   3. Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is
   4. Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)
   5. Stop the ping activity


(Observe SSH Traffic)
14. Log back into the windows-vm
15. Back in Wireshark, start a packet capture up
16. Filter for SSH traffic only
17. From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)
18. Open PowerShell, and type: ssh labuser@<private IP address>
   1. Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark
   2. Exit the SSH connection by typing ‘exit’ and pressing [Enter]


(Observe DHCP Traffic)
19. Back in Wireshark, filter for DHCP traffic only
20. From your Windows 10 VM, attempt to issue your VM a new IP address from the command line
   1. Open PowerShell as admin and run: ipconfig /renew
   2. Observe the DHCP traffic appearing in WireShark


Observe DNS Traffic)
21. Back in Wireshark, filter for DNS traffic only
22. From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are



