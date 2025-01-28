<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This is a tutorial that outlines the prerequisites and installation of the open-source help desk ticketing system osTicket!<br />

<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop (RDP)
- Internet Information Services (IIS)
- Windows 10 

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Create a Resource Group in Azure and assign a VM
- Install MySQL
- Install HeidiSQL 
- Install PHPManager for IIS
- Install Rewrite
- Install Microsoft Visual C++ Redistributable
- Install osTicket v1.15.8

<h2>Steps to complete Installation</h2>

Create a new resource group in Microsoft Azure

![image](https://github.com/user-attachments/assets/1b8e9395-a387-424c-a007-97f908d27b99)

Create a new Virtual Machine (VM) and make sure it's in the same region & inside of your new resource group. Username and password can be set to anything, we will be using that information to login the VM through Remote Desktop! When creating the VM, Azure will create a new virtual network (V-net). 

![Lab2-2](https://github.com/user-attachments/assets/9ce2d7dc-2e78-4a15-a8c6-4c4757761800)

Open the Remote Desktop application and connect to the VM using the corresponding IP Address and credentials.

![Lab2-3](https://github.com/user-attachments/assets/ea963cee-fea7-45f6-8824-d8064b95e122)

Now we can start the osTicket pre-requisite installation process! Start by installing IIS (Internet Information Services). Navigate to the Windows search bar -> Type "Control Panel" -> Click "Programs" -> "Turn Windows features on or off" -> Look for "Internet Information Services", and select.

![Lab2-4](https://github.com/user-attachments/assets/2777eebf-a8af-4dc4-baf9-0e565264e6ce)

Once selected, expand IIS -> expand "World Wide Web Services" -> expand "Application Development Features" -> Select "CGI" -> Press "OK" to download. Note: CGI will be needed to act as a middleman between IIS and PHP! It will execute PHP data for the IIS.

![Lab2-5](https://github.com/user-attachments/assets/3d1f184f-8672-44a0-a4f5-1c9c35c94cdb)

Install PHP Manager for IIS

![Lab2-6](https://github.com/user-attachments/assets/759cc292-09c1-455f-b4c6-21cd50e41669)

Install ReWrite 

![Lab2-7](https://github.com/user-attachments/assets/e976c365-488a-4c73-835c-ecc02c3a734c)

Install Microsoft Visual Code C++

![Lab2-8](https://github.com/user-attachments/assets/a6a9d6c4-a54f-40fe-be3c-2b2758754c2a)

When At MySQL Server accept the terms and continue, click on typical installation and install. When finished you will reach the setup wizard for MySQL. MySQL will act as our database and store all ticket information, user details, logs and attachments, etc.

![Lab2-9](https://github.com/user-attachments/assets/e1dfc8fd-651a-442d-98ca-87ceefcd6b3d)

On the next wizard for MySQL, select the Standard Configuration and hit next -> next.

![Lab2-10](https://github.com/user-attachments/assets/e64bdea9-575c-49a1-91b1-32e9c6a59d70)

Now type in a new root password, this can be personalized to whatever you like! Select next -> execute.

![Lab2-11](https://github.com/user-attachments/assets/57c43961-9838-432d-8e19-e5d1ec0ea01f)

Create a new PHP folder and extract the "php-7.3.8-nts..." file into the new PHP folder you made.

![Lab2-12](https://github.com/user-attachments/assets/ff7c6c6e-fee8-4ffb-bbe8-38af118a646c)

Go to search bar and type "IIS" and run the application as an administrator.

![Lab2-13](https://github.com/user-attachments/assets/532a62f9-1d07-499a-b7aa-6f6e9b444652)

Open PHP Manager and select "Register new PHP version". Enter the path towards the new PHP folder and specify "php-cgi.exe". Now restart the IIS by first pressing stop and then start.

![Lab2-14](https://github.com/user-attachments/assets/a2e18a17-f859-4660-b252-d7d9d21ef117)

![Lab2-15](https://github.com/user-attachments/assets/c959cc2f-4bbe-42d6-8fb0-e64a8bbed194)

Extract osTicket-v-1.15.8. After extracting, open the unzipped folder and move the folder named "upload" inside the "wwwroot" folder. Rename "upload" folder to "osTicket" and save.

![Lab2-16](https://github.com/user-attachments/assets/c9ef52f1-3a47-487b-81aa-06b1beb6380a)

![Lab2-17](https://github.com/user-attachments/assets/1acf2cdf-83db-4659-859f-f8b3768a13bc)

In IIS navigate to the left hand side and expand "OSTicket-vm" -> expand "Sites" -> expand "Default Web Site" -> click "osTicket". Then click "Browse *.80 (http)" to open the local site for osTicket. Some plugins aren't enabled upon installing and need to be manually enabled.

![Lab2-18](https://github.com/user-attachments/assets/f5e1366d-f137-47f4-b7be-e9a4b8fee610)

Select "Enable or disable an extension" and enable the following: "php_imap_dll", "php_intll.dll" & "php_opcache.dll". Now the necessary plugins are on and we can proceed.

![Lab2-19](https://github.com/user-attachments/assets/53c34376-8cfd-4a4e-87f2-1cfc9398df87)

![Lab2-20](https://github.com/user-attachments/assets/e677671e-61f1-4094-b163-3e34d5389fbd)

Rename the "ost-sampleconfig.php" to "ost-config.php" 

![Lab2-21](https://github.com/user-attachments/assets/369709f1-8cbb-4a02-bd71-87e673692555)

Disable the inheritance from the standard users and instead enable it for "Everyone" and give them full control.

![Lab2-22](https://github.com/user-attachments/assets/380041c0-d01c-42c4-b8e7-2e7b10d34037)

![Lab2-23](https://github.com/user-attachments/assets/7796e41f-9abf-4285-b22d-2591bd995e84)

![Lab2-24](https://github.com/user-attachments/assets/51a17e9c-1ec6-41db-a009-ace6a56128b4)

![Lab2-25](https://github.com/user-attachments/assets/ef71a56c-fa9f-473f-b9a0-0d5e6f9ce3c8)

![Lab2-26](https://github.com/user-attachments/assets/72d02522-59dd-41e0-852f-a96c0899d296)

![Lab2-27](https://github.com/user-attachments/assets/00d8fbae-a071-4348-a42a-587006fe4b9f)

![Lab2-Cleanup](https://github.com/user-attachments/assets/fdd51c67-6f6b-4292-92c6-20c8543ac210)
