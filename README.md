<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines configuring Group Policy, enabling/unlocking accounts and resetting passwords in Active Directory.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Steps</h2>

- Install Active Directory
- Create a Domain Admin User
- Join a PC to My Domain and Set Up Remote Desktop For Non-Admin Users
- Run Powershell Script to Create Additional Users

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/ziLAQkg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I first installed Active Directory Domain Services to my Windows Server VM. I then promoted the server to a domain controller, creating a new forest titled "mydomain.com". Then I restarted the machine and logged back in as a domain user.
</p>
<br />

<p>
<img src="https://i.imgur.com/AiZ5cQq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After that, I went into Active Directory Users and Computers (ADUC) and created two new Organizational Units (OUs), _EMPLOYEES and _ADMINS. Next, I created a new employee named "Davin" and added him to the "Domain Admins" security group. I logged out and then logged back in on remote desktop as mydomain.com\davin_admin, which will be my admin account from now on. 
</p>
<br />

<p>
<img src="https://i.imgur.com/FzBkrD4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I then joined my Windows 10 VM, "Client 1" to my domain (mydomain.com). I previously had set Client 1's DNS settings to my Domain Controller's private IP address. After logging in as an admin, I went to Client 1's system properties and allowed domain users access to remote desktop. I then logged back into my Domain Controller as davin_admin. I subsequently ran a Powershell script as an administrator to create 10,000 accounts for the _EMPLOYEES OU. Lastly, I confirmed the functionality of the user accounts by signing in with one of them. 
</p>
<br />
