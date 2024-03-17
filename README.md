<h1>Active Directory Home Lab</h1>

<h2>Description</h2>
We deploy Active Directory within a home lab setting using Oracle VirtualBox. By establishing a domain controller to host Active Directory, we leverage group policies, enabling a multi-user client to obtain an IP address and facilitate communication with both the private and external network of the domain.


<h2>Languages and Utilities Used</h2>

- <b>Oracle VirtualBox</b> 
- <b>Active Directory</b>  

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
Logout, then log back in under our domain admin account
<br />
<br />
Login:  <br/>
<img src="https://i.imgur.com/V4oMvQ0.png" height="80%" width="80%" alt="ADDS_Client Steps"/>
<br />
<br />
Proceed to the server manager, under "add roles and features" install "Remote Access," this contains our NAT/RAS services
<br />
<br />
Remote Access:  <br/>
<img src="https://i.imgur.com/Hi1DQuo.png" height="80%" width="80%" alt="ADDS_Client Steps"/>
<br />
<br />
Installation:  <br/>
<img src="https://i.imgur.com/EKxpRL2.png" height="80%" width="80%" alt="ADDS_Client Steps"/>
<br />
<br />
Proceed to configure NAT
<br />
<br />
Tools, Routing and Remote Access:  <br/>
<img src="https://i.imgur.com/68Hzufx.png" height="30%" width="30%" alt="ADDS_Client Steps"/>
<br />
<br />
Configure and Enable Routing and Remote Access:  <br/>
<img src="https://i.imgur.com/8CM9twm.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
Restarted Server
<br />
<br />
Configure NAT:  <br/>
<img src="https://i.imgur.com/7AUR1eW.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
After NAT has been configured, proceed to the server manager, under "add roles and features" to install DHCP
<br />
<br />
Installation of DHCP:  <br/>
<img src="https://i.imgur.com/xJdEg8z.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
Proceed to open DHCP Services and add a new scope to the DHCP  
<br />
<br />
New Scope:  <br/>
<img src="https://i.imgur.com/5trsCbF.png" height="40%" width="40%" alt="ADDS_Client Steps"/>
<br />
<br />
After adding a new scope to the DHCP, it needs to be authorized DHCP to respond to client requests
<br />
<br />
Authorization:  <br/>
<img src="https://i.imgur.com/rT44i4o.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
Preloaded a list of accounts into the active directory users to simulate a corporate environment
<br />
<br />
Populated Users:  <br/>
<img src="https://i.imgur.com/2RlJDy6.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
Open up VirtualBox and create a new VM to house our Windows 10 Client
<br />
<br />
New Windows 10 client:  <br/>
<img src="https://i.imgur.com/StH3Ro5.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
Configured an Interal NIC for our Windows 10 client
<br />
<br />
Network Interface Card:  <br/>
<img src="https://i.imgur.com/Sq2VZRU.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
New Windows 10 client:  <br/>
<img src="https://i.imgur.com/StH3Ro5.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
Open up the client and install Windows 10
<br />
<br />
Installation of Windows 10:  <br/>
<img src="https://i.imgur.com/9PAjbBI.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
New Windows 10 client:  <br/>
<img src="https://i.imgur.com/StH3Ro5.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
Configured an Interal NIC for our Windows 10 client
<br />
<br />
After Windows 10 is installed on our client, go to system, "Rename this PC(Advanced)" rename to, "CLIENT1" and join our domain
<br />
<br />
Joining domain:  <br/>
<img src="https://i.imgur.com/bKIeHc9.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
Proceed back to the domain controller, under DHCP "address leases" we can see our client has an IP address
<br />
<br />
Leased Address:  <br/>
<img src="https://i.imgur.com/AP1eXo7.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
Within our windows 10 client, open up command prompt and type "ipconfig," we can see our client's IPv4 address matches that of the DHCP leased address
<br />
<br />
Client Command Prompt:  <br/>
<img src="https://i.imgur.com/6uWLruT.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
<br />
<br />
Our client has now been connected to the domain and is recieving it's IP address from the DHCP of the domain controller and can succesfully ping the external network through our NAT configuration
<br />
<br />
<img src="https://i.imgur.com/6yNzsaz.png" height="60%" width="60%" alt="ADDS_Client Steps"/>
</p>
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
