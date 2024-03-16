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
Configured Two Network Interface Cards, one will connect our domain controller to the external network (which will run NAT), while the second will connect to the internal VM network.
<br />
<br />
First NIC:  <br/>
<img src="https://i.imgur.com/BuE2bZj.png" height="80%" width="80%" alt="ADDS_Client Steps"/>
<br />
<br />
Second NIC: <br/>
<img src="https://i.imgur.com/2DSGs0U.png" height="80%" width="80%" alt="ADDS_Client Steps"/>
<br />
<br />
Installation of Windows Server 2019:  <br/>
<img src="https://i.imgur.com/RJabM3i.png" height="80%" width="80%" alt="ADDS_Client Steps"/>
<br />
<br />
After setup, we opened the network settings to reconfigure our NICs
<br />
<br />
Reconfigured NICs:  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="ADDS_Client Steps"/>
<br />
<br />

<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="ADDS_Client Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="ADDS_Client Steps"/>
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
