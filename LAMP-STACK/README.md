## Lamp Stack Implemetatioin

The Project ( LAMP STACK ) is a comprehensive program designed for individuals seeking to build and deploy web applications using the LAMP stack. This course offers a hands-on learning experience, guilding participants through the process of creating dynamic websites by combining Linux, Apache, MySQL, and PHP. throughout the course and project implementation, participants will gain a solid understanding of the LAMP stack components and their roles in web application develoment. Starting with an introduction to the LAMP stack architecture, learners will explore the benefits and advantages of using this powerful combination of technologies.


The course/project covers essential topics such as setting up a Linux environment, configuring the Apache web server, managing MySQL databases, and writting PHP code for server-side functionlity. Participantss will learn how to install and configure the necessary software components, ensuring a smooth and optimized development environment. By following the practical examples,demo shown and engaging in hands-on exercises, participants will gain proficiency in building dynamic web applications. They will learn how to handle user requests, interact with databases, process forms, and implement security measures. Additionally, the course/project will cover common development frameworks and tools that can enhance productivity and simplify web application development.


The Project ( LAMP Stack ) goes beyond the basics, delving into advanced topics such as performance optimization, debugging, and deployment strategies. Participants will gain insights into best practices for scaling for scaling application, securing data, and ensuring the robustness of their projects. Upon completion of the course/project, participants will have acquired the skills and knowledge required to develop and deploy web applications using the LAMP stack. Whether pursuing personal project or working in a professional setting, this project will equip you with the expertise to leverage the power of the LAMP stack and build robust, scalable, and secure web applications.


## Web Stack Implementation ( Lamp Stack ) In AWS

As you kick off your career in DevOps,you will soon realise that everything you will be doing as a DevOps engineer is around software,websites,applications etc. And,there are different stack of technologies that makes different solution possible. These stack of technologies are regarded as **WEB STACK**. Example of web stack include **LAMP**, **LEMP**, **MEAN**, and **MERN** stacks. As you proceed in your journey, you will be required to understand and implement all of these technology stacks. Lets have a short close up on what a Technology stacks is.

## What Is a Technology Stacks?

A technology stack is a set of frameworks and tools used to develop a software product. This set of frameworks and tools are very specifically chosen to work together in creating a well-functioning software. They are acronymns for individual tectnologies used together for a specific technology product. Some examples are....

• **LAMP** ( Linux, Apache, MySQL, PHP or Python, or Perl )

• **LEMP** ( Linux, Nginx, MySQL, PHP, or Python, or Perl )

• **MERN** ( MongoDB, ExpressJS, ReactJS, NodeJS )

• **MEAN** ( MongoDB, ExpressJS, AngularJS, NodeJS )

**WARNING**: Most of the things you will be doing at the early days may not mean a lot to youy. Sometimes it may seem like you are just copying and pastig. That is absolutely fine. I want some concepts to begin to register in your sub-conscious mind, and without you realising it, you are building up skills. although, there are certain traps that will require you to troubleshoot along the way. So watch out for them in all your project implementations.

**After** succesful competion of **PBL** projects **1** to **4**, you will be able to achieve the following.

1. Become very confident on the Linux Tereminal

2. Deepen your understanding of Web Stack and familiarity between the differences between the different Web Technology stacks such as **LAMP**, **LEMP**, **MEAN**, **MERN** stacks

3. Solid Linux administration skills in storage management, NFS, troubleshooting, and basic networking.

4. Basic knowledge of AWS platform and components used to host a Website of various Web stacks.

Being able to work with Linux require the ability to work outside the level of your present knowledge. It means that in the real world, you will be faced with tasks that you never worked on before, and with **Google** search and its results, you can achieve a lot.
Thanks to "**Google**!!!". It is one of the essential skills you will need to develop - constructing a correct search query for Google to process and having the ability to comb through resources that interpretes into a potential solution for you is a great skill to have as well.

**Side Self Study**

1. conduct a Google search on what software development life cycle (SDLC) is and document your finding in a Google world file.

2. Conduct another Google search, understand what LAMP stack means.

3. Read about *'**chmod**'* and *'**chown**'* commands in Linux and understand how access and ownership of files and directories work.

4. Learn what TCP and UPD terms mean and how they are different. List down ports most commonly used in Web (http, https, ssh, telnet, ftp, sftp, telnet)

5. Get yourself familiar with basic text editing in **Vi (Vim)** editor.

**Instructions On How To Submit Your Work For Review And Feedback**

As a beginner it would be nice that you also set up your workspace for learning.

**IMPORTANT NOTE**: For Mac user you do not need to download windowes terminal as you already have a terminal by defualt


## Preparing Prerequisites

**Step 0 - preparing prerequisites**

In order to complete this project you will need an AWS account and a virtual server with Server OS.

**AWS** is the biggest Cloud Service Provider and it offers a free tier account that we are going to leverage for our projects.

Do not focus too much on AWS itself right now, there will be a proper Cloud introduction and configuration projects later in this course.

Right now, all we need to know is that AWS can provide us with a free virtual server called **EC2 (Elastic Compute Cloud)** for our needs.

Spinning up a new EC2 instance (an instance of a virtual server) is only a matter of a few clicks.

### Follow these instructions below to get yourself set up.

1. Register a new AWS account 

2. Select your preferred ergion (the closest to you) and launch a new EC2 instance of t2.micro family with Ubuntu Server 20.04 LTS (HVM)

**IMPORTANT** - save your private key (.pem file) securely and do not share it with anyone! If you lose it, you will not be able to connect to your server ever again!

**IMPORTANT NOTICE** - Both *Putty* and *ssh* use the **SSH protocol** to establish connectivity between computers. It is the most secure protocol because it uses crypto algorithms to encrypt the data that is transmitted - it uses TCP port 22 which is open for all newly created EC2 instances in AWS by default. Most of these terminologies will make more sense to you as you proceed. So for now, if nothing makes sense, just ignore. But be assured that the information is already registered in your sub-conscious mind. So it will become useful to you soon.

The process to connect to the virtual server is defferent between Windows and Mac. So lets take a quick tour.

**(Windows)** - Connecting to EC2 using Putty.

Remember the private key your downloaded from AWS while provisioning the server? It is a ***PEM*** file format. You can open it up to see the content and have a glimpse of what a ***PEM*** file looks like.

Now, we are going to use that ***PEM*** key to connect to our EC2 Instance via ***ssh***.

On, windows the windows terminal tool is not installed by default, you need to install it.

**IMPOORTANT** - Anywhere you see these anchor tags **< >** , going forward, it means you will need to replace the cointent in there with values specific to your situation.

**( Macbook )** Connecting to EC2 using the terminal

• The terminal is already installed by default. You just need to open it up.

• You do not need to conveert to a **.ppk** file . just use the same key as downloaded from AWS.

• Change directory into the location where your **PEM** file is. Most likely will be in the **Downloads** folder.


## Installing Apache And Updating The Firewall

Step 1 - Installing Apache and updating the firewall

**What is Apache?**

**Apache HTTP Server** is the most widely used web server software. Developed and maintained by Apache Software Foundation, Apache is an open source software available for free. It rubs 67% of all webservers in the world. It is fast, reliable , and secure. However, websites and other applications can run on other web server software as well. Such as **Nginx, Microsoft's IIS,** etc.

**Install Apache using Ubuntu package manager**

Use the following command;

• $ sudo apt update

• $ sudo apt install apache2


![Alt text](<Images/Screenshot 2024-01-09 at 02.51.47.png>)


To verify that apache2 is running as a Service in your OS,use the following command

• $ sudo systemctl status apache2


![Alt text](<Images/Screenshot 2024-01-09 at 02.55.34.png>)

Lets try to check how we can access it locally in our Ubuntu shell, run any of this command;

• $ curl http://locathost:80

• $ curl http://127.0.0.1:80


![Alt text](<Images/Screenshot 2024-01-09 at 03.15.02.png>)

These 2 command above actually do pretty the same - they use **'*curl*'** command to request our Apache HTTP Server on port 80 (actually you can even try to not specify any port - it will work anyway).


## Installing MySql

Step 2 - Installing MySQL

Now that you have a web server up and running, we need to install a **Database Management system (DBMS)** to be store and manage data for your site in a **relational database. MySQL** is a popular relational database management system used within PHP environment, so we will use it in our project.

Again, use 'apt' to acquire and install this software:

• $ sudo apt install mysql-server

When prompted, confirm installation by typing **Y**, and then **ENTER**.


![Alt text](<Images/Screenshot 2024-01-09 at 17.15.41.png>)

When the installation is finished, log in to the MySQL console by typing:

• $ sudo mysql

This will connect to the MySQL server as the administrative database user **root**, which is inferred by the use of sudo when running this command. You should see output like this:


![Alt text](<Images/Screenshot 2024-01-09 at 17.25.11.png>)

Its recommanded that you run a security script that comes pre-installed with **MySQL**. This script will remove some insecure default settings and lock down access to your database system. Before running the script you will set a password for the **root** user, using **mysql_native_password** as default authentication method. The user's password is **PassWord.1** .

### Exit the MySQL shell with:

• mysql> **exit**

### Start the interative script by running:

• $ sudo mysql_secure_installation

This will ask if you want to configure the **VALIDATE PASSWORD PLUGIN** .

**Note**: Enabling this feature is something of a judgment call. if enabled, passwords which don't match the specified criteria will be rejected by MySQL with an error. It is safe to leave validation disabled, but you should always use strong, unique password for database credentials.


![Alt text](<Images/Screenshot 2024-01-11 at 01.40.49.png>)


## Installing PHP 

Step 3 - installing PHP

**PHP** is the component of our setup that will process code to display dynamic content to the end user. In addition to **php** package, you'll need **php-mysql**, a PHP module that allow PHP to communicate with MySQL-based databases. You'll als need **libapache2-mod-php** to enable Apache to handle PHP files. Core PHP packages will automatically be installed as dependencies.

To install these 3 package at once, run:

• $ sudo apt install php libapache2-mod-php php-mysql


![Alt text](<Images/Screenshot 2024-01-11 at 02.04.24.png>)

Once the installation is finished, you can run the following command to confirm your PHP version:

• php -v


![Alt text](<Images/Screenshot 2024-01-11 at 02.08.10.png>)

At this point, your LAMP stack is completely installed and fully operational.

• Linux (Ubuntu)

• Apache HTTP Server

• MySQL

• PHP

