# osTicket: Prerequisites and Installation

## Project Overview
This repository documents the prerequisites and installation of the open-source help desk ticketing system **osTicket** on a Windows virtual machine in Microsoft Azure using Internet Information Services (IIS).

## Environments and Technologies Used
- Microsoft Azure (Virtual Machines, Compute, Resource Group)
- Remote Desktop
- Internet Information Services (IIS)

## Operating Systems Used
- Windows 10 Pro (21H2 or later)

## List of Prerequisites
- Azure subscription with the ability to create virtual machines
- Virtual Machine (Windows 10) with at least 2 vCPUs and 8 GB RAM
- Remote Desktop Connection enabled on the VM
- Installation files downloaded and placed on the VM desktop:
  - osTicket installation zip (containing the "upload" folder and supporting files)
  - PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x64.zip)
  - Microsoft Visual C++ Redistributable (VC_redist.x64.exe)
  - IIS URL Rewrite Module (rewrite_amd64_en-US.msi)
  - MySQL 5.5.62 (mysql-5.5.62-win32.msi)
  - HeidiSQL (portable or installer)

> **Note:** Replace the image placeholders below (e.g., `screenshot-1.png`) with your actual screenshot file names after uploading them to the repository. Use clear, cropped screenshots that exactly match each step.

## Installation Steps

1. **Create a Windows 10 Virtual Machine in Azure**  
   Create a resource group, then create a Windows 10 Pro VM with at least 2 vCPUs and 8 GB RAM. Set an admin username and password you will remember. Note the public IP address.  

   ![Create Azure VM and note settings](screenshot-1.png)

2. **Connect to the VM using Remote Desktop**  
   Open Remote Desktop Connection on your local machine, enter the public IP address of the VM, and log in with the admin credentials you created.  

   ![Remote Desktop connection to VM](screenshot-2.png)

3. **Download and extract the osTicket installation files**  
   Download the required files (listed in Prerequisites) to the VM desktop and extract them as needed.  

   ![Installation files on desktop](screenshot-3.png)

4. **Enable Internet Information Services (IIS) with CGI**  
   Open Control Panel → Programs → Turn Windows features on or off.  
   Enable **Internet Information Services** → **World Wide Web Services** → **Application Development Features** → **CGI**.  
   Also enable **Common HTTP Features** (all sub-items) and **IIS Management Console**.  

   ![Enabling IIS and CGI](screenshot-4.png)

5. **Install PHP Manager for IIS**  
   From the installation files folder, run the PHPManagerForIIS installer.  

   ![PHP Manager installation](screenshot-5.png)

6. **Install the URL Rewrite Module**  
   Run the rewrite_amd64_en-US.msi installer.  

   ![URL Rewrite Module installation](screenshot-6.png)

7. **Extract PHP to C:\PHP**  
   Create the folder C:\PHP and extract the PHP 7.3.8 contents into it.  

   ![PHP extracted to C:\PHP](screenshot-7.png)

8. **Install Visual C++ Redistributable**  
   Run VC_redist.x64.exe.  

   ![VC Redistributable installation](screenshot-8.png)

9. **Install MySQL 5.5.62**  
   Run the MySQL installer. Choose **Typical** setup. Set the root password to "root" (or your preferred password).  

   ![MySQL installation and password setup](screenshot-9.png)

10. **Register PHP with IIS**  
    Open IIS Manager (run as Administrator).  
    Select the server name → double-click **PHP Manager** → **Register new PHP version** → browse to C:\PHP\php-cgi.exe.  

    ![Registering PHP in IIS](screenshot-10.png)

11. **Copy osTicket files to the web root**  
    Extract the "upload" folder from the osTicket zip to C:\inetpub\wwwroot.  
    Rename the folder from "upload" to "osTicket".  

    ![osTicket files in wwwroot](screenshot-11.png)

12. **Complete osTicket setup in the browser**  
    Install and open HeidiSQL. Create a new session with hostname 127.0.0.1, username "root", password "root".  
    Create a new database named "osticket".  

    ![Creating database in HeidiSQL](screenshot-12a.png)

    Open a browser on the VM and navigate to http://localhost/osTicket/scp (or the setup wizard URL).  
    Fill in the required information: admin email, name, database name "osticket", database user "root", database password "root".  
    Complete the installation wizard.  

    ![osTicket setup wizard](screenshot-12b.png)

    ![Successful installation and admin login](screenshot-12c.png)

## Completion
The osTicket system is now installed and accessible at http://localhost/osTicket (staff) or http://localhost/osTicket/scp (admin).  
This concludes the prerequisites and installation phase.

**Important:** This project focuses only on installation. Post-installation configuration and ticket lifecycle are not included.




Mark the ticket as resolved/closed once the issue is fixed and document the outcome.

