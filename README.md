<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

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
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
