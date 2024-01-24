## WEB STACK IMPLEMENTATION (Lemp Stack)

Let's dive into the architecture of the Lemp stack, understanding how Linux provides a solid foundation, Nginx serves as a powerful web server, MySQL handles the database, and PHP empowers server-side functionality.

Throughout the course/project,we will set up a Linux environment, configure Nginx for optimal performance, manage MySQL database, and develop PHP code to bring application to life. Through the practical and hands-on exercises, you will gain proficiency in building dynamic websites with the LEMP stack. We will explore techniques for handling user requests, interacting with database, processing forms, and implementing robust security measures.

In this project you will implement a similar stack, but with an alternative Web Server - **NGINX**, which is also very popular and widely used by many websites in the internet.

### SIde Self study

1. Make yourself familiar with basic **SQL syntax and most commonly used commands**

2. Be comfortable using not lony VIM, but also **Nano editor** as well, get to know **basic Nano commands**.

### Step 0 - Preparing prerequisites

In order to complete this project you will need an AWS account and a virtual server with Ubuntu OS.

**Hint:** There is simpler way that do not require conversion of **.pem** key to **.ppk** - using **Git Bash**.

Download and install Git Bash, then launch Git Bash and run the following command:

• ssh -i <Your-private-key.pem> ubuntu@<EC2-Public-IP-address>


## Installing the Nginx Web Server

**Step 1 -** In order to display web pages to our site visitors, we are going to employ Nginx, a high-performance web server. We'll use the **apt** package manager to install this package.

For this session, start off by updating your server's package index. Following that, you can use **apt install** to get Nginx installed:

• $ sudo apt update

• $ sudo apt install nginx

When prompted, enter **Y** to confirm that you want to install Nginx.


![Alt text](<Images/Screenshot 2024-01-19 at 00.21.08.png>)

To verify that nginx was sucessfully installed and is running as a service in Ubuntu, run:

• $ sudo systemctl status nginx


![Alt text](<Images/Screenshot 2024-01-19 at 00.29.17.png>)

Before we can receive any traffic by our Web Server, we need to open **TCP port 80** which is default port that web brousers use to access web pagesin the internet.

As we know, we have TCP port 22 open by default on our EC2 machine to access it via SSH, so we need to add a rule to EC2 configuration to open inbound connection through port 80:


![Alt text](<Images/Screenshot 2024-01-23 at 02.01.31.png>)

Our server is running and we can access it locally from the internet. First, let us try to check how we can access it locally in our Ubuntu shell, run:

• $ curl http://localhost:80

or

• $ curl http://127.0.0.1:00


![Alt text](<Images/Screenshot 2024-01-23 at 01.36.04.png>)

These 2 commands above actually do pretty much the same- they use **'curl'** command to request our Nginx on port 80 (actually you can even try to not specify any port - it will work anyway).

Lets test how our Nginx server can respond to request from the internet.

• http://<Public-IP-Address>:80

Another way to retrieve your Public IP address, other than to check it in AWS Web console, is to use following command:

• curl -s http://169.254.169.254/latest/meta-data/public-ipv4

The URL in browser shall also work if you do not specify port number since all web browsers use port 80 by default.

If you see this following page, then your web server is now correctly installed and accessible through your firewall.


![Alt text](<Images/Screenshot 2024-01-23 at 02.04.33.png>)


## Installing MySQL

**Step 2 -** Having a web server up and running, you need to install a **Database Management System (DBMS)** to be able to store and manage data for your site in a **relational database. MySQL** is a popular relational database management system used within PHP environments.

Use **'apt** to acquire and install this software:

• $ sudo apt install mysql-server

When prompted, confirm installation by typing **Y**, and then **ENTER**.


![Alt text](<Images/Screenshot 2024-01-24 at 01.43.55.png>)

When the installation is fininshed, log in to the MySQL console by typing:

• $ sudo mysql

This will connect to the MySQL server as the administrative user **root**, which is inferred by the use of sudo whwn running this command. You should see an output like this:


![Alt text](<Images/Screenshot 2024-01-24 at 01.48.38.png>)

It's recommended that you run a security script that comes pre-installed with MySQL. This script will remove some insecure default settings and the lock down access to your database system. Before running the script you will set a password for the **root** user, using mysql_native_password as default authentication method. We're defining this user's password as **PassWord.1**,

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';

Exit the MySQL shell with:

• mysql> exit

Start the interactive script by running:

• $ sudo mysql_secure_installation

This will ask if you want to configure the **VALIDATE PASSWORD PLUGIN**.

**Note**: Enabling this feature is something of a judgment call. If enabled, passwords which don't match the specified criteria will be rejected by MySQL with an error. It is safe to leave validation disabled, but you should always use strong, unique passwords for database credentials.

Answer **Y** for yes, or anything else to continue without enabling. If you answer "yes", you'll be asked to select a level of password validation.


![Alt text](<Images/Screenshot 2024-01-24 at 02.20.38.png>)

Lets test if we're able to log in tothe MySQL console by typing:

• $ sudo mysql -p

Notice the **-p** flag in this command, which will prompt you for the password used after changing the **root** user password.

To exit the MySQL console, type:

• mysql> exit


![Alt text](<Images/Screenshot 2024-01-24 at 02.43.04.png>)

Your MySQL server is now installed and secured. Next, we will install PHP, the final component in the LEMP stack.