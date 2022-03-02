# Create-server-for-Symfony-deployment

- [1 - Console SSH  ](#1---Console-SSH) 
- [2 - Update OS ](#2---Update-OS) 
- [3 - Install Apache server ](#3---Install-Apache-server) 
- [4 - Install PHP 7.4 ](#3---Install-PHP-7.4) 
- [5 - Install MYSQL](#3---Install-MYSQL)




## 1.  Console SSH 

- open terminal :

        ssh root@<IP_SERVER>


## 2.  Update OS

- in root@localhost:~# 


         sudo apt-get update
         
         sudo apt-get upgrade
         
         sudo apt-get dist-upgrade


## 3. Install Apache server 

- Install Apache2


        sudo apt-get install apache2 

   
- Rewrite URL

        sudo a2enmod rewrite


- Restart Apache2

    
        sudo service apache2 restart


 ## 4. Install PHP 7.4

- Update
        
        sudo apt-get update

- PHP

        sudo apt-get install php7.4 php7.4-common php7.4-cli php7.4-mysql libapache2-mod-php7.4 php7.4-mbstring php7.4-json php7.4

## 5. Install MYSQL
   
        sudo apt-get install mysql-server

- Restart Server

      apache2 restart

- Launch MYSQL 

        sudo mysql -u root 








