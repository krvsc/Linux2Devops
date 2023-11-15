# Azure LAMP Stack E-commerce App Deployment

## Introduction
This is a sample e-commerce application built for learning purposes.

The deployment instructions provided here are specific to an Azure cloud server running Ubuntu Linux.

## Deploy Pre-Requisites

>**Create an Azure Virtual Machine**

1. Log in to the Azure portal.
2. Navigate to the Virtual Machines section and create a new Ubuntu VM.
3. Follow the on-screen instructions to configure the VM.

>**Connect to the Azure VM**

Connect to the Azure VM using SSH:
``` 
#bash

ssh azureuser@<your-vm-ip-address>
```
**NOTE:** You may also refer to connect blade in the sidebar of azure vm there you will find everything what you need.

>**Update the System**
```
#bash

sudo apt update
sudo apt upgrade -y
```

## Deploy and Configure Database

>**Install MariaDB**
```
#bash

sudo apt install -y mariadb-server
sudo systemctl start mariadb
sudo systemctl enable mariadb
```
>**Configure MariaDB**
```
#bash

sudo mysql
```

There are a couple of points you may want to consider before configurartion of mysql database:

>>Security Best Practices:

It's generally a good practice to provide only the necessary privileges to the user. Instead of granting all privileges on *.*, you might want to specify the exact privileges needed for the ecomdb. 

**Example:** If the user only needs to perform SELECT, INSERT, UPDATE, and DELETE operations, you can grant those specific privileges:
```
#sql

GRANT SELECT, INSERT, UPDATE, DELETE ON ecomdb.* TO 'ecomuser'@'localhost';
```

