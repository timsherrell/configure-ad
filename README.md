
<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- Command Prompt
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (22H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Installed Active Directory
- Verified connectivity
- Joined client VM to domain
- Created AD users with Powershell script
- Allowed domain users to remote to client


<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://github.com/timsherrell/configure-ad/assets/144177449/dfd44420-a79c-434e-be79-b5294a86c34f"/>
</p>
<p>
Remoted into Windows Server and installed Active Directory Domain Services. 
</p>
<br />

<p>
<img src="https://github.com/timsherrell/configure-ad/assets/144177449/a0c52b6a-4c05-4616-924b-4bbcd78d5815"/>
</p>
<p>
Promoted Windows Server to domain controller.
</p>
<br />

<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/df475e20-a740-4bbb-8d0c-6249bf0a5351" />
</p>
<p>
  Verified connectivity between server and client machines.
</p>
<br />

<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/4ecaf563-8db9-472a-aa15-37d0611f635b" />
</p>
<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/48a8ba4d-6978-4546-a488-26dfbefd06eb" />
</p>
<p>
  Configured client DNS to domain controller's private IP and joined client to timsh.com domain 
</p>

<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/13e953f3-6aaf-470f-81db-514b7b7c17da" />
</p>
<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/fa49ba45-18fc-4f9d-a1e7-58bc1da1739f" />
</p>
<p>
  Used a Powershell script to create many users in AD. I did not create this script. I edited the $PASSWORD_FOR_USERS variable to a password I would remember and the $NUMBER_OF_ACCOUNTS_TO_CREATE varible to a smaller number so the script would finish running sooner.   
</p>

<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/e7ef3f3d-6273-4901-b04d-a54a721ee565" />
</p>
<p>
  Configured remote desktop to allow any domain user to remote to client. 
</p>

