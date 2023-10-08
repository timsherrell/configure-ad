
<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure), Part 1</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022

<h2>High-Level Deployment and Configuration Steps</h2>

- Install Active Directory
- Promote Server to Domain Controller 
- Open Active Directory Users and Computers 

<h2>Deployment and Configuration Steps</h2>

<p>
To begin, we copy the public IP address from our Windows Server in Azure and paste it into our Windows Remote Desktop interface. I like to just type "rd" into the Windows search bar to bring up Remote Desktop Connection. Then paste the IP into the Computer field. 
</p>
<p>
<img src="https://github.com/timsherrell/configure-ad/assets/144177449/68f7a327-2a8c-40ac-b7b6-02bdb0ea8395" />
</p>
<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/98b958ff-297f-4e02-b23d-802f80555eb7" />
</p>
<br />
<p>
  A box talking about certificate errors will pop up. We can safely ignore this. It's not going to affect anything. Click the yes button to continue. 
</p>
<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/62024fab-24a8-4cb3-ad88-184087b119b3" />  
</p>
<br />

<p>
  Once you're on the Server desktop you should see the Server Manager pop up automatically. If it doesn't pop up automatically click on the Windows Start button. From there you should be able to click on/open the Server Manager. Click on Add Roles and Features highlighted here. 
</p>
<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/ffb2414a-ce4d-4f25-8930-0a6192c5f7e0" />
</p>
<p>
  The Add Roles and Features Wizard will pop up.
</p>
<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/a7c7524f-855c-4bc0-a75b-44f3d4da73ca" />
</p>
<p>
  Click the next until this screen comes up. Then click the checkbox next to Active Directory Domain Services. 
</p>
<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/c4e5160f-1d15-47ef-965a-9082fc9e9c71" />
</p>
This will cause another box to appear. In this box click the Add Features button. The box will disappear. Then click next till you see the install button become available to click in the wizard. The installation may take a couple of minutes.  
<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/44276127-6490-4faa-bf3e-3fff588f7cb2" />
</p>
<p>
<img src="https://github.com/timsherrell/configure-ad/assets/144177449/dfd44420-a79c-434e-be79-b5294a86c34f"/>
</p>
<br />
<p>
  Next, we will promote the Server to a Domain Controller (DC).
</p>
<p>
  Look in the upper right-hand corner of the Server Manager Window for a flag with a notification next to it. Click on the flag and then click the text in the pop-up that says "Promote this server to a domain controller." 
</p>
<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/2d3e442a-86e5-416b-b58b-3e8f34032bf4" />
</p>
This will bring up the Active Directory Domain Services Configuration Wizard. Click the Radio button next to "Add a new forest." In the Root domain name field, we will type the name of our domain. This will be in the form of "mydomain.com." We can use any name we want followed by ".com." We will use this in part 2 of this tutorial to add a workstation (Windows 10 Pro machine) to our domain. 
<p>
<img src="https://github.com/timsherrell/configure-ad/assets/144177449/a0c52b6a-4c05-4616-924b-4bbcd78d5815"/>
</p>
<br />
<p>
  Click next to come to the Domain Controller Options page. We need to create a password for the Directory Services Restore Mode (DSRM). We won't use this password again in this tutorial, but good practice demands we use a password we will remember. As a side note, it is best during this tutorial to save your usernames and passwords in a text file you can refer to later. This is not a good practice in real life but it will be very helpful just in this tutorial. 
</p>
<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/af09c5e2-595a-4acf-be68-026d605db17d" />
</p>
<br />
<p>
  Once that is done, click next to come to the Additional Options page. We're just waiting for the NetBIOS field to populate with our domain name. Then click next until the install button isn't grayed out anymore.    
</p>
<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/38c74e89-92d7-493d-8f6c-94fe3f60c1f1 " />
</p>
<p>
  Then click install. This may take a minute to finish. Then the server will restart and the remote connection will close. 
</p>
<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/d02799c0-cd5c-4e7f-992f-1336b1b1b454" />
</p>
<br />
<p>
  We'll need to remote back into the Server again. The Remote Desktop Connection window should still have the IP address saved from the last time we used it. You can navigate to your machine in the Azure portal (portal.azure.com) if you want to double-check the IP address.       
</p>
<p>
  When you remote back in you'll see the same box as before where you will enter your credentials. We won't be able to log in the same way we did before. The server has been promoted to a domain controller, so we have to log in to the domain. Click "More choices" near the bottom of the window. 
</p>
<p>
 <img src="https://github.com/timsherrell/configure-ad/assets/144177449/7104c27b-40cd-434e-b1fc-8808647f0e3c" /> 
</p>
<p>
  Now click where it says "Use a different account."  
</p>
<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/18e91b4f-c104-4dd2-88ad-214c980c000e" />
</p>
<p>
  Finally, type your domain name with your original login and password like in the image below (timsh.com\labuser).
</p>
<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/0a1ca25a-6eb4-4c2b-b3ea-0d1b74b0e15a" />
</p>
<br />

<p>
  Once you're back on the server desktop, look at the upper right-hand corner of the Server Manager again. Click on tools and then click Active Directory Users and Computers. 
</p>
<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/eab0597d-74bd-4586-8ae2-e73a906bee20" />
</p>
<p>
  This will bring up the Active Directory Users and Computer window. 
</p>
<p>
  <img src="https://github.com/timsherrell/configure-ad/assets/144177449/b1756175-8a89-47d7-b90d-d97d3d9db690" />
</p>
<br />
<p>
  Congratulations! You're now in the traditional Active Directory environment used by System Administrators in most IT departments. I would recommend doing this lab several times until it comes a bit more naturally and doesn't take you as long to get through. That way you'll have a good grasp on it.  
</p>
<p>
  In part 2 of this tutorial, we will join our Windows 10 Pro Azure virtual machine to the domain we just created. See you then!
</p>
