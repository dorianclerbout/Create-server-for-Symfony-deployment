# Create & Config & Secure VPS Server for symfony 6 deployment
- [1 - Create SSH key  ](#1---Create-SSH-key) 
- [2 - Server Security ](#2---Service-Security) 
- [3 - Server Locale ](#3---Serveur-Locale)
- [4 - Firewall ](#4---Firewall) 
- [5 - Secure shared memory ](#5---Secure-shared-memory)
- [6 - Install Fail2Ban](#6---Install-Fail2Ban) 
- [7 - Update Os](#7---Update-Os)
- [8 - Install Apache server ](#8---Install-Apache-server )
- [9 - Install MYSQL](#9---Install-MYSQL)
- [10 - Install Symfony](#10---Install-Symfony)

# 1.  Create SSH key

- Open terminal :

        ssh-keygen -t rsa -b 4096 -o -a 100

- Copy SSH key inside server :
        
        ssh-copy-id -i ~/.ssh/id_rsa.pub user@host


 
# 2.  Server Security
 1. Open terminal :

        ssh root@<IP_SERVER>

- If you are not create SSH key , enter server root password

## 2. Update Root Password 

        passwd root

## 3. Create New User

        adduser user_name

## 4. Then give administrator rights to the new user.

        usermod -aG sudo user_name
- Use sudo for root command

## 5. Connect ssh key to new user

- Open new terminal

        ssh-copy-id user_name@<IP_SERVER>

## 6. Change the default SSH service listening port for security

        
- Restart SSH

        /etc/init.d/ssh restart

## 7. Disable access to server via root user

       sudo nano /etc/ssh/sshd_config

- Then locate the following line: 

        PermitRootLogin and write No

- Restart SSh

        sudo /etc/init.d/ssh restart

# 3. Server Locale

        sudo dpkg-reconfigure locales

        sudo nano /etc/default/locale



# 4. Firewall

- And to release only incoming connections from the `new_port_ssh`

        sudo ufw allow nouveau_port_ssh/tcp

- Activate firewall

        sudo ufw enable

- To display the status and rules of the firewall.

        sudo ufw status verbose

- To delete a rule.

        sudo ufw delete allow ssh



 # 5. Secure shared memory

 - To modify  `/etc/fstab `
  
        sudo nano /etc/fstab

- At the end of the file

        tmpfs   /run/shm    tmpfs   defaults,noexec,nosuid  0   0

# 6. Install Fail2Ban
        
        sudo apt-get install fail2ban

- Save config : 

        sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.conf.backup

- Update Configuration

        sudo nano /etc/fail2ban/jail.conf


# 7.  Update OS

- In root@localhost:~# 


         sudo apt-get update
         
         sudo apt-get upgrade
         
         sudo apt-get dist-upgrade

 

# 8. Install Apache server 

- Install Apache2


        sudo apt-get install apache2 

- Edit Apache config

        sudo nano /etc/apache2/apache2.conf
   
- At the end of this file, add the ServerName
 
        ServerName 192.89.11.121

 - Verify syntax :

        sudo apache2ctl configtest

- Restart Apache2

    
        sudo service apache2 restart

- Release incoming connections from the HTTP port

        sudo ufw allow 80/tcp


 # 9. Install PHP 7.4

- Update
        
        sudo apt-get update

- Install PHP

        sudo apt-get install php7.4 php7.4-common php7.4-cli php7.4-mysql libapache2-mod-php7.4 php7.4-mbstring php7.4-json php7.4

- Create `info.php ` for test

        sudo nano /var/www/html/info.php

- Add 

         <?php phpinfo(); ?>

- Modify  `date.timezone` inside php.ini

        sudo nano /etc/php/7.4/cli/php.ini

- To test date.timezone

        timedatectl status

- Configure date.timezone

        sudo timedatectl set-timezone Europe/Paris

# 10. Install MYSQL
   
        sudo apt-get install mysql-server

        &&

        mysql_secure_installation

- Restart Server

       sudo apache2 restart

# 10. Install Symfony

        sudo apt-get install acl git php7.4-curl php7.4-zip php7.4-xml php7. 4-mbstring php7.4-gd php7.4-common

- Composer Install

        sudo curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer







