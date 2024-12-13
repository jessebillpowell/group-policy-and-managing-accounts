<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Enabling and Unlocking Accounts & Resetting Passwords and Group Policy (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/N1KRYjz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
First, we want to enter "gpmc.msc" under RUN in the start menu to open the Group Policy Management Console from the DC-1 Domain Controller.
</p>
<br />

<p>
<img src="https://i.imgur.com/iHJOGFd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, we want to expand several of the domains, and sub-domains in the GPMC. 

 First, right-click on "Default Domain Policy," listed under DOMAINS > mydomain.com, and click on edit. While editing, expand: Computer Configuration > Policies > Windows Settings > Security Settings > Account Lockout Policy.

 Next, cick on Account Lockout Threshold and change the threshold to configure the password to use a lockout after "X" amount of failed attempts. I chose 5 for "X" so that accounts will be locked out after five failed attempts.  
</p>
<br />

<p>
<img src=https://i.imgur.com/MDtCHRz.png"" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
It is now listed under the Default Domain Policy under Group Policy Management. The settings can be changed to whatever the administrator would like to for account lockout settings.  
</p>
<br />

<p>
<img src="https://i.imgur.com/ww9maAa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, we want to ensure that Client-1's DNS settings are using DC-1'S private IP address. This should have already been done in the preparing Active Directory portion of the lab, but good to make sure. Then login into Client-1 using the local admin account "labuser" and join it to the domain "mydomain.com." Afterwards, we re-start the Client-1 virtual machine. Then we login into DC-1 Domain Controller as jane_admin, look under Windows Administrative Tools - Active Directory Users & Computers and look to verify that Client-1 is listed in the "CLIENTS" tab. Lastly, create an OU called _CLIENTS and move Client-1 into this OU. 
</p>
<br />

<p>
<img src="https://i.imgur.com/w0L1lEW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this step, you want to enter "Domain Users" as users that have access to use Remote Desktop, so that domain users may access the Client-1 from Remote Desktop.
</p>
<br />

<p>
<img src="https://i.imgur.com/RWpa8i4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, Powershell ISE will be opened as an administrator. We will use a script that auto-create random user names of 10,000 employees and place these randown names in the Organizational Unit "_EMPLOYEES." The employee accounts can be checked by looking under Windows Administrative Tools - Active Directory Users & Computers and look to verify the random users. We will choose a random user, "fex.pih," logout out jane_admin, login as fex.pih and add the password for all emplyees of "Password1."
</p>
<br />
