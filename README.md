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

> **Note:** Create an `images` folder in your repository. Upload and rename the screenshots you provided exactly as listed below (01-, 02-, etc.) so the links work. Only the installation-related screenshots are used — all ticket screenshots, support center, staff panel, and old README screenshots are excluded.

## Installation Steps

1. **Create a Windows 10 Virtual Machine in Azure**  
   Create a resource group, then create a Windows 10 Pro VM with at least 2 vCPUs and 8 GB RAM. Set an admin username and password. Enable RDP access (port 3389).

   ![Azure VM creation - Basics tab](images/01-azure-create-basics.png)  
   ![Azure VM creation - Disks tab](images/02-azure-create-disks.png)  
   ![Azure VM creation - Networking tab (RDP port open)](images/03-azure-create-networking.png)  
   ![Azure VM creation - Review + create](images/04-azure-create-review.png)  
   ![Deployment in progress](images/05-azure-deployment-progress.png)  
   ![VM overview (running)](images/06-azure-vm-overview.png)

2. **Connect to the VM using Remote Desktop**  
   Open Remote Desktop Connection on your local machine and connect using the VM's IP.

   ![Remote Desktop Connection window](images/07-rdp-connection.png)

3. **Download and extract the osTicket installation files**  
   Download the required files (listed in Prerequisites) to the VM.

   ![Google Drive download warning (downloading the files zip)](images/08-google-drive-warning.png)  
   ![List of downloaded installation files](images/09-downloaded-files-list.png)  
   ![Installation files folder (showing PHP Manager installing)](images/10-installation-files-php-manager.png)

4. **Enable Internet Information Services (IIS) with CGI**  
   Open Control Panel → Programs → Turn Windows features on or off.  
   Enable **Internet Information Services** → **World Wide Web Services** → **Application Development Features** → **CGI**.  
   Also enable **Common HTTP Features** (all sub-items) and **IIS Management Console**.

   *(Take and add your own screenshot here – name it `11-iis-enable-cgi.png`)*

5. **Install PHP Manager for IIS**  
   Run the PHPManagerForIIS installer.

   *(Already shown in step 3 above)*

6. **Install the URL Rewrite Module**  
   Run the rewrite_amd64_en-US.msi installer.

   *(Take and add your own screenshot here – name it `12-url-rewrite-install.png`)*

7. **Extract PHP to C:\PHP**  
   Create the folder C:\PHP and extract the PHP 7.3.8 contents into it.

   *(Take and add your own screenshot here – name it `13-php-extract.png`)*

8. **Install Visual C++ Redistributable**  
   Run VC_redist.x64.exe.

   *(Take and add your own screenshot here – name it `14-vc-redist-install.png`)*

9. **Install MySQL 5.5.62**  
   Run the MySQL installer. Choose **Typical** setup. Set root password (e.g., "root").

   *(Take and add your own screenshot here – name it `15-mysql-install.png`)*

10. **Register PHP with IIS**  
    Open IIS Manager (run as Administrator).  
    Select the server name → double-click **PHP Manager** → **Register new PHP version** → browse to C:\PHP\php-cgi.exe.

    *(Take and add your own screenshot here – name it `16-php-register-iis.png`)*

11. **Copy osTicket files to the web root**  
    Extract the "upload" folder from the osTicket zip to C:\inetpub\wwwroot.  
    Rename the folder from "upload" to "osTicket".

    *(Take and add your own screenshot here – name it `17-osticket-wwwroot.png`)*

12. **Complete osTicket setup in the browser**  
    Open HeidiSQL. Create a new session (hostname 127.0.0.1, username "root", password "root").  
    Create a new database named "osticket".  

    ![HeidiSQL - creating database and final installation checklist](images/18-heidi-sql-checklist.png)

    Open a browser on the VM and navigate to http://localhost/osTicket/setup.  
    Complete the installation wizard. After success, secure/remove the setup folder.

    *(Take and add 2–3 screenshots of the browser wizard and final success screen – name them `19-osticket-wizard-1.png`, `20-osticket-wizard-2.png`, `21-osticket-success.png`)*

## Completion
The osTicket system is now installed and accessible at http://localhost/osTicket (client) o


