<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployment and Configuration </h1>

<br>


Building on the first project that set up our simulated Active Directory environment, we now move to the next step in our tutorial series.
  
Welcome to the "Active Directory Deployment and Configuration" project, where we explore the details of deploying and refining an Active Directory system.

This project is designed to impart a fundamental understanding of Active Directory services, emphasizing key aspects such as installation, forest creation, user account administration, domain integration, and customized Remote Desktop access.

<br>


<h2>Prerequisites</h2>

- <a href="https://github.com/franciscovfonseca/Active-Directory-and-Azure-Setup/blob/main/README.md"> Preliminary Setup for Active Directory and Network Traffic Analysis between Azure VMs </a>

<br>


<h2>Key Objectives</h2>

<h3>🟢 Active Directory Installation</h3>

-  Configure and install Active Directory services on the designated Domain Controller virtual machine.

<h3>🟢 Forest Creation</h3>

- Establish a new Active Directory forest.

<h3>🟢 Administrator Account Creation</h3>

- Create and administer user accounts with administrative privileges for effective management of the Active Directory environment.

<h3>🟢 Domain Joining</h3>

- Integrate the Client-01 virtual machine into the established domain, ensuring seamless communication with the Active Directory infrastructure.

<h3>🟢 Remote Desktop Setup</h3>

- Configure Remote Desktop access specifically tailored for non-administrative users, enhancing user accessibility while maintaining security protocols.

<br>




<h2>Environments and Technologies Used</h2>

🔹 Microsoft Azure (Virtual Machines/Compute)

🔹 Remote Desktop

🔹 Active Directory Domain Services

<br>



<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<br>
<br>



<h2>Configuration Steps</h2>

<h3>1️⃣ Install Active Directory in DC-01</h3>

<br>


Go to the **Domain Controller DC-01** and in ***Server Manager*** dashboard click on ***Add roles and features***.

<img width="736" alt="AD-setup" src="https://github.com/kirkgacias/ad-deployment-configuration/assets/158519921/bb534e6b-0072-420a-9f74-c03bbcc77016">

<br>
<br>
<br>


Click ***Next*** until reaching the ***Server Roles*** section.

<img width="736" alt="AD-setup" src="https://github.com/kirkgacias/ad-deployment-configuration/assets/158519921/bb534e6b-0072-420a-9f74-c03bbcc77016">

<br>
<br>
<br>



Check the box ⬜ next to ***Active Directory Domain Services*** then ***Add Features***.

<img width="736" alt="AD-setup" src="https://github.com/kirkgacias/ad-deployment-configuration/assets/158519921/bb534e6b-0072-420a-9f74-c03bbcc77016">

<br>
<br>
<br>


Click Next until reaching the ***Confirmation*** tab then click ***Install***.

<img width="736" alt="AD-setup" src="https://github.com/kirkgacias/ad-deployment-configuration/assets/158519921/bb534e6b-0072-420a-9f74-c03bbcc77016">

<br>
<br>
<br>


It may take a while to install.

Once it says "*Configuration required. Installation succeeded on (**Your DC name here**)*" 🡪 Click ***Close***.

<img width="736" alt="AD-setup" src="https://github.com/kirkgacias/ad-deployment-configuration/assets/158519921/bb534e6b-0072-420a-9f74-c03bbcc77016">

<br>
<br>
<br>


Towards the top-right corner of the *Server Manager* window, there will be a flag and a yellow triangle with a ⚠️ symbol 🡪 Click on that.

<img width="736" alt="AD-setup" src="https://github.com/kirkgacias/ad-deployment-configuration/assets/158519921/bb534e6b-0072-420a-9f74-c03bbcc77016">

<br>
<br>
<br>



Then click on "***Promote the server to a domain controller***".

<img src="https://github.com/franciscovfonseca/Active-Directory-Lab/assets/172988970/a067d615-f065-479a-97ef-65a23609406d" height="40%" width="40%" alt="9"/><br />

<br>
<br>
<br>

A window will pop up for a **Configuration Wizard**.

Check the bubble ◉ next to "*Add a new forest*"<br>
<br>
After that give it a domain name (example in the image below) and then click *Next*.

<img src="https://github.com/franciscovfonseca/Active-Directory-Lab/assets/172988970/e1bfed73-b689-4cbf-a950-56f6ee5341e9" height="80%" width="80%" alt="9"/><br />

<br>
<br>
<br>


Give it a DSRM password (required but won't be used in this tutorial).

Click *Next*.

<img src="https://github.com/franciscovfonseca/Active-Directory-Lab/assets/172988970/04a4531f-502e-493e-a7cd-2264ccad85d8" height="80%" width="80%" alt="9"/><br />

<br>
<br>
<br>


Next, the **NetBIOS domain** will be made (this may take a while).<br>

Once it is made, click *Next* until reaching the **Prerequisites Check** tab, this process will take a moment.

Now click *Install*.

<img src="https://github.com/franciscovfonseca/Active-Directory-Lab/assets/172988970/04a4531f-502e-493e-a7cd-2264ccad85d8" height="80%" width="80%" alt="9"/><br />

<br>
<br>
<br>


After Installing, the VM will rebooted.

Once it is rebooted 🡪 Log back into the Domain Controller with the *Domain Name* and the *Username*.<br>
<br>
Example below:

<img src="https://github.com/franciscovfonseca/Active-Directory-Lab/assets/172988970/e597573e-b3fc-4d4e-b15a-5b7bd4a29f25" height="55%" width="55%" alt="9"/><br />



<br>
<br>
<br>

<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<h3>&#9313; Promote DC-01 to Domain Controller </h3>

- Once the installation is done, notice the flag on the top left of the Server Manager
- Click on the flag and promote DC-01 to Domain Controller.

<img width="242" alt="notif" src="https://github.com/kirkgacias/ad-deployment-configuration/assets/158519921/3cb91456-cc00-4e70-8ea2-2b54a5dc8137">



<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

-  We will now add a new Forest and set the Root domain name to “mydomain.com”
<p>
<img width="565" alt="my domain" src="https://github.com/kirkgacias/ad-deployment-configuration/assets/158519921/e4d06e9a-a5a4-4e8b-b464-b90ac041cbc8"> </p>
  
- Finish setup and restart DC-01
- Log back in with “your username"@mydomain.com



<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<h3>&#9314; Creating an Admin in Active Directory </h3>

- Once DC-01 has rebooted, click on tools and select Active Directory Users and Computers
- Right click on mydomain.com and select new and click on Organizational Unit
<img width="438" alt="Users" src="https://github.com/kirkgacias/ad-deployment-configuration/assets/158519921/23db8c79-84f4-4e6d-befe-77505518cb05">


<br>
<br>
<br>
<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<p><strong> We will be creating an OU named _EMPLOYEES and _ADMINS </strong></p>

<img width="450" alt="admins" src="https://github.com/kirkgacias/ad-deployment-configuration/assets/158519921/d64f8f3b-130b-4156-bc08-b16f7b21fc89">


<p><strong>.</strong></p>
<p><strong>.</strong></p>

<p><strong>Right click on Users and create a new user named Jane Doe with the username jane_admin</strong></p>

<img width="323" alt="jane doe" src="https://github.com/kirkgacias/ad-deployment-configuration/assets/158519921/5d8f782a-145a-404b-bc83-7a6721b3728d">


<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<p><strong>Now we will turn Jane Doe into an admin by right clicking her name and adding her to the “Domain Admins” Security Group</strong></p>

<img width="412" alt="add to group" src="https://github.com/kirkgacias/ad-deployment-configuration/assets/158519921/08175b12-7a59-4030-b5ef-6ef1983ac6e7">



<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<p><strong>Logout of DC-01 and log back in with Jane Doe’s credentials</strong></p>

<img width="337" alt="jane login" src="https://github.com/kirkgacias/ad-deployment-configuration/assets/158519921/751f9854-2aa5-4f94-b641-b355e77a2a32">

<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>


<h3>&#9315; Join Client-01 to domain </h3>

<p><strong> For Client-01 to join the domain, we first have to set it’s DNS server as DC-01’s private address.</strong></p>

- In the Azure Portal, select Client-01 -> Networking -> Network interface and click on DNS servers

<img width="735" alt="dns servers" src="https://github.com/kirkgacias/ad-deployment-configuration/assets/158519921/13292c41-67f1-4212-95c4-084ac2ec0751">



<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<p><strong>Select a custom DNS server and type in the private ip address of DC-01 and restart Client-01</strong></p>

<img width="356" alt="dns servers2" src="https://github.com/kirkgacias/ad-deployment-configuration/assets/158519921/d7ec7764-9fcd-4d46-8962-f536bcb1007d">

<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<p><strong> Now log back in to Client-01 using your original admin credentials. Click start and go to Settings > Rename this PC (advanced) > Change and add “mydomain.com” and login with the admin credentials previously created (jane_admin) </strong></p>

<img width="297" alt="remote desktop first login" src="https://github.com/kirkgacias/ad-deployment-configuration/assets/158519921/97df566d-84c9-40d2-88b1-769f79af10a6">

<br>

<p> <strong>Once Client-01 has been added, the VM will restart.</strong></p>


<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<h3>&#9316; Setup Remote Desktop for non-administrative users </h3>

- Log back into Client-01 using jane_admin and open Settings > Remote Desktop> User Accounts and click “Select users that can remotely access this PC”
- Add Domain Users

<br>

<img width="343" alt="domain users" src="https://github.com/kirkgacias/ad-deployment-configuration/assets/158519921/04eaffe2-1fa3-4c4c-a327-8ea5b63e2c24">

<p><strong>This will allow normal users to login to Client-01</strong></p>

<br>

<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>



<h2> Final Thoughts </h2>

<p>
We've successfully concluded the Active Directory Deployment and Configuration phase. Through configuring Active Directory on the Domain Controller, we established our infrastructure by creating a forest, administrator account, and ultimately integrating Client-01 into the domain. In the upcoming project, we'll be generating users and simulating various Active Directory scenarios. </p>








