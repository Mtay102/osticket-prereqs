<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This is a tutorial that will outline the prerequisites and installation process of the open-source help desk ticketing system osTicket.<br>

<br>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)


<h2>Operating Systems Used </h2>

- Windows 10</b>

<h2>List of Prerequisites</h2>

- Create an Azure Virtual Machine:
    - Windows 10
    - 2 vCPUs
- Name the Virtual Machine and assign a username and password
- Log into the VM with Remote Desktop

<h2>Installation Steps</h2>


<p>
Within the VM (osticket-vm), download the osTicket-Installation-Files.zip and unzip it onto your desktop. The folder should be called “osTicket-Installation-Files”
</p>

![Install1](https://github.com/user-attachments/assets/04600937-e2c0-40a4-a775-00d08b131180)

<br>

<p>
Next Install / Enable IIS in Windows WITH CGI <br>
  -World Wide Web Services -> Application Development Features -> [X] CGI
</p>

 <br>
 
<p>
Next from the “osTicket-Installation-Files” folder, install PHP Manager for IIS and rewrite
</p>

![Install2](https://github.com/user-attachments/assets/cd9e06de-ee14-4c90-8234-c8ccad01d6b2)


<br>

<p>
  Next Create the directory C:\PHP <br><br>
From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder
<br>
<br>
From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.
<br>
<br>
From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi)<br><br>
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
Username: root
Password: root
</p>

![Install3](https://github.com/user-attachments/assets/45cbd896-e831-491e-8aec-ba82a740580b)

<br> 

<p>
Next Open IIS as an Admin<br>
Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)<br>
Reload IIS (Open IIS, Stop and Start the server)
</p>

<br>

<p>
  Next Install osTicket v1.15.8 From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”
</p>



<br>



<p>
Go to sites -> Default -> osTicket
On the right, click “Browse *:80”
<br>
Note that some extensions are not enabled<br>
<br>
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”<br>
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll<br>
Refresh the osTicket site in your browser, observe the changes
</p>

![Install4](https://github.com/user-attachments/assets/4e7616c0-9eaa-45e5-8989-3ff1571462ad)

<br>

<p>
  Rename: ost-config.php<br>
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php<br>
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
<br>
<br>
Assign Permissions: ost-config.php<br>
Disable inheritance -> Remove All<br>
New Permissions -> Everyone -> All
<br>
<br>
Continue Setting up osTicket in the browser (click Continue)<br>
  - Also complete the admin field
</p>


<br>


<p>
  From the “osTicket-Installation-Files” folder, install HeidiSQL.<br>
Open Heidi SQL<br>
Create a new session, root/root<br>
Connect to the session<br>
Create a database called “osTicket”
</p>

![Install6](https://github.com/user-attachments/assets/bbe63f8b-65b9-4cdf-bca3-927d2dbdd831)

<br>

<p>
  Continue Setting up osTicket in the browser<br>
MySQL Database: osTicket<br>
MySQL Username: root<br>
MySQL Password: root<br>
Click “Install Now!”<br>
</p>

![Install7](https://github.com/user-attachments/assets/bc99a66c-2342-4850-80bd-fb9c52e5f327)

