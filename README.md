<p align="center">
<img src="https://github.com/niloymridul/osprereqs/assets/139414980/14148678-3d21-4da3-acb6-9cfb9ddf9903" height="40%" width="40%" alt="Kali Linux logo"/>
</p>

<h1>osTicket - Prerequisites & Installation Process</h1>
Welcome to the osTicket tutorial. This part of the tutorial will be detailing the setup of osTicket and usage of Microsoft Azure.<br />

<h2>Environments & Softwares Used</h2>

- Microsoft Azure
- osTicket
- Virtual Machines
  
<h2>Project Steps</h2>

<p>
Welcome to the osTicket tutorial. This part of the tutorial will be detailing the setup of osTicket.

Before start installing, let's talk about osTicket, what is does, and why we need it. osTicket is a popular open-source support ticket system. 

Open source means that the source is made for anyone to use or alter and distribute as they see fit. 

A support ticket system is software meant typically for help desk professionals and said software is used to process and monitor customers/client issues from the moment they come in until they manage to get some form of a resolution.
</p>

<p align="center">
<img src="https://github.com/niloymridul/osprereqs/assets/139414980/fac9df13-bd34-42e8-8ba9-e6aab8b8683f)"  alt="Azure logo"/>
</p>
<p>
With this in mind, we are going to use Microsoft Azure (a cloud computing platform created and managed by Microsoft that provides various services online). If you hadn't already made an account, go ahead and do so. 

[Click here to go to the official download webpage of Microsoft Azure and create an account!](https://azure.microsoft.com/en-us/free)

Once you have logged in you will have to make a Resource Group. A resource group in Microsoft Azure is simply a container that holds resources/services such as virtual machines, web apps, databases, and more. It's important for staying organized and more important for dividing and protecting certain resources from different departments of companies.

Going off from that point, we will need to create a Resource Group which is where we will put our virtual machine. Now, similar to my VirtualBox tutorial, a virtual machine is an operating system created using software on one physical computer in order to emulate the functionality of another separate physical computer. Azure does this by having their own servers and systems that do this for us.
</p>

<p>
We can name our resource group whatever we want but for this tutorial, we will call this osticketpractice. Now within our resource group, we will then create a virtual machine called Vm-osticket. We will be making a Windows 10 virtual machine.

The name isn't important but it should be something that you should be able to remember and we will be placing it in our resource group. While you create your username and password, be sure it is something that you can remember. Also, be sure to create a virtual network (which it will do automatically) and have it be placed inside the network group so we can connect with the virtual machine with no concern whatsoever along with any other virtual machines we choose to make when working on this program. Now wait a few minutes for it to be created.

Now I want you to connect with this. Go to Virtual Machines, click on the newly made virtual machine, and observe the page. On the page, I want you to copy the IP address by right-clicking the line and pressing copy or pressing the copy button you can click on while hovering next to the IP address. Next, I want you to go ahead and go ahead open the application that you typically use to remotely open a desktop. 

For Windows users, you will need to type in the search bar Remote Desktop Connection. Afterward, you will need to type in both username and password so in case it tries to login you into another account you will need to click More Choices -> Use a different account. For Mac Users, you will need to install an app from the app store such as a remote desktop, and then type in the IP address and credentials.

After you typed in your credentials, you will have to log in. The next thing we will need to do is install all of the necessary files needed for osTicket to be set up.
The link down below will take you to a google drive page of all the needed files but for now, download them as a Winrar zip file.

[Click here for the necessary installation files for OSTicket.](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)
If you have trouble installing these folders, you might need to install these files through Google Chrome.

While it installs, we can go to the next step. We will need to enable certain features that are needed for osTicket to work.

- IIS Management Conole - This will allow us to manage Web server features and individual sites such as the website of OSTicket
- CGI (Common Gateway Interface) - Interface specification that enables web servers(osTicket is one) to execute programs to process website user requests such as submitting tickets.
- Common HTTP Features - This adds to the others as it enables things such as directory browsing and HTTP errors that are needed for osTicket.

Now in order to turn these on, you will need to click the following order. 
Control Panel -> Programs -> Turn Windows Features on and off.

Afterward, just simply follow the folder path posted below. The Xs mean that you need to click on them.
Internet Information Services  -> World Wide Web Services -> Application Development Features ->
[X] CGI
[X] Common HTTP Features

Internet Information Services -> Web Management Tools -> IIS Management Console
[X] IIS Management Console

Now we start installing things one by one in the package we had. Unpack the package in your downloads, follow the steps, and then start installing in this order. You only typically need to install and hit agree when running the downloading exe files.

- 1 - PHP Manager for IIS. File name is PHPManagerForIIS)V1.5.0.msi
- 2 - Rewrite Module. File name is rewrite_amd64_en-US.msi. 
- 3 - Create C:\PHP
- 4 - Extract PHP 7.3.8 into the PHP folder that we just created in the C drive. Look at the image.
- 5 - Install VC redist.x86.exe.Install following this simple clicking order. Typical Setup -> Launch Configuration Wizard (after installation) -> Standard Configuration. To modify security settings, you will need to set up a root password. In this tutorial, we will Password1 but you may use whatever you wish.
- 6 - I want you to type in IIS in the search bar. When you see Internet Information Service, run it as administrator. 
- 7 - When you see the interface, click PHP Manager. We need to register a PHP manager. Click on register new PHP version then click on the path to the PHP folder and click on the cgi folder. Then go back to the main menu interface and restart the server (Either by hitting restart or stopping it and then turning it on).
Note: PHP is an open-source, server-side programming language that is used for customer relationship management systems such as osTicket and can be written into HTML which osTicket is used on.
- 8 - Install osTicket. We will do it by copying the upload folder and putting it in c:\inetpub\wwwroot. We will then rename it to osTicket.
- 9 - Reload IIS either by restarting or stopping and starting it again.
- 10 - Go to sites -> Default in middle panel -> osTicket -> Browse*:80(http) to check the page. Note: IT IS IMPORTANT THAT when you follow this order of clicks the Default Web Site has an arrow next to it to keep in mind.
- 11 - As you can see it is a welcome page, but we will have to adjust our settings to change it osTicket. Go back to the IIS main menu and click PHP Manager. Go ahead and click enable or disable an extension. We have to enable the following extensions and please go ahead and type parts of them in the filter search bar.
- 12 - We will rename a file and please follow this order to the exact path location and file name.
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
- 13 - After renaming, we have to assign permissions to it. First, right-click on it to access its properties. Go to security and press advanced. First, we will remove all inheritance by clicking disable inheritance and then remove all. Then we will add a permission. Click on add which is above enable inheritance. Click Select a principal. Then we will click and type everyone in the object name box and then hit ok. Then we will grant everyone full control which will enable everyone. Then hit ok and exit out of the property windows.
- 14 - Click on this HeidiSQL file and click the link in the Word document file. Just keep clicking next if anything and launch HeidiSQL. Skip updates and create a new session in the root folder which can be done by clicking on the arrow next to New. Put the username and password as something you can remember. 
- 15 - Open the newly made session. Create a new database called osTicket.
- 16 - Now comes the setup of osTicket account. Click continue on the osTicket page. You do not actually have to put in an actual email but in this case, just make one up and be sure to remember it. In this case, you can follow my lead. Note that the default email is the email that receives requests and issues from customers.
Helpdesk Name: Hugh Neutron
Default Email: duckneutron@neutron.com
MySQL Database: osTicket
MySQL Username: root
MySQL Password: Password1
You will need to fill out the Admin User info so be sure to remember it when you fill out the information even if it isn't real. Then click Install now.

- 17 - It should be complete by now. To check, browse your help desk login page: http://localhost/osTicket/scp/login.php. Feel free to log in and experiment.

And check the End User osTicket URL:
http://localhost/osTicket/ 

- 18 - The last thing we need to do is clean up and reset permissions so no one can alter or adjust the website based set up.
So delete the Setup folder so we can't alter any setup. The path is the following - C:\inetpub\wwwroot\osTicket\setup
We will also need to set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php

</p>
