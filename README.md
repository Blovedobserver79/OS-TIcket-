# OS-TIcket-
OS TIcket 
<img width="700" height="200" alt="image" src="https://github.com/user-attachments/assets/2f8ffe9e-7547-4ebd-a35a-966849d77c11" />

osTicket - Prerequisites and Installation

This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.

Video Demonstration



YouTube: osTicket Configuration and Administration: Your Guide to Free Helpdesk & Ticketing Software



https://youtu.be/IHcMBVq40iE?si=eR9_Zz_itH0Lfy00





Environments and Technologies Used

Microsoft Azure (Virtual Machines/Compute)
Remote Desktop
Internet Information Services (IIS)
OSTicket Platform





Operating Systems Used

Windows 11 (21H2)

List of Prerequisites

Item 1

Item 2

Item 3

Item 4

Item 5

Installation Steps

<img width="1707" height="905" alt="Azure 1" src="https://github.com/user-attachments/assets/b1c11e60-4e90-46c4-b483-09530964bf9e" />

Create a Windows 10 VM in Azure.
At least 2 vCPUs, 8GB RAM. Name as you like.
Assign a username and password.


<img width="1568" height="918" alt="Azure 2" src="https://github.com/user-attachments/assets/2c6b731a-7eb0-4cc6-a0d8-679061cc0e32" />

Connect to the VM using Remote Desktop.
Use the public IP, username, and password.


<img width="1697" height="876" alt="azure 3" src="https://github.com/user-attachments/assets/0de86ac4-c5a5-4f55-b5aa-63e830177ec6" />

Download and extract the OS ticket installation files onto the VM desktop.


<img width="1547" height="930" alt="Azure 4" src="https://github.com/user-attachments/assets/713f2f25-b713-46d9-99fd-e533a4d719eb" />

Enable IIS (Internet Information Services) and CGI:
Go to Control Panel → Programs → Turn Windows features on or off.
Enable “Internet Information Services” and under it, “CGI.”


<img width="1882" height="912" alt="azure 5" src="https://github.com/user-attachments/assets/cf63a7a2-81b6-4101-bf15-448967410e36" />

Install PHP Manager for IIS from the osTicket installation files folder.




<img width="1916" height="1016" alt="azure 6" src="https://github.com/user-attachments/assets/fcfd55ff-5b6b-46d6-8b3c-8b28f5865ea3" />

Install the IIS Rewrite Module from the same folder.



<img width="547" height="592" alt="azure 7 " src="https://github.com/user-attachments/assets/81c094c1-bb0d-40b5-913a-9ce9e7279532" />

Create a folder C:\PHP and extract PHP binaries (php-7.3.8) into it.




<img width="1852" height="532" alt="azure 8" src="https://github.com/user-attachments/assets/3503e570-452c-4268-ba46-23981ecf9037" />

Install the “vcredist” (C++ Redistributable) from the installation files folder.




<img width="1215" height="547" alt="azure 9" src="https://github.com/user-attachments/assets/dbf3c169-db73-460e-8d06-365ef346a39c" />

Install MySQL (version 5.5.62):
Choose typical setup.
For “root” user, set password to “root”.
egister PHP with IIS:
Open IIS Manager as Administrator.
Double-click PHP Manager, “Register new PHP version,” and select C:\PHP\php-cgi.exe.
Copy and configure osTicket web files:
Extract the osTicket “upload” folder into C:\inetpub\wwwroot.
Rename “upload” to “osTicket.”
Final database and osTicket setup:
Install HeidiSQL.
Connect using root/root.
Create a new database called “osticket”.
In browser, go to osTicket setup page, enter admin info, and database settings (database: osticket, user: root, password: root).
Complete installation and log in with your admin credentials.


<img width="1412" height="763" alt="azure 10" src="https://github.com/user-attachments/assets/0b7918b2-82e8-4282-821c-e940e8eb5978" />

Rename “upload” to “osTicket.” Final database and osTicket setup: Install HeidiSQL. Connect using root/root. Create a new database called “osticket”. In browser, go to osTicket setup page, enter admin info, and database settings (database: osticket, user: root, password: root). Complete installation and log in with your admin credentials.



<img width="1012" height="577" alt="azure 11" src="https://github.com/user-attachments/assets/730c99d0-e9d8-4fa2-83dd-eb1379d2f2b9" />

Start and Connect to VM:
Turn on the osTicket virtual machine and use Remote Desktop to access it.

<img width="497" height="375" alt="OS TICKET 1 " src="https://github.com/user-attachments/assets/17bec1c1-3687-49b2-85c7-2681fd6f0b67" />


Open Two Browser Tabs:
One for your lab checklist, another for managing osTicket tasks.

<img width="423" height="248" alt="OS TICKET 2" src="https://github.com/user-attachments/assets/40e643b1-03fb-453c-955a-79b79428922e" />


Open Two Browser Tabs:
One for your lab checklist, another for managing osTicket tasks.

Log in as Admin and Configure Departments:
In the admin panel, archive the Maintenance department and set CIS Admin to “top level.”
Create a Ticket as End User:
Switch to the end user portal and create a ticket (e.g., Karen reports online banking down).


<img width="768" height="305" alt="os Ticket 3 " src="https://github.com/user-attachments/assets/87980dc8-a990-4b61-8300-0753fa43b06f" />

Log in as Help Desk Agent (John):
Review, assign the correct department, set the SLA/severity, and correct the help topic.

Assign/Transfer the Ticket:
Route the ticket to the relevant department or team (e.g., Online Banking).

<img width="536" height="362" alt="OS TICKET 4" src="https://github.com/user-attachments/assets/20ff15ec-d2a5-41af-9547-29b39157e806" />


Log in as Specialist (Jane):
As Jane, take ownership, troubleshoot, update ticket status, and log any actions taken.



Resolve and Close the Ticket:




Mark the ticket as resolved/closed once the issue is fixed and document the outcome.

