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

<a href="https://github.com/franciscovfonseca/Active-Directory-and-Azure-Setup/blob/main/README.md"> Preliminary Setup for Active Directory and Network Traffic Analysis between Azure VMs </a>

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

<img width="736" alt="AD-setup" src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/6b2d8467-b11b-4e6e-9041-80263bd1874b">

<br>
<br>
<br>


Click ***Next*** until reaching the ***Server Roles*** section.

<img width="736" alt="AD-setup" src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/3576aa91-f8ba-4f69-b6af-62605b2763af">

<br>
<br>
<br>



Check the box ⬜ next to ***Active Directory Domain Services*** then ***Add Features***.

<img width="736" alt="AD-setup" src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/7f80f91b-b01f-45fa-bd54-668c4e777847">

<br>
<br>
<br>


Click *Next* until reaching the ***Confirmation*** tab then click ***Install***.

<img width="736" alt="AD-setup" src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/8bf52f7a-944c-4a36-84c6-991f7fd7c6dc">

<br>
<br>


It may take a while to install.
<br>
<br>


Once it says "***Configuration required. Installation succeeded on DC.***" 🡪 Click ***Close***.

<img width="736" alt="AD-setup" src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/93374b1a-1dbc-4b86-bba6-37e7a9cdd693">

<br>
<br>
<br>


<h2></h2>


<h3>2️⃣ Promote DC-01 to Domain Controller </h3>

<br>


Towards the top-right corner of the *Server Manager* window, there will be a flag and a yellow triangle with a ⚠️ symbol 🡪 Click on that.

<img width="736" alt="AD-setup" src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/53424c41-3b9c-4817-ae15-895923b629fa">

<br>
<br>
<br>



Then click on "***Promote the server to a domain controller***".

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/d1e0b1af-0216-4184-9364-8152df7e5b1d" height="40%" width="40%" alt="9"/><br />

<br>
<br>
<br>

A window will pop up for a **Configuration Wizard**.

Check the bubble ◉ next to "*Add a new forest*"<br>
<br>
After that give it a domain name (example in the image below) and then click *Next*.

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/ce5d0f58-1030-44bb-9661-12044740ccf7" height="80%" width="80%" alt="9"/><br />

<br>
<br>
<br>


Give it a DSRM password (required but won't be used in this tutorial).

Click *Next*.

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/351b2112-e08b-4d91-b078-2793e7dfb5f5" height="80%" width="80%" alt="9"/><br />

<br>
<br>
<br>


Next, the **NetBIOS domain** will be made (this may take a while).<br>

Once it is made, click *Next* until reaching the **Prerequisites Check** tab, this process will take a moment.

Now click *Install*.

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/a07d4751-2dbc-41a1-bbbf-8522cf0353e9" height="80%" width="80%" alt="9"/><br />

<br>
<br>
<br>


After Installing, the VM will rebooted.

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/5215b104-2afa-487d-a720-bc9fee60e1eb" height="55%" width="55%" alt="9"/><br />

<br>
<br>
<br>

Once it is rebooted 🡪 Log back in to the **Domain Controller** with the ***Domain Name*** and the ***Username*** and ***Password*** that we had created for the DC in the previous turorial (in Azure).<br>


<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/1da11dd5-3fbb-45a0-a86a-f9763e0872f9" height="55%" width="55%" alt="9"/><br />



<br>
<br>
<br>

<h2></h2>


<h3>3️⃣ Creating an Admin in Active Directory </h3>
<br>

Once logged in: using Server Manager 🡪 click on **Tools** in the top-right corner.

Then click on ***Active Directory Users and Computers***.

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/06b9f07d-ead5-462f-8ffc-fde5075740dd" height="70%" width="70%" alt="9"/><br />
<br>

In the *Domain Container* 🡪 Create a new **Organizational Unit**

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/316049aa-5956-4b2c-84f5-e0e14248a729" height="80%" width="80%" alt="9"/><br />
<br>

Name the Organizational Unit "***_ADMINS***", uncheck the box ⬜ "*Protect container from accidental deletion*" then click ***OK***.

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/c89f59a5-ad03-4000-a0f7-d5b58008a22e" height="40%" width="40%" alt="9"/><br />
<br>

In the **_ADMINS** tab, create a *New* 🡪 *User*.

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/405988b7-1565-4060-ad2f-e784c5702956" height="80%" width="80%" alt="9"/><br />
<br>

Name this anything 🡪 Just remember the **User** and **Password**.

Uncheck the box ☐ that is next to "*User must change password at next logon*" 🡪 This won't be necessary.

Click ***Next*** then click ***Finish***.

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/016403b3-f372-4d6b-b753-48c30bddf2bb" height="50%" width="50%" alt="9"/><br />

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/11f58d5d-834b-4304-9039-4e1ed8815fa0" height="50%" width="50%" alt="9"/><br />
<br>

Now add this User to the ***Domain Admins** security group*.

Right-click on the User created, then click ***Properties***.

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/520c50e9-1012-42a4-8efa-569c4b3802d0" height="80%" width="80%" alt="9"/><br />
<br>


Click on the ***Members of*** tab, then click ***Add***. 

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/959c9d54-6f07-4f6a-aa4d-207f10c295df" height="50%" width="50%" alt="9"/><br />
<br>

Type ***domain*** in the box under "*Enter the object names to select*" 🡪 then click ***Check Names***. 

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/127acebe-b1dd-47ef-8028-2dec15ae8cd8" height="60%" width="60%" alt="9"/><br />
<br>

Choose the ***Domain Admins*** option then click ***OK***.

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/60675433-14d0-47f0-8b92-c380b109f2b4" height="80%" width="80%" alt="9"/><br />
<br>

Now, click ***Apply***.

✅ The User has successfully been added to the Domain Admins security group 🡪 click ***OK***.

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/b1818229-aa07-4a41-9d68-9ec441077b2b" height="50%" width="50%" alt="9"/><br />
<br>


Now logout of the **Domain Controller** and re-login as the **User** just created (***Tucker Smith***).

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/8410c255-bde4-4019-b2ef-6bd47f73dc75" height="50%" width="50%" alt="9"/><br />
<br>
<br>
<br>

<h2></h2>

<h3>4️⃣ Join Client-01 to Domain </h3>
<br>

For *Client-01* to join the *Domain Controller*, we first have to set its **DNS Server** as **DC-01’s Private IP Address**.

First, in the *Azure Portal*, go to the **Client VM**, then go to the ***Networking*** tab and click on the ***Network Interface***.

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/5a14a506-0344-4648-8895-d68ea33eea6e" height="60%" width="60%" alt="9"/><br />
<br>

Next, go to the **DNS Servers** tab and create a ***custom DNS Server***.

Add a custom server using the *Domain Controller's Private IP address*.

Example Below:

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/8f9b46a3-a80d-4f84-8f9f-c42cd108962c" height="60%" width="60%" alt="9"/><br />
<br>

Now click ***Save***.

Next go back to the **Client VM** and click ***Restart*** in the *Overview tab*. 

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/9d51c37d-195d-4161-a1f6-625fefa1d184" height="80%" width="80%" alt="9"/><br />
<br>

Once the Client is restarted:

🡪 Login to the Client with ***Remote Desktop*** as the **Admin Account** created (***Tucker Smith*** in this case).

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/3cd12607-36c3-4817-9de9-32c86bfe7ad6" height="50%" width="50%" alt="9"/><br />
<br>

After login in:

Go to **Settings 🡪 System 🡪 About** and click on ***Rename this PC (advanced)***.

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/f5ade15e-9e20-4376-9e73-24975e9dc514" height="80%" width="80%" alt="9"/><br />
<br>

Now Click on "***Change...***"

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/0b155ebb-4ddd-4c69-b53e-21db7fdfe283" height="50%" width="50%" alt="9"/><br />
<br>

Now check the bubble ⦿ next to ***Domain*** then type in the *Domain Name* (**Your own domain name**).

There should be a window that pops up for a login 🡪 Use the admin previously created to login.

Example below:

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/13b2eb4c-9274-481f-92b2-f9b1258136d4" height="80%" width="80%" alt="9"/><br 
                                                                                                                                                               
<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/9584e704-762c-4c98-9095-736d8daba619" height="40%" width="40%" alt="9"/><br />

✅ Success.

The VM will now restart after a short period.
<br>
<br>
<br>

<h2></h2>


<h3>5️⃣ Setup Remote Desktop for Non-Administrative Users </h3>
<br>

Now, log into the Domain Controller.

Go back to **Server Manager 🡪 Tools 🡪 Active Directory Users and Computers**.

Under the Domain container, go to the **Computers** tab ⟶ it should show that the **Client** has been added to the list.

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/2ddfd99c-5ca8-4d66-b6ad-96d7e3d9bfc1" height="80%" width="80%" alt="9"/><br />
<br>

Now, log into the **Client** as the *Admin User* created and go to **System Settings 🡪 Remote Desktop**.

Click on ***Select users that can remotely access this PC***.

Next click ***Add***.

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/e0c247c2-2469-4d15-afda-2e4118204e6c" height="80%" width="80%" alt="9"/><br />
<br>

In the box at the bottom: type in "***Domain Users***" and click on ***Check Names***.

Next click ***OK***.

<img src="https://github.com/franciscovfonseca/Active-Directory-Deployment-and-Configuration/assets/172988970/1d4d5e7d-14f0-4203-b819-46da88d3fc93" height="60%" width="60%" alt="9"/><br />
<br>


This will allow normal users to login to the **Client VM**.
<br>
<br>
<br>
<br>




<h2> Final Thoughts </h2>

We've successfully concluded the **Active Directory Deployment and Configuration** phase.
  
Through configuring **Active Directory** on the **Domain Controller**, we established our infrastructure by creating a **Forest**, an **Administrator Account**, and ultimately integrating **Client-01** into the Domain.

In the upcoming project, we'll be **Generating Users using Powershell** and simulating various Active Directory scenarios.

<br>
<br>
<br>









