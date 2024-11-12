# osticket-prereqs

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

- Create a Virtual Machine in Azure
- Install Web Platform Installer
- Install osTicket v.1.15.8
- Install HeidiSQL
  

<h2>Installation Steps</h2>

Create a resource group called osTicket

![Screenshot 2024-11-12 074128](https://github.com/user-attachments/assets/aeab1e33-75b6-4f57-ae19-584635b9ec29)



Create a Virtual Machine and name it osticket-vm

![Screenshot 2024-11-12 074409](https://github.com/user-attachments/assets/1747cef8-dc48-4b7f-a5e6-b0ed71afbef0)




Connect to Remote Desktop Connection using the public ip address that is given

![image](https://github.com/user-attachments/assets/35706181-0d47-4938-8588-c035c35fd490)

In the VM, download https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD and unzip in onto your desktop. Folder should be called "osTicket_Installation Files"
![image](https://github.com/user-attachments/assets/c74c1aea-ef67-402c-a291-9fdf8f76ad9a)



Head to Control Panel, Install/Enable ISS in Windows with CGI
World Wide Web Services -> Application
Development Features -> [X] CGI

![image](https://github.com/user-attachments/assets/96d66a10-b560-4cb7-80c2-2a5a071879cc)

Install PHP Manager for ISS from the osTicket_Installation

![image](https://github.com/user-attachments/assets/18131491-6df2-45c1-b51e-318baf16dfc6)

Install the Rewrite Module 

![image](https://github.com/user-attachments/assets/0bee4dcc-7129-4815-9179-7ac3e5b77fcc)

Create the directory C:\PHP
![image](https://github.com/user-attachments/assets/a65031dd-c6e7-4bed-aaeb-0f4d4baaf0e4)

Unzip PHP 7.3.8 into the "C:\PHP" folder

![image](https://github.com/user-attachments/assets/de90504c-42eb-4c6e-ae09-934217fef890)

Install VC_redist.x86.exe
![image](https://github.com/user-attachments/assets/11f8571d-e402-46e1-b35f-1adedd2a043b)

Install MYSQL 5.5.62
Set Up -> Launch Configuration Wizard (after install) -> Standard Configuration -> 
Username: root
Password: root
![image](https://github.com/user-attachments/assets/d493b722-3343-4636-9e17-efde573a289c)

Open ISS as an Admin and proceed to register PHP from within ISS (PHP Manager -> C:\PHP\php-cgi.exe)

![image](https://github.com/user-attachments/assets/928243de-9743-442f-91b3-6d8531d63f97)
![image](https://github.com/user-attachments/assets/af7993c8-aff6-4af2-bc0b-d3b915458e3a)

Install "osTicket-v1.15.8zip"
![image](https://github.com/user-attachments/assets/e2736977-485e-4319-a309-9a7bfcc4acae)
Once unzipped, copy the "upload" folder into "c:\inetpub\wwwroot" and proceed to rename "upload" to "osTicket"
![image](https://github.com/user-attachments/assets/5a071124-7a3f-4eef-912b-2e41e5acd076)

Go into ISS and Stop/Start the server. Once that's done, go to sites -> default -> osTicket -> "Browse *:80"
![image](https://github.com/user-attachments/assets/fbac7d00-34ba-47f2-a81e-983d1a0dc016)

![image](https://github.com/user-attachments/assets/ed9abfbe-4bd8-44dd-9982-08ebca6f496d)
Enable Extensions in IIS: Some extensions are not enabled

Go back to IIS, sites -> Default -> osTicket
Double-Click PHP Manager:
![image](https://github.com/user-attachments/assets/cd5fe363-0d5c-43a7-be10-30c6a3049ebc)

Click "Enable or disable an extension".

Enable: php_imap.dll.

Enable: php_intl.dll

Enable: php_opcache.dll:


Refresh the osTicket site in the browser, and observe changes
![image](https://github.com/user-attachments/assets/b54f9ae6-a515-4232-953a-a3c983bfd218)

Rename

From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php.

To: C:\inetpub\wwwroot\osTicket\include\ost-config.php:
![image](https://github.com/user-attachments/assets/ce3d4228-ad77-4497-a3d9-26e115ecae3d)

Assign Permissions: ost-config.php

Disable inheritance -> Remove All:
![image](https://github.com/user-attachments/assets/d1fceb18-db10-4396-afe8-3618b2b5c0b8)

New Permissions -> Everyone -> All:
![image](https://github.com/user-attachments/assets/4121924a-fd40-405d-b178-a6559a1bec6d)


![image](https://github.com/user-attachments/assets/d44aa98b-3d34-4feb-bf8e-e9dc131cb83e)
Continue Setting up osTicket in the browser (click continue)

![image](https://github.com/user-attachments/assets/c6149ea0-39b5-4d4e-8565-ffb00f26d3cc)

Download and Install HeidiSQL

![image](https://github.com/user-attachments/assets/efc30e56-f4d4-426a-8680-d804e966a3a9)
Create a new session. root/Password1

Connect to the session
![image](https://github.com/user-attachments/assets/33c5c5eb-1adf-42ee-b501-1afed4734fb9)

Create a database called "osTicket"
![image](https://github.com/user-attachments/assets/b0631895-47a9-45c5-bd51-901930379ef7)



Continue Setting up osTicket in the browser

MySQL Database: osTicket

MySQL Username: root

MySQL Password: Password1:

![image](https://github.com/user-attachments/assets/24346cea-7949-4e1b-b015-a66a7dace2a4)


Login to the osTicket Admin Panel

(http://localhost/osTicket/scp/login.php)
![image](https://github.com/user-attachments/assets/40e0ad95-03be-4fc0-b8be-db1e155129df)













