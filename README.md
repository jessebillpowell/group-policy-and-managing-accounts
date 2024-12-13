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
It is now listed under the Default Domain Policy under Group Policy Management. The settings can be changed to whatever the administrator would like to for account lockout settings. Eventually, these settings will take effect, but it is not immediate. If we want it done immediately, this can be done by logging into Client-1 as an admin, like Jane Doe, opening up command line, and entering gpupdate /force. 
</p>
<br />

<p>
<img src="https://i.imgur.com/wlT8HqA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We can unlock fex.pih's account from Active Directory by going back in the Domain Controller DC-1 > goto Active Directory Users and Computers > mydomain.com > _EMPLOYEES > double click on the user whose account is locked out (fex.pih) > click on the account tab for fex.pih > and check on the unlock account box, and press apply and ok.
</p>
<br />

<p>
<img src="https://i.imgur.com/k2YhIeW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />

<p>
<img src="https://i.imgur.com/NPr5f2Z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Similarly, you can also reset passwords doing a similar process to unlocking an account. To reset the password (or unlock the account), goto Active Directory Users and Computers > mydomain.com > _EMPLOYEES > right click on the user whose account is locked out (fex.pih) > click on the reset password option for fex.pih > and then give user a new password from the box and you can also unlock the account from this box and hit ok.

 You could also enable and disable a users account doing the same exact process that was done to reset the password, except when you right click on the users name, instead of clicking on reset password, you click on disable account or enable account, whichever you are looking to do.
</p>
<br />

<p>
<img src="https://i.imgur.com/hloyWoh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
If we want to observe the logs of all of the activity from login attempts (successful and unsuccessful), reseting of passwords, unlocking of accounts, etc, this can be done going to the Event Viewer app in the Client VM (Client-1). You can open it from the client's profile, open Event Viewer as an adminsitrator, and then a box will open up for the administrator to put in their username and password. I entered the credentials for Jane Doe, and saw all of the log activity of fex.pih.
</p>
<br />
