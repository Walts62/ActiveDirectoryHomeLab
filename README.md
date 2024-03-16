<h1>Active Directory Home Lab</h1>

<h2>Description</h2>
We deploy Active Directory within a home lab setting using Oracle VirtualBox. By establishing a domain controller to host Active Directory, we leverage group policies, enabling a multi-user client to obtain an IP address and facilitate communication with both the private and external network of the domain.


<h2>Languages and Utilities Used</h2>

- <b>Oracle VirtualBox</b> 
- <b>Active Directory</b> 
- <b>PowerShell</b> 

<h2>Environments Used </h2>

- <b>Windows Server 2019</b>
- <b>Windows 10</b>



<h2>Program walk-through:</h2>

<p align="center">
Launched VirtualBox and created our Windows Server client: <br/>
<img src="https://i.imgur.com/vkRVDVc.png" height="80%" width="80%" alt="ADDS_Client Steps"/>
<br />
<br />
Configured two Network Interface Cards (NIC), one will connect our domain controller to the external network (which will run NAT), while the second will connect to the internal VM network.
<br />
<br />
First Network Interface Card:  <br/>
<img src="https://i.imgur.com/BuE2bZj.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
Second Network Interface Card: <br/>
<img src="https://i.imgur.com/2DSGs0U.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
Proceed to open the VM and install Windows Server
<br />
<br />
Installation of Windows Server 2019:  <br/>
<img src="https://i.imgur.com/lnwZDSV.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
After setup, we opened the network settings to view our NICs. 
<br />
<br />
Network Interface Cards:  <br/>
<img src="https://i.imgur.com/iToGcKc.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
You will be able to distinguish each NIC from each other by seeing that the secondary NIC has a 169.254.x.x address (an Automatic Private IP Address [APIPA]). This lets us know this will be our internal network card, it will be assigned an IP address and DNS.
<br />
<br />
Secondary Network Interface Card Details:  <br/>
<img src="https://i.imgur.com/iqDAwE9.png" height="50%" width="50%" alt="ADDS_Client Steps"/>
 <br />
<br />
 Reconfigured NICs:  <br/>
<img src="https://i.imgur.com/4gEKT5k.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
Proceed to the server manager, then "Add roles and features" and install Active Directory and Domain Services
<br />
<br />
Installation of Active Directory Domain Services:  <br/>
<img src="https://i.imgur.com/cYDEg0O.png" height="80%" width="80%" alt="ADDS_Client Steps"/>
<br />
<br />
Promote server to domain controller:  <br/>
<img src="https://i.imgur.com/qOLo7bJ.png" height="80%" width="80%" alt="ADDS_Client Steps"/>
<br />
<br />
Restarted Server
<br />
<br />
Login Prompt:  <br/>
<img src="https://i.imgur.com/7KzkknF.png" height="80%" width="80%" alt="ADDS_Client Steps"/>
<br />
<br />
After login, proceed to "Active Directory Users and Computers" and under "mydomain.com" create a new organizational unit, "_ADMINS" to host the domain admin account
<br />
<br />
Organizational Unit:  <br/>
<img src="https://i.imgur.com/KgSACTh.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
Account configured:  <br/>
<img src="https://i.imgur.com/NwuRLR1.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
After creation of the account, head into properties of the user, "member of" and make it a domain admin
<br />
<br />
Added to "Domain Admins":  <br/>
<img src="https://i.imgur.com/ZqzgaWs.png" height="50%" width="50%" alt="ADDS_Client Steps"/>
<br />
<br />

 
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
