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

> **Note:** Upload all your screenshots to the repository (recommend creating an `images` folder). Use clear, cropped screenshots. Replace the file names below with your actual uploaded file names/paths.

## Installation Steps

1. **Create a Windows 10 Virtual Machine in Azure**  
   Create a resource group, then create a Windows 10 Pro VM with at least 2 vCPUs and 8 GB RAM. Set an admin username and password. Enable RDP access (port 3389).

   ![Azure VM creation - Basics tab](images/azure-basics.png)  
   ![Azure VM creation - Disks tab](images/azure-disks.png)  
   ![Azure VM creation - Networking tab (RDP port open)](images/azure-networking.png)  
   ![Azure VM creation - Review + create](images/azure-review-create.png)  
   ![Deployment in progress](images/azure-deployment-progress.png)  
   ![VM overview (running)](images/azure-vm-overview.png)

2. **Connect to the VM using Remote Desktop**  
   Open Remote Desktop Connection on your local machine, enter the public/private IP (or use Azure Bastion if no public IP), and log in with the admin credentials.

   ![Remote Desktop Connection window](images/rdp-connection.png)

3. **Download and extract the osTicket installation files**  
   Download the required files (listed in Prerequisites) to the VM. Extract as needed.

   ![Google Drive download warning (example of downloading files)](images/google-drive-warning.png)  
   ![Installation files folder on VM](images/installation-files-folder.png)  
   ![List of downloaded installation files](images/downloaded-files-list.png)

4. **Enable Internet Information Services (IIS) with CGI**  
   Open Control Panel → Programs → Turn Windows features on or off.  
   Enable **Internet Information Services** → **World Wide Web Services** → **Application Development Features** → **CGI**.  
   Also enable **Common HTTP Features** (all sub-items) and **IIS Management Console**.

   *(Add your own screenshot of Windows Features with IIS/CGI enabled here)*

5. **Install PHP Manager for IIS**  
   Run the PHPManagerForIIS installer from your installation files.

   ![Installing PHP Manager for IIS](images/php-manager-install.png)

6. **Install the URL Rewrite Module**  
   Run the rewrite_amd64_en-US.msi installer.

   *(Screenshot shown in files list above)*

7. **Extract PHP to C:\PHP**  
   Create the folder C:\PHP and extract the PHP 7.3.8 contents into it.

   *(Add your own screenshot of C:\PHP folder here)*

8. **Install Visual C++ Redistributable**  
   Run VC_redist.x64.exe.

   *(Screenshot shown in files list above)*

9. **Install MySQL 5.5.62**  
   Run the MySQL installer. Choose **Typical** setup. Set the root password (e.g., "root").

   *(Screenshot shown in files list above)*

10. **Register PHP with IIS**  
    Open IIS Manager (run as Administrator).  
    Select the server name → double-click **PHP Manager** → **Register new PHP version** → browse to C:\PHP\php-cgi.exe.

    *(Add your own screenshot of PHP Manager registration here)*

11. **Copy osTicket files to the web root**  
    Extract the "upload" folder from the osTicket zip to C:\inetpub\wwwroot.  
    Rename the folder from "upload" to "osTicket".

    *(Add your own screenshot of wwwroot folder here)*

12. **Complete osTicket setup in the browser**  
    Open HeidiSQL. Create a new session (hostname 127.0.0.1, username "root", password "root").  
    Create a new database named "osticket".  

    ![HeidiSQL - creating osticket database](images/heidi-sql-create-db.png)

    Open a browser on the VM and navigate to http://localhost/osTicket/setup (installation wizard).  
    Fill in the required information (admin details, database name "osticket", user "root", password "root").  
    Complete the wizard. After installation, remove/secure the setup folder.

    ![osTicket installation wizard - Install Now button](images/osticket-install-now.png)  
    *(Add your own screenshots of the setup wizard and successful installation here)*

## Completion
The osTicket system is now installed and accessible at http://localhost/osTicket (client) or http://localhost/osTicket/scp (admin).  


