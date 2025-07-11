<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Installation files for osTicket
- Azure virtual machine
- Heidi SQL

<h2>Installation Steps</h2>
<p>
Welcome to my first hands-on tutorial! In this lab, we’ll begin by provisioning a virtual machine (VM) using the Microsoft Azure portal. A virtual machine acts as a remote computer that allows us to safely install and configure applications—without impacting our physical system.

To get started:

Create a new Resource Group in Azure and name it osTicket to organize all related resources.

Deploy a virtual machine using either 2 or 4 vCPUs depending on your available resources.

For this demonstration, I’ll be using a VM with 4 vCPUs to ensure smooth performance.
<p>
<img src="https://i.imgur.com/9y8HV1c.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />


<p>
Once your virtual machine has been successfully deployed, the next step is to connect to it via Remote Desktop Protocol (RDP).

In the Azure portal, go to your VM's overview page.

Locate and copy the Public IPv4 address of the VM.

Open your RDP client and connect using the IP address.

Mac Users:

You’ll need to download the Microsoft Remote Desktop app from the Mac App Store if you haven’t already.

Once connected, log in using the username and password you set during the VM creation process.
</p>
<p>
<img src="https://i.imgur.com/x93jbDZ.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Now that you're connected to your virtual machine, the next step is to enable IIS (Internet Information Services) — the web server that will host the osTicket application.

Follow these steps:

Open the Control Panel

Click on “Uninstall a Program”

In the left sidebar, select “Turn Windows features on or off”

In the list that appears, scroll down and check the box for "Internet Information Services"

Click OK to install IIS.

This process may take a few minutes to complete.

Once installed, IIS will be ready to serve your PHP-based web application. You can test that it's working by opening a browser on the VM and navigating to http://localhost — you should see the default IIS welcome page.
</p>
<p>
<img src="https://i.imgur.com/OF6ho1G.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
With IIS now enabled, the next step is to install the Web Platform Installer (Web PI). This tool simplifies the process of downloading and installing the components required for osTicket, such as PHP, MySQL, and other necessary extensions.

Use the following link to access all the files you'll need for this setup:
- [Download osTicket Lab Files & Web Platform Installer](https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)

Open the link above

Download and run the Web Platform Installer from the provided files

Follow the prompts to complete the installation
</p>
<p>
<img src="https://i.imgur.com/BbmzmYb.png" height="400%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Once the Web Platform Installer (Web PI) is installed, we’ll use it to install the necessary backend components for osTicket.

Inside Web Platform Installer:
Launch Web Platform Installer

Use the search bar to find and install:
- MySQL 5.5
- PHP (select the x86 versions, up to version 7.3)

Next download osTicket. Then extract and copy the "upload" folder into c:\inetpub\wwwroot. Afterwards rename the folder to osTicket
</p>
<p>
<img src="https://i.imgur.com/3bL41Ax.png" height="400%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
With all dependencies installed, it’s time to access the osTicket setup through your browser.

Open IIS Manager on your virtual machine

In the left-hand sidebar, expand:
- Sites → Default Web Site → osTicket (or the folder where you placed the osTicket files)

With the osTicket site selected, look to the right-hand "Actions" pane and click:
- “Browse *.80”

This will launch your default web browser and open the osTicket web installer using the local server URL (typically http://localhost/osTicket).
</p>
<p>
<img src="https://i.imgur.com/DFrkgwD.png" height="400%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Before completing the osTicket installation, we need to ensure that essential PHP extensions are enabled through PHP Manager in IIS.

Steps to Enable Extensions:

Open IIS Manager

Navigate to:
- Sites → Default Web Site → osTicket

In the Features View, double-click on PHP Manager

Click on “Disable or enable an extension”

From the list of available extensions, enable the following:
- php_intl.dll
- php_opcache.dll
</p>
<p>
<img src="https://i.imgur.com/gqy1cHT.png" height="400%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
To complete the installation, you’ll need to rename and secure the osTicket configuration file.

Step-by-Step Instructions:

Navigate to the following folder on your VM:
- C:\inetpub\wwwroot\osTicket\include\

Locate the file named:
- ost-sampleconfig.php

Rename this file to:
- ost-config.php

After renaming the file, you need to restrict its permissions to protect sensitive configuration data.

Steps to Secure ost-config.php:
- Right-click on the file → Properties
- Go to the Security tab → click Advanced
- Click “Disable inheritance”
- When prompted, choose “Remove all inherited permissions from this object”
- Click “Add” → Select a principal → Type in Everyone → click OK
- Under Permissions, check Full Control and click OK
- Apply the changes and close all dialog boxes
</p>
<p>
<img src="https://i.imgur.com/6CA6htT.png" height="400%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/k75bCyb.png" height="400%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
With all configurations and permissions set, return to your browser to complete the web-based osTicket installation.

Steps:
- In your browser (e.g., http://localhost/osTicket), click the “Continue” button to proceed with the installer.

You’ll be prompted to configure basic help desk settings:
- Help Desk Name – Choose a name that represents your support environment (e.g., Acme Support Portal)
- Default System Email – Select or enter an email address that will receive all incoming support tickets from users
<p>
<img src="https://i.imgur.com/vd3Ex6A.png" height="4000%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Final Configuration in the Browser
  
In the osTicket web installer, fill in your MySQL database details:
- MySQL Database: 
- MySQL Username:
- MySQL Password: 

Click “Install Now!” to complete the installation.

If everything was configured correctly, you should see a confirmation message: osTicket has been successfully installed!

Post-Installation Cleanup (Very Important)
To secure your environment, complete the following cleanup tasks:

Delete the Setup Directory:
- Navigate to: C:\inetpub\wwwroot\osTicket\setup
- Delete the entire setup folder

This prevents reinstallation and blocks potential attackers from accessing the installer.

Secure the Configuration File:
- Go to: C:\inetpub\wwwroot\osTicket\include\ost-config.php
- Right-click the file → Properties → Security
- Set Permissions to Read-only for all users

Logging into the Admin Panel
You can now access the osTicket admin dashboard:
- Log in with the admin credentials you created during the initial setup.
</p>



