<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Deploying Active Directory in the Cloud (Azure)</h1>
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
<img src=https://i.imgur.com/H7PgUQ6.png"" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In the first step, we want to login to DC-1 (Domain Controller) and install Active Directory Domain Services. Then Promote DC-1 to a Domain Controller and configure a new forest with a dom ain (mydomain.com\) was used. The default account was logged out, the Remote Desktop was re-started to ensure these changes took effect, and then logged in under the new domain, as mydomain.com\labuser, so that logging in as a domain user is allowed now. 
</p>
<br />

<p>
<img src="https://i.imgur.com/ITqySOz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this step, we created an administrative user (Admin User) and Organizational Units.
 
  *Create an Organizational Unit (OU) called _EMPLOYEES for employee users
  
  *Create an OU called _ADMINS for administrative users
  
  *Create a user named Jane Doe. Jane Doe will be added to the _ADMINS OU. Also, for this user to have admin privileges, Jane Doe must also be added to "Domain Admins"   
   Security Group. 
  
After creating these OU's, we log out of the DC-1 as labuser, and then log back in, as Jane Doe, using the domain and user name for Jane Doe (mydomain.com\jane_admin).
</p>
<br />

<p>
<img src="https://i.imgur.com/As8fhd3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

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
