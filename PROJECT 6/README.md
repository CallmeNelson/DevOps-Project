# Understanding Client-Server Architecture

## Client-Server Architecture With MySQL

### Understanding Client-Server Architecture

Client-Server refers to an architecture in which two or more computers are connected together over a network to send and receive requests between one another.

In their communication, each machine has its own role: the machine sending is usually referred as "Client" and the machine responding (serving) is called "Server".

In thsi case, our Web Server has a role of a "Client" that connects and reads/writes to/from a Database (DB) Server (MySQL, MongoDB, Oracle, SQL Server or any other), and the communication betweeen them happens over a Local Network(it can also be internet connection, but it is a common practice to place Web Server and DB Server close to each other in local network).

## Real example of **LAMP** website

This **LAMP** website server(s) can be located anywhere in the world and you can reach it also from any part of the globe over global network - internet.

Assuming that you go on your browser, and typed in there **www.propitixhome.com**. It means that your browser is considered that **"Client"**. Essentially, it is sending request to the remote server, and in turn, would be expecting some kind of response from the remote server.

Lets take a very quick example and see Client-Server communicatation in action.

Open up your Ubuntu or Windows terminal and run **curl** command:

• $ curl -Iv www.propitixhomes.com

**Note:** If your Ubuntu does not have 'curl', you can install it by running **sudo apt install curl**

In this example, your terminal will be the **client**, while **www.propitixhomes.com** will be the **server**


![Alt text](<Images/Screenshot 2024-02-06 at 16.47.36.png>)

Another simple way to get a server's IP address is to use a simple diagnostic tool like 'ping', it will also show round-trip time - time for packets to go to and back from the server, this tool uses **ICMP protocol.**


# Implement a Client Server Architecture Using MySQL Database Managetment System (DBMS).

**1•** create and configure two Linux-based virtual server (EC2 instances in AWS).

• Server A name - `mysql server`

• Server B name - `mysql client`

**2.** On **mysql server** Linux Server install MySQL software.

• Sudo apt update


![Alt text](<Images/Screenshot 2024-02-15 at 02.25.19.png>)

• Sudo apt install mysql-server


![Alt text](<Images/Screenshot 2024-02-15 at 02.28.15.png>)

• Sudo systemctl enable mysql


![Alt text](<Images/Screenshot 2024-02-15 at 02.36.41.png>)

**3.** On **mysql client** Linux Server install MySQL Client software.

• Sudo apt update


![Alt text](<Images/Screenshot 2024-02-15 at 02.51.47.png>)

• Sudo apt install mysql-client


![Alt text](<Images/Screenshot 2024-02-15 at 02.55.01.png>)

**4.** By default, both of your EC2 virtual servers are located in the local virtual network, so they can communicate to each other using **local IP addresses.** Use **mysql server's** local IP address to connect from **mysql client**. MySQL server uses TCP port 3306 by default, so you will have to open it by creating a new entry in 'Inbound rules' in 'mysql server' Security Groups. For extra security, do not allow all IP addresses to reach your 'mysql server' - allow access only to the specific local IP address of your 'mysql client'.


![Alt text](<Images/Screenshot 2024-02-15 at 03.24.16.png>)

• Sudo mysql_secure_installation


![Alt text](<Images/Screenshot 2024-02-15 at 03.51.32.png>)

• Sudo mysql


![Alt text](<Images/Screenshot 2024-02-15 at 04.08.20.png>)

**5.** You might need to configure MySQL server to allow connection from remote hosts.

Run below code:

• sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf 

Replace '127.0.0.1'to'0.0.0.0'


![Alt text](<Images/Screenshot 2024-02-15 at 04.25.52.png>)

Restart the server;


![Alt text](<Images/Screenshot 2024-02-20 at 03.02.39.png>)

**6.** From **mysql client** Linux Server connect remotely to **mysql server** database Engine without using **SSH**. You must use the **mysql** utility to perform this action.


![Alt text](<Images/Screenshot 2024-02-22 at 01.29.52.png>)

**7.** Check that you have successfully connected to a remote MySQL server and can perform SQL queries:

**COPY Below Code;**

* Show databases;


![Alt text](<Images/Screenshot 2024-02-22 at 01.35.27.png>)