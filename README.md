# Create-server-for-Symfony-deployment
- [0 - Create SSH key  ](#0---Create-SSH-key) 
- [1 - Console SSH  ](#1---Console-SSH) 
- [2 - Update OS ](#2---Update-OS) 
- [3 - Install Apache server ](#3---Install-Apache-server) 
- [4 - Install PHP 7.4 ](#3---Install-PHP-7.4) 
- [5 - Install MYSQL](#3---Install-MYSQL)

## 0.  Create SSH key

- Open terminal :

        ssh-keygen -t rsa -b 4096 -o -a 100

- Copy SSH key inside server :
        
        ssh-copy-id -i ~/.ssh/id_rsa.pub user@host

## 1.  Console SSH 

- Open terminal :

        ssh root@<IP_SERVER>

 
## 2.  Server Security

1. Open terminal :

        ssh root@<IP_SERVER>

* If you are not create SSH key , enter server root password

2. Update Root Password 

        passwd root

3. Create New User

        adduser user_name

4. Then give administrator rights to the new user.

        usermod -aG sudo user_name

5. Connect ssh key to new user

- Open new terminal

        ssh-copy-id user_name@<IP_SERVER>

6. Change the default SSH service listening port for security
## 3.  Update OS

- In root@localhost:~# 


         sudo apt-get update
         
         sudo apt-get upgrade
         
         sudo apt-get dist-upgrade


## 4. Install Apache server 

- Install Apache2


        sudo apt-get install apache2 

   
- Rewrite URL

        sudo a2enmod rewrite


- Restart Apache2

    
        sudo service apache2 restart


 ## 5. Install PHP 7.4

- Update
        
        sudo apt-get update

- PHP

        sudo apt-get install php7.4 php7.4-common php7.4-cli php7.4-mysql libapache2-mod-php7.4 php7.4-mbstring php7.4-json php7.4

## 6. Install MYSQL
   
        sudo apt-get install mysql-server

- Restart Server

      apache2 restart

- Launch MYSQL 

        sudo mysql -u root 








