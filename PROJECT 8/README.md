# Automating Loadbalancer configuration with Shell scripting

Streamline your load balancer configuration with ease using shell scripting and simple **CI/CD** on Jenkins. This project demonstrates how to automate the setup and maintenance of your load balancer using a freestyle job, enhancing efficiency and reducing manual effort


# Automate the Deployment of Webservers

In the implementing load banlancer with Nginx course, We deployed two backend servers, with a load balancer distributing traffic across the webservers. We did that by typing commands right on our terminal.

In this course we will be automating the entire process. We will do that by writing a shell script that when ran, all that will did manually will be done for us automatically. As DevOps Engineers automation is at the heart of the work we do. Automation helps us speed the deployment of services and reduce the chance of making errors in our day to day activity.


# Deploying and Configuring the Webservers

All the process we need to deploy our webservers has been codified in the shell script below:

* #!/bin/bash

####################################################################################################################
##### This automates the installation and configuring of apache webserver to listen on port 8000
##### Usage: Call the script and pass in the Public_IP of your EC2 instance as the first argument as shown below:
######## ./install_configure_apache.sh 127.0.0.1
####################################################################################################################

set -x # debug mode
set -e # exit the script if there is an error
set -o pipefail # exit the script when there is a pipe failure

PUBLIC_IP=$1

[ -z "${PUBLIC_IP}" ] && echo "Please pass the public IP of your EC2 instance as an argument to the script" && exit 1

sudo apt update -y &&  sudo apt install apache2 -y

sudo systemctl status apache2

if [[ $? -eq 0 ]]; then
    sudo chmod 777 /etc/apache2/ports.conf
    echo "Listen 8000" >> /etc/apache2/ports.conf
    sudo chmod 777 -R /etc/apache2/

    sudo sed -i 's/<VirtualHost \*:80>/<VirtualHost *:8000>/' /etc/apache2/sites-available/000-default.conf

fi
sudo chmod 777 -R /var/www/
echo "<!DOCTYPE html>
        <html>
        <head>
            <title>My EC2 Instance</title>
        </head>
        <body>
            <h1>Welcome to my EC2 instance</h1>
            <p>Public IP: "${PUBLIC_IP}"</p>
        </body>
        </html>" > /var/www/html/index.html

sudo systemctl restart apache2



Fellow the steps below to run the script:

**Step 1:** Provision an EC2 instance running 20.04. You can refer to the course **Implementing load balancer with Nginx** for a refresher

**Step 2:** Open port 8000 to allow traffic from anywhere using the security group. Again refer to the course mentioned above in step one for a refresher.

**Step 3:** Connect to the webserver via the terminal using SSH client

**Step 4:** Open a file, paste the script above and close the file using command below:

* sudo vi install.sh


![Alt text](<Images/Screenshot 2024-03-14 at 19.18.01.png>)

To close the file type the **esc** key **Shift + :wqa!**

**Step 5:** Change the permissions on the file to make an executable using the command below:

* sudo chmod +x install.sh

**Step 6:** Run the shell script using the command below. Make sure you read the instructions in the shell script to learn how to use it.

* ./install.sh PUBLIC_IP



![Alt text](<Images/Screenshot 2024-04-07 at 01.30.55.png>)



# Deployment of Nginx as a Load Balancer using Shell script

### Automate the Deployment of Nginx as a Load Balancer using Shell script

Having successfully deployed and configured two webservers, We will move on to the load balancer. As a prerequisite, we need to provision an EC2 instance running ubuntu 22.04, open port 80 to anywhere using the security group and connect to the load balancer via the terminal.


## Deploying and  Configuring Nginx Load Balancer

All the steps following in the **Implementing Load Balancer with Nginx** Course has been codified in the script below:

Read the instrictions carefully in the script to learn how to use script.

### Steps to Run the Shell Script

**Step 1:** On your terminal, open a file nginx.sh using the command below:

**Step 2:** Copy and Paste the script inside the file

**Step 3:** Close the file using the command below:

* type esc the shift + :wqa!


![Alt text](<Images/Screenshot 2024-03-14 at 20.08.18.png>)

**Step 4:** change the file permission to make it an executable using the command below:

* sudo chmod +x nginx.sh

**Step 5:** Run the script with the command below:

* ./nginx.sh PUBLIC_IP Webserver-1 Webserver-2



![Alt text](<Images/Screenshot 2024-04-07 at 01.11.34.png>)


# Verifying the setup

### Screenshot for webserver onewebserver



![Alt text](<Images/Screenshot 2024-04-05 at 20.49.20.png>)



### Screenshot for webserver Two



![Alt text](<Images/Screenshot 2024-04-06 at 01.22.21.png>)



### Screenshot of load balancer



![Alt text](<Images/Screenshot 2024-04-07 at 01.22.25.png>)