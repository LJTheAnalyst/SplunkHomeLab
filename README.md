<h1>Splunk Cloud in VirtualBox - Mastering Searches, Commands, Reports, and Dashboards</h1>

<h2>Description</h2>
The core focus for this project is to gain practical experience with Splunk Cloud by setting up a virtual environment in Oracle VM VirtualBox and exploring core functionalities in detail like searches, commands, reports, and dashboards. For this home lab I will use the Search App to add data to my Splunk deployment, search the data with various commands, save the searches as reports, and create dashboards. The searches included in the lab will derive from uploaded indexted data from log files. Commands will be used to create specilaized searches which will provide data that'll be used for the creaation of detailed reports and charts. Lastly, the Dashboard Editor will be used to create a new dashboard which I will add the saved reports, charts, and new search to. 
<br/>


<h2>Key Learnings</h2>

- Hands-on experience with Splunk Cloud search app function and create visualizations from log files to extract insights from data.
- Reporting and dashboard creation used for visual data analysis and communicating to key stakeholders.
- Navigation, familiarity, and use cases of the Splunk platform.
- Understanding of virtual machine setup and networking in VirtualBox.
<br/>


<h2>Utilities Used</h2>

- <b>Splunk Cloud</b>
- <b>Log Files</b>


<h2>Environments Used </h2>

- <b>Oracle VM Virtualbox</b> 
- <b>Windows 11</b>

<h2>Links</h2>

- <b>Splunk Cloud:</b> https://www.splunk.com/en_us/download/splunk-cloud.html
- <b>Oracle VM Virtualbox:</b> https://www.virtualbox.org/


<h2>Program walk-through:</h2>

<p align="center">

<h3><b>Part 1: VirtualBox Configuration and Data Upload</b></h3>
<br/>

Oracle VM VirtualBox is the Virtual Machine (VM) that I will download, configure, and manage this lab. I also downloaded the VirtualBox Extension Pack to support the VM. <br/>
<img src="https://imgur.com/OeSOJfK.png" height="80%" width="80%" alt="Nessus Essentials"/> 
<br />
<br />
The first step of this lab is uploading the data that I will be querying and analyzing. I was able to access the the 'add data' feature from my Splunk cloud home page. The files that will be uploading includes access.log files, secure.log files, and vendor_sales.log files from mail servers and web accounts. Once the files were uploaded, I performed a basic search to ensure a successful upload.  <br/>
<br><img src="https://imgur.com/9FyAwXS.png" height="80%" width="80%" alt="Nessus Essentials"/><br/>
<br><img src="https://imgur.com/GUUa05K.png" height="80%" width="80%" alt="Nessus Essentials"/><br/>
<br><img src="https://imgur.com/ZgUNOdq.png" height="80%" width="80%" alt="Nessus Essentials"/><br/>
<br><img src="https://imgur.com/csXbN2D.png" height="80%" width="80%" alt="Nessus Essentials"/><br/>
<br><img src="https://imgur.com/KLZgxHm.png" height="80%" width="80%" alt="Nessus Essentials"/><br/>
<br><img src="https://imgur.com/G7EM1dv.png" height="80%" width="80%" alt="Nessus Essentials"/>
<br />
<br />


<h3><b>Part 2: Exploring the Search App</b></h3>
<br />

For part 2 I will be exploring the Search App by searching for keywords and also optimizing my search criteria by using specified time periods. <br/>
<br><img src="https://imgur.com/C4rGZw9.png" height="80%" width="80%" alt="Nessus Essentials"/><br/>
<br>To increase the number of returned events, I adjusted the time frame from Last 24 hours to Yesterday. As displayed below, the amount of events increased from 2,897 to 4,107.<br/>
<br><img src="https://imgur.com/kfGnF3Z.png" height="80%" width="80%" alt="Nessus Essentials"/><br/>
<br>To run a search with specified relative time ranges I ran a search over the last two days, created the following search query. <br/>
<br><img src="https://imgur.com/Zbmfp9b.png" height="80%" width="80%" alt="Nessus Essentials"/><br/>
<br>To run a search with specified date and time ranges, I created a custom time time range. For example, to troubleshoot an issue that took place January 6, 2023 about 9:30 AM, I specified the earliest time of 01/06/2024 7:30:00 and the latest time of 01/06/2024 10:30:00 to show the events immediately before and after the issue took place.<br/>
<br><img src="https://imgur.com/ieESetm.png" height="80%" width="80%" alt="Nessus Essentials"/><br/>
<br />
<br />


<h3><b>Part 3: Searching the Data</b></h3>
<br />

Next I created a dedicated domain admin account. This was done by creating an Organizational Unit (OU), which I named ‘Admin’, then creating a user to add to the Admin OU. For the purpose of this lab, the password policy was set to Password never expires. Once the user was successfully created, it was then added to the Domain Admins group. Finally, to ensure that the user was successfully created I logged into windows using credentials of the newly created user. <br/>
<img src="https://imgur.com/AQGZJn4.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/I4vWPQB.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/0P3qeaA.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/rg1M70h.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/37uVYKg.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/1Svj0cg.png" height="80%" width="80%" alt="Nessus Essentials"/>
<br />
<br />
To allow the soon to be created Client to have access to be on the private virtual network and still be able to access the internet through the domain controller I installed the Remote Access Server (RAS) and Network Address Translation (NAT) through the Server Manager. The steps were as followed: Select Remote Access, add routing, selected Network Address Translation (NAT), and selected to use the previously configured IP addresses. <br/>
<img src="https://imgur.com/VF5Pk2R.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/laLmN9a.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/kmzXbSH.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/NcYvzoM.png" height="80%" width="80%" alt="Nessus Essentials"/>
<br />
<br />
The next step is to Setup DHCP Server on the domain controller which will allow computers/ client computers on the network to automatically get their IP Address on the internal network. The steps were as followed: select DHCP Server, set a new scope which included an IP range of 172.16.0.100 – 172.16.0.200, a length of 24, and a subnet mask of 255.255.255.0. A Lease Duration was set to 8 days. The new scope was then successfully created. <br/>
<img src="https://imgur.com/etcPtVl.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/FBFBJw4.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/AU1zc9H.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/VpMgj1X.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/ZW8DpVZ.png" height="80%" width="80%" alt="Nessus Essentials"/>
<br />
<br />
A PowerShell Script was used to create 1,052 users to add to Active Directory. A PowerShell script was created to set the password for all 1,052 users to ‘Password1’ and retrieve the list of users from a .txt file that was created. Furthermore, a loop script was used to format the first name, last name, and username for each user. To bypass the security feature in PowerShell I had to unrestrict the security policy. The script was then run to add the users to Active Directory. <br/>
<img src="https://imgur.com/PuoRSJC.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/Pt4vuBy.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/Ky3j4Bo.png" height="80%" width="80%" alt="Nessus Essentials"/>
<br />
<br />
To verify that all users were added to Active Directory, I opened the created ‘_USERS’ Organizational Unit. All users were successfully added. <br/>
<img src="https://imgur.com/Z5HDcJT.png" height="80%" width="80%" alt="Nessus Essentials"/>
<br />
<br />
A separate VM was created and configured for the Client in which Windows 11 Pro was installed. This VM will be used to connect to the domain. During the installation of Windows 11, there was an error in need of troubleshooting. To troubleshoot this error, I opened the Registry Editor from the command line window, created a new key and named it ‘LabConfig’ for the local machine then create four new DWORD (32-bit) Values; Bypass BypassTPMCheck, BypassCPUCheck, BypassRAMCheck, and BypassSecureBootCheck. The troubleshoot was successful, and I was then able to finish installing Windows 11 to the VM.  <br/>
<img src="https://imgur.com/XvcbwJc.png" height="80%" width="80%" alt="Nessus Essentials"/> 
<img src="https://imgur.com/opAuQ9m.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/T19k2lR.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/71K3NRo.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/mh8Vzvp.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/dUB6nN4.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/5ZNxwzS.png" height="80%" width="80%" alt="Nessus Essentials"/>
<br />
<br />
Next, I verified that the IP configuration is correct and I’m able to ping something on the internet to verify that DNS Server is working. I was able to successfully ping both, www.google.com and also the domain I created. <br/>
<img src="https://imgur.com/2XlTiEX.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/z9yekyf.png" height="80%" width="80%" alt="Nessus Essentials"/> 
<img src="https://imgur.com/v4s2lXG.png" height="80%" width="80%" alt="Nessus Essentials"/>
<br/>
<br/>
Next, I changed the default hostname from DESKTOP-LTUV7 to Client1 and added Client1 to the domain (mydomain.com). <br/>
<img src="https://imgur.com/2i1sl46.png" height="80%" width="80%" alt="Nessus Essentials"/> 
<img src="https://imgur.com/qtXqGVO.png" height="80%" width="80%" alt="Nessus Essentials"/>
<br />
<br />
I then logged back into the Server Manager and verified that the client computer (Client1) that I created was added to the domain and I’m able to login to the client computer with a created account. Using the Windows 11 VM (Client 1), I then attempted to login with the created user ‘astuart’ using the created credentials. The login attempt was successful. <br />
<img src="https://imgur.com/CNt6ht1.png" height="80%" width="80%" alt="Nessus Essentials"/>
<img src="https://imgur.com/iFsRsgl.png" height="80%" width="80%" alt="Nessus Essentials"/> 
<img src="https://imgur.com/ZopQzGu.png" height="80%" width="80%" alt="Nessus Essentials"/>
<br />
<br />
</p>
