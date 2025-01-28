<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Group Policy and Managing Accounts In On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines configuring Group Policy, unlocking accounts, and resetting passwords in Active Directory.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Steps</h2>

- Login to Domain Controller
- Configure Group Policy to Lockout After 5 Attempts
- Pick a User and Attempt to Login 6 Times With Bad Password
- Reset the User's Password, Unlock the Account In Active Directory, then Login 

<h2>Deployment and Configuration Steps</h2>

<p>
<img width="912" alt="Screenshot 2025-01-28 at 9 56 53 AM" src="https://github.com/user-attachments/assets/aecbc091-4971-4a2c-8545-4c3e24f41970" />
</p>
<p>
I logged into my Windows Server Domain Controller VM via remote desktop. Then I opened Group Policy Management Console (GPMC) and went to edit my default domain policy. I selected "computer configuration", "policies", "Windows Settings", "Security Settings", "Account Policies", "Account Lockout Policy". I set the account lockout threshold to 5 invalid logon attempts with a 30 minute lockout duration. 
</p>
<br />

<p>
<img width="1436" alt="Screenshot 2025-01-28 at 10 09 20 AM" src="https://github.com/user-attachments/assets/d9599025-f67a-4548-9cb1-f6d9bcd58827" />
<img width="263" alt="Screenshot 2025-01-28 at 10 17 25 AM" src="https://github.com/user-attachments/assets/5fef408e-392d-447e-8be5-cd3267420450" />
<p>
After that, I logged in as an Admin into my Client-1 Windows 10 VM as an admin. Rather than wait the 90 minutes for the group policy to take effect, I ran the command "gpupdate /force" to enable it immediately. I then selected one of the users I generated in a previous project from a Powershell script and attempted to login to Client-1 six times with a bad password. On the 6th time, remote desktop gave me a message explaining the account has been locked out.
</p>
<br />

<p>
<img src="https://i.imgur.com/FzBkrD4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From here I went back into my Domain Controller and found the user that was locked out. I right clicked their name and hit "Reset Password". I then resest the password and unlocked their account. Lastly, I confirmed I could login to Client-1 with the new password.
</p>
<br />
