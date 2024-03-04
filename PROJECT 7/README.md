# IMPLEMENTING LOADBALANCERS WITH NGINX

## Introduction to Load Balancing and Nginx


![Alt text](<Images/Screenshot 2024-02-29 at 14.55.29.png>)

load balancing is like having a team of helpers working together to make sure a big job gets done smoothly and efficiently. Imagine you have alot of heavy boxes to carry, but you can't carry them all by yourself because they are too heavy.

Load balancing is when you call your friends to help you carry the boxes. Each friend takes some of the boxes and carries them to the right place. This way, the work gets done much faster because everyone is working together.

In computer terms, load balancing means distributing the work or tasks among several computers or servers so that no one computer gets overloaded with too much work. This helps to keep everything running smoothly and ensures that websites and apps work quickly and don't get too slow. It's like teamwork for computer!

## Setting Up a Basic Load Balancer

We are going to be provisioning two EC2 instances running ubuntu 22.04 and install Apache webserver in them. We will open port 8000 to allow traffic from anywhere, and finaly update the default page of the webservers to display their public IP address.

Next we will provision another EC2 instance running ubuntu 22.04, this time we will install Nginx and configure it to act as a load balancer distributing traffic across the webservers.

**Step 1:** Provisioning EC2 instance

* Open your AWS Management Console, click on EC2. Scroll down the page and click on Launch instance.

* Under Name, Provide a unique name for each of your webservers.

* Under Application and OS Images, click on quick start and click on ubuntu.


![Alt text](<Images/Screenshot 2024-02-29 at 15.40.07.png>)

* Under Key Pair, click on create new key pair if you do not have one. You can use the same key pair for all the instances you provision for this lesson:


![Alt text](<Images/Screenshot 2024-02-29 at 15.48.12.png>)

* And finally click on launch instance:


![Alt text](<Images/Screenshot 2024-02-29 at 15.50.32.png>)

**Step 2:** Open Port 8000 We will be running our webservers on port 8000 while the load balancer runs on port 80. We need to open Port 8000 to allow from anywhere. To do this we need to add a rule to the security group of each of our webservers

* Click on the instance ID to get the details of your EC2 instance,


![Alt text](<Images/Screenshot 2024-02-29 at 21.40.11.png>)

* On that same page, scroll down and click on security:


![Alt text](<Images/Screenshot 2024-02-29 at 21.43.53.png>)

* Click on security group:


![Alt text](<Images/Screenshot 2024-02-29 at 21.48.13.png>)

* On the top of the page click on Action and select Edit inbound rules:


![Alt text](<Images/Screenshot 2024-02-29 at 21.54.52.png>)

* Add your rules, then Click on save rules:


![Alt text](<Images/Screenshot 2024-02-29 at 22.00.22.png>)

**Step 3:** Install Apache Webserver

After provisioning both of our servers and have opened the necessary port, its time to install Apache software on both server. To do so we must first connect to each of the webserver via ssh. Then we can now run commands on the terminal of our webservers.

* Connecting to the webserver: To connect to the webserver, click on your instance Id, at the top of the page click on connect.


![Alt text](<Images/Screenshot 2024-02-29 at 22.12.03.png>)

* Next copy the ssh command below:


![Alt text](<Images/Screenshot 2024-02-29 at 22.16.37.png>)

* Open a terminal in your local machine, cd into Downloads folder. Paste the ssh command you copied in the previous step then click on enter and type yes when prompted. You should be connected to a terminal on your instance.


![Alt text](<Images/Screenshot 2024-02-29 at 22.25.25.png>)

* Next install Apache with the command below:

• sudo apt update -y &&  sudo apt install apache2 -y


![Alt text](<Images/Screenshot 2024-02-29 at 22.29.26.png>)


![Alt text](<Images/Screenshot 2024-02-29 at 22.32.05.png>)

* Verify that Apache is running using the command below:

• sudo systemctl status apache2


![Alt text](<Images/Screenshot 2024-02-29 at 22.39.02.png>)

**Step 4:** Configure Apache to server a page showing its public IP:

We will start by configuring **Apache** webserver to serve content on port 8000 instead of its default which is port 80. Then we will create a new **index.html** file. The file will contain code to display the public IP of the EC2 instance. We will then override apache webservers default html file with our file.

* Configuring Apache to Server content on port 8000:

1• Using your text editor (eg vi, nano) open the file /etc/apache2/ports.conf

• sudo vi /etc/apache2/ports.conf 

2• Add a new Listen directive for port 8000: First type **i** to switch the editor to insert mode. Then add the listen directive, Then save your file.


![Alt text](<Images/Screenshot 2024-02-29 at 22.58.48.png>)

3• Next open the file /etc/apache2/sites-available/000-default.conf and change port 80 on the virtualhost to 8000. copy below:

• sudo vi /etc/apache2/sites-available/000-default.conf

4• Close the file by first pressing the **esc** key on your keyboard then command below:

• :wqa!


![Alt text](<Images/Screenshot 2024-03-04 at 17.40.28.png>)

5• Restart apache to load the new configuration using the command below:

• sudo systemctl restart apache2

* Creating our new html file:

1• Open a new **index.html** file with the command below:

•sudo vi index.html

2• Switch vi editor to insert mode and paste the html file below. Before pasting the html file, get the public IP of your EC2 instance from AWS Management Console and replace the placeholder text for IP address in the html file.

*Copy Below code;*

•         <!DOCTYPE html>
        <html>
        <head>
            <title>My EC2 Instance</title>
        </head>
        <body>
            <h1>Welcome to my EC2 instance</h1>
            <p>Public IP: YOUR_PUBLIC_IP</p>
        </body>
        </html>




![Alt text](<Images/Screenshot 2024-03-04 at 18.06.01.png>)

3• Change file ownership of the index.html file with the command below:

• sudo chown www-data:www-data ./index.html

* Overriding the Default html file of Apache Webserver:

1• Replace the default html file with the new html file using the command below:

• sudo cp -f ./index.html /var/www/html/index.html

2• Restart the webserver to load the new configuration using the command below:

• sudo systemctl restart apache2

3• You should find a page on the browser like so:


![Alt text](<Images/Screenshot 2024-03-04 at 17.50.01.png>)

**Step 5:** Configuring Nginx as a Load Balancer

* Provision a new EC2 instance running ubuntu 22.04. Make sure port 80 is open to accept traffic from anywhere. You can refer to **step 1** through **step 2** to refresh your memory.

* Next SSH into the instance. Again refer to **step 3** for a refresh if needded.

* Install Nginx into the instance using the command below:

• sudo apt update -y && sudo apt install nginx -y


![Alt text](<Images/Screenshot 2024-03-04 at 18.35.22.png>)


![Alt text](<Images/Screenshot 2024-03-04 at 18.36.48.png>)

* Verify that Nginx is installed with the command below:

• sudo systemctl status nginx


![Alt text](<Images/Screenshot 2024-03-04 at 18.39.45.png>)

* Open Nginx configuration file with the command below:

• sudo vi /etc/nginx/conf.d/loadbalancer.conf

* Paste the configuration file below to configure nginx to act like a load balancer. A screenshot of an example config file is shown below: Make sure you edit the file and provide necessary information like your server ip address etc.

•         
        upstream backend_servers {

            # your are to replace the public IP and Port to that of your webservers
            server 127.0.0.1:8000; # public IP and port for webserser 1
            server 127.0.0.1:8000; # public IP and port for webserver 2

        }

        server {
            listen 80;
            server_name <your load balancer's public IP addres>; # provide your load balancers public IP address

            location / {
                proxy_pass http://backend_servers;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            }
        }
    



![Alt text](<Images/Screenshot 2024-03-04 at 19.24.11.png>)

**Upstream backend_servers** defines a group of backend servers. The **Server** lines inside the **upstream** block list the addresses and ports of your backend servers.**proxy_pass** inside the **location** block sets up the load balancing,passing the requests to the backend servers. The **proxy_set_header** lines pass necessary headers to the backend servers to correctly handle the requests.

* Test your configuration with the command below:

• sudo nginx -t


![Alt text](<Images/Screenshot 2024-03-04 at 19.32.32.png>)

* If there are no errors, restart Nginx to load the new configuration with the command below:

• sudo systemctl restart nginx

* Paste the public IP address of Nginx load balancer, you should see tghe same webpages served by the webservers.


![Alt text](<Images/Screenshot 2024-03-04 at 19.37.12.png>)