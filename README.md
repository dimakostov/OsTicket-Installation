![image](https://github.com/user-attachments/assets/94648995-696b-49ac-a5a7-06206f2100ce)<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
In this lab, I install osTicket from the ground up using the necessary installation files. There are a few steps to take before the installation of the ticketing system. This lab is done using a Windows 10 Pro VM made on Azure. The necessary installation files that are referenced and used are located in the list of Prerequisites below.


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10 Pro</b>

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- Internet Information Services (IIS)
- PHP Manager
- Rewrite Module
- VC Redist
- MySQL
- Heidi SQL
- osTicket
- Link to downloads: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6


<h2>Installation Steps</h2>


![image](https://github.com/user-attachments/assets/b05f7e63-75be-4b56-91ca-bde9a3b27eef)


<p>
Before installing any files, Internet Information Services (IIS) needs to be enabled. We are installing osTicket locally and it needs IIS in order to function. To turn on IIS, open the Control Panel. From the Control Panel, open Programs and and Turn Windows Features On or Off. Within this menu, expand Internet Information Services, expand Web Management Tools and enable IIS Management Console. Click and expand World Wide Web Services and expand Application Development Features. In Application Development Features, enable CGI and click ok to confirm.
</p>
<br />

![image](https://github.com/user-attachments/assets/9f9f8bdf-fb8f-4734-aed9-8b570c5ace33)

<p>
After enabling IIS, download and install PHP Manager for IIS (PHPManagerforIIS_V1.5.0.msi) from the installtion files folder. Download and install the Rewrite Module (rewrite_amd64_en-US.msi) after installing PHP Manager for IIS.
</p>
<br />

![image](https://github.com/user-attachments/assets/971acfda-914c-47b3-a1e6-97a0d3d05204)

<p>
After installing the Rewrite Module, create a new folder/directory called C:\PHP on the Windows (C:) drive. This new folder will be used to unzip the contents from the PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) zip folder downloaded from the installation files. Extract all contents from the zip folder into the C:\PHP folder.
</p>
<br />

![image](https://github.com/user-attachments/assets/eee3b6bb-dc38-47df-92d3-913958544161)

<p>
Next, download and install VC_redist.x86.exe from the installation files.
</p>
<br />

<p>
![image](https://github.com/user-attachments/assets/0c0d9351-8240-4c9b-ae3b-8f74fd8dd07d)

</p>
<p>
Next, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the installation files. Within the MySQL setup wizard, click "I agree" and select a Typical install and Install. Launch the Configuration Wizard after the installation. Select Standard Configuration and select Install As Windows Service and make sure Launch the MySQL Server automatically is checked. For credentials, the username will be root and the password is Password1. In a practical setting, the credentials will be more secure so that they are not easily guessed. For the purposes of this lab, the standard credentials (root and Password1) will do.
</p>
<br />

![image](https://github.com/user-attachments/assets/82f1468f-4233-4086-81dc-517cc35c0330)

![image](https://github.com/user-attachments/assets/45eb0db2-a886-402a-b152-36566c5f1659)

<p>
Before installing osTicket, configurations need to be made within IIS. Open IIS as an admin and select PHP Manager. Within PHP Manager, select Register new PHP version. Select Browse and select the PHP CGI executable file (php-cgi.exe) within the PHP folder created earlier in the lab. After registering the PHP version, reload the IIS server within the management console.
</p>
<br />

![image](https://github.com/user-attachments/assets/e68ab546-50fe-4aec-bd3c-16f5cc8944fa)

<p>
From the installation files, download osTicket v1.15.8. Extract and copy the "upload" folder to the following path: c:\inetpub\wwwroot. Within the c:\inetpub\wwwroot folder, rename "upload" to "osTicket." Reload the IIS server afterwards.
</p>
<br />

![image](https://github.com/user-attachments/assets/7eda5a86-0ffe-4797-ade6-ca0074aaf62f)

![image](https://github.com/user-attachments/assets/0830f9e8-327b-41a1-9fd3-3378a44a284f)

![image](https://github.com/user-attachments/assets/e6a59a09-28dd-4a36-8cb9-c54aad4dd186)

<p>
Within the IIS console, browse to Sites -> Default -> osTicket. Click "Browse *:80" and the installation page for osTicket will now show up. Some extensions are not enabled and they will be enabled with the IIS console before installing osTicket. To do so, click on PHP Manager while in the osTicket menu in IIS. Click on "Enable or disable an extension." Enable the following extentions: php_imap.dll, php_intl.dll, php_opcache.dll.
</p>
<br />

![image](https://github.com/user-attachments/assets/77b09c36-fec4-4c00-ad95-dc54e546d0b8)

![image](https://github.com/user-attachments/assets/0c844d5a-7ba9-47a6-890a-e99d1267f50d)

<p>
Before continuing to install osTicket, a file needs to be renamed as well as have its permissions changed. From C:\inetpub\wwwroot\osTicket\include, rename ost-sampleconfig.php to ost-config.php. The newly named ost-config.php will have its permissions changed. Open its Properties and change the following permissions: Disable inheritence -> Remove All and New Permissions -> Everyone -> All.
</p>
<br />

![image](https://github.com/user-attachments/assets/b5c69067-bf59-40e8-95d9-3c6d490a7e66)

![image](https://github.com/user-attachments/assets/b2d1c6c6-02a2-47bd-b5c5-c903cd51018d)

<p>
From the installation files, download and install HeidiSQL. Create a new session with HeidiSQL and enter the password used in the installation of MySQL earlier. Within the new session, right-click on Unnamed and create a new database named osTicket. 
</p>
<br />

![image](https://github.com/user-attachments/assets/b513fe74-2f71-402d-85b3-14ef495a3ab1)

<p>
Within osTicket browser window, enter the necessary details to set up osTicket. For the MySQL database, use the credentials used for MySQL and HeidiSQL.
</p>
<br />

![image](https://github.com/user-attachments/assets/5e27ce3c-3291-4073-b965-00bf0ae8562f)

![image](https://github.com/user-attachments/assets/fb286a39-a115-42da-861c-291e18dd5a92)

<p>
After everything is done, osTicket should now be installed! Before continuing to use osTicket, some clean up has to be done. First, delete the setup folder found in C:\inetpub\wwwroot\osTicket. Next, return to C:\inetpub\wwwroot\osTicket\include and change the permissions of the ost-config.php file. The file should no longer have full access to Everyone. Revert the permissions to "Read" only. 
</p>
<br />

<h2>osTicket Installed!</h2>

osTicket is now installed and ready to be used. I used osTicket to understand how ticketing systems work and how to resolve tickets. In IT Support, I have to work with a team to solve a person's IT related issues through the use of a ticketing system. I used this lab as a means to set up a ticketing system from the ground up and lay the grounds for what I will be doing in the future.
