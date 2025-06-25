<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
<b>osTicket</b> is a free and open-source support ticket system that helps you manage customer or user requests in one place. Instead of handling support emails manually, osTicket lets people submit tickets online, through email, or an API—and routes them to the right person or team. It makes staying organized, responding faster, and keeping track of everything easier. Who doesn't love easier? &#128512 <br />
<br />
This guide shows you how to get osTicket up and running on an Azure virtual machine. It walks you through everything you need to do before <i>actually</i> installing osTicket—like setting up the server and installing the required software.<br />
<br />
<b>Let's Gooo</b> &#128640 <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Prerequisites</h2>

- Create an Azure Account (Tenant (Organization) and Subscription)
- Sign into Azure Account

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1 - Create a Virtual Machine (VM) in Azure
- Step 2 - Connect to Virtual Machine using Remote Desktop
- Step 3 - Within VM, download the installation file from <a href="https://www.osticket.com">osTicket</a> and unzip it onto your desktop
- Step 4 - Install the Required Software (for this guide, software includes: Install IIS, PHP, and MySQL) 
- Step 5 - Move Files to the Web Directory
- Step 6 - Set Up the Database (MySQL)
- Step 7 - Start the Web Installer
- Step 8 - Final Touches- Congrats! osTicket should be installed correctly!

<h2>Installation Steps</h2>

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/TaeIVwZ.png" height="80%" width="80%" alt="Azure Virtual Machine Steps"/>


<b> **PRE-STEP** -- After signing in to Azure, click on "Resource Groups" in the dashboard. You will be redirected to the "Create Resource Group" page.</b>
</p>
<br />
<br />
<br />



<p>
<img src= "https://i.imgur.com/qB68NYR.png" height="80%" width="80%" alt="Azure Virtual Machine Steps"/>
</p>

<h3><b> Step 1 - Create Virtual Machine </b></h3>
  
<p>Make sure that the resource group is created under the correct <b>Subscription.</b>

Next, enter a <b>Resource Group Name</b> that is easy to recognize and will be used to contain your Virtual Machine.

Next, select a <b>Region</b> that is geographically close to your location for optimal performance.

Finally, click <b>Review + Create</b> to create the Resource Group
</p>
<br />
<br />
<br />
<br />

<p>
<img src="https://i.imgur.com/DVnMCCU.png" height="80%" width="80%" alt="Azure Virtual Machine Steps"/>
</p>
<p>
<h3><b> Step 2 - Create a Virtual Machine</b></h3>
  <br />

After creating your resource group, return to the Azure Dashboard.

Next, click on <b>"Virtual Machines" </b>— you can find this either on the dashboard or in the left-hand navigation menu.

Then, click the <b>"+ Create"</b> button and select <b>"Azure virtual machine"</b> from the dropdown.
** For complete tutorial on Azure virtual machine set-up , click here a ref<"https://github.com/micaelahwalkerit/azure_virtualmachine">
</p>
<br />
<br />
<br />
<br />

<p>
<img src="https://i.imgur.com/aST7Tc3.png" height="80%" width="80%" alt="Azure Virtual Machine Steps"/>
</p>
<p>
<h3><b>Step 3 - Fill in Basic Tab for your Virtual Machine </b></h3>
<br />
  
After clicking <b>"Azure virtual machine"</b> from the dropdown menu, you'll be taken to the <b>Basics</b> tab. This is where you'll enter the essential information needed to set up your virtual machine.

<b>Fill in the following fields:</b>

<b>Subscription:</b> Select the appropriate subscription from the list.

<b>Resource Group:</b> Choose the resource group you created earlier.

<b>Virtual Machine Name:</b> Enter a name for your VM (e.g., MyFirstVM).

<b>Region:</b> Select the same region you used for your resource group.

<b>Image:</b> Choose the operating system you'd like to install (e.g., Windows 11, Ubuntu).

<b>Size:</b> Click "See all sizes" and select a VM size that fits your performance needs and budget. (However, it's best to choose at least 2 vcpus for speed)

<b>Administrator Account Setup:</b>

<b>Username:</b> Create a secure username for logging into your VM.

<b>Authentication Type:</b>

<ul>For <i>Windows</i>, set a strong password.

For <i>Linux</i>, upload an SSH public key or choose password authentication if preferred. ( Azure now automatically generates an SSH key pair for you but you can also just use a Username & Password like you would for Windows).</ul>

<b>Licensing:</b> (Usually for a Windows VM) If you see a Licensing checkbox, check it or else your VM will fail to deploy.

Click <b>"Next: Disk"</b>
</p>
<br />
<br />
<br />
<br />

<p>
<img src="https://i.imgur.com/c9ucNHD.png" height="80%" width="80%" alt="Azure Virtual Machine Steps"/>
</p>
<p>
<h3><b>Step 4 - Disks Tab </b></h3>
<br />

Leave defaults (or choose SSD for better performance).

Click <b>"Next: Networking"</b>.
</p>
<br />
<br />
<br />
<br />

<p>
<img src="https://i.imgur.com/IWOHYJU.png" height="80%" width="80%" alt="Azure Virtual Machine Steps"/>
</p>
<p>
<h3><b>Step 5 - Networking Tab</b></h3> 
  <br />

Azure will automatically create a <b>Virtual Network (VNet) and Subnet</b>. However, you can change the VNet name.
<br />
<ul><i>This is one of Azure's helpful features for a virtual machine. These are essential because they allow your VM to communicate with other resources, just like a physical computer on a network</i></ul>

Ensure <b>"Public IP"</b> is set to create a new one (if you want internet access).

<b>Leave defaults unless you have specific networking needs.</b>
</p>
<br />
<br />
<br />
<br />

<p>
<img src="https://i.imgur.com/s6te31Q.png" height="80%" width="80%" alt="Azure Virtual Machine Steps"/>
</p>
<p>
<h3><b> Step 6 - Management, Montoring, Advanced,Tag Tabs </b></h3>
  <br />
This step is pretty easy! You can leave the options as they are! Wahoo, this is last aspect of "set-up" &#129395;
<br />
Click <b>Review + Create<b/>
</p>
<br />
<br />
<br />
<br />

<p>
<img src="https://i.imgur.com/YBEt0H5.png" height="80%" width="80%" alt="Azure Virtual Machine Steps"/>
</p>
<p>
<h3><b>Step 7 - Review + Create</b></h3>
<br />


Wait for validation to pass.

Click <b>"Create."</b>
</p>
<br />
<br />
<br />
<br />

<p>
<img src="https://i.imgur.com/DTPz4WR.png" height="80%" width="80%" alt="Azure Virtual Machine Steps"/>
</p>
<p>
<h3><b>Step 8 - Wait for Deployment to Take Place</b></h3>
<br />
  
Azure will take a few minutes to create your Virtual Machine based on all of the configurations from the previous steps.

Once done, click "Go to resource" to view your new virtual machine and observe VNet and Subnet to make sure it matches what was configured in previous steps.
</p>
<br />
<br />
<br />
<br />

<p>
<img src="https://i.imgur.com/NdZHP4m.png" height="80%" width="80%" alt="Azure Virtual Machine Steps"/>
</p>

<p>
<h3><b>Step 9 - Check to see if Virtual Machine is Successfully Running</b></h3>
<br />
</p>

 <p>
Click <b> "Home".</b>

Click <b>"Virtual Machines".</b>

See if the Virtual Machine you created is running
</p>
<br />

<p>Now you can connect to your Virtual Machine via Remote Desktop (RDP) for Windows VMs or Secured Shell (SSH) for Linux VMs
</p>

<br />
<br />
<br />

<h2>In Conclusion</h2>
<p>
Creating a virtual machine in Azure lets you run a computer in the cloud for tasks like running apps, storing data, or testing software. It’s a fast and flexible way for businesses to build secure infrastructure, protect their data, and manage systems without needing physical equipment. Learning how to set up a virtual machine helps both individuals and organizations work more efficiently and safely in the cloud.
