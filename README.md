# Deployment Ubuntu 

* SSH
* VNC
* Nginx
* NodeJs 
* Git
* PHP 8
* php composer
* MySQL

## Before install 
```
sudo apt-get update
```

## SSH
  
  1- install SSH server in Ubuntu :
```  
sudo apt-get install openssh-server
```  
   2 - to re-enable the service to start up at boot 
```  
sudo systemctl enable ssh
```
   3 - to start the service :
```
 sudo systemctl start ssh
```  
  4  `haythamasalama@192.168.0.1` or ` haytham@hp-pc`
```
ssh user@server-name  
```
 #### to check if ssh service is running :     
```
   sudo systemctl status ssh
```

#### More Info :
```
  https://www.cyberciti.biz/faq/ubuntu-linux-install-openssh-server/
 ```  
     
## VNC

  1- install lightdm :
``` 
sudo apt install lightdm
```  

  2- reboot :
  
```
sudo reboot
```

 3- install x11vnc :
 
```
sudo apt install x11vnc
```
   4
``` 
sudo nano /lib/systemd/system/x11vnc.service
```
   5- Copy and paste these commands and change the password (yourPassword) to strong password
   this password that request when you use vnc viewer  
   ```
    [Unit]
    Description=x11vnc service
    After=display-manager.service network.target syslog.target

    [Service]
    Type=simple
    ExecStart=/usr/bin/x11vnc -forever -display :0 -auth guess -passwd yourPassword
    ExecStop=/usr/bin/killall x11vnc
    Restart=on-failure

    [Install]
    WantedBy=multi-user.target
  ```
 6
```   
sudo systemctl daemon-reload
```   

 7- to re-enable the service to start up at boot :
``` 
sudo systemctl enable x11vnc.service
```

 8- to start the service :
```          
sudo systemctl start x11vnc.service
``` 
 #### check if x11vnc service  is running :
``` 
sudo systemctl status x11vnc.service
``` 
 #### to use vnc viewer on windoes or other operating system : 
```
https://www.realvnc.com/en/connect/download/viewer/
```
![image](https://user-images.githubusercontent.com/37311945/155212175-5048fa1b-0d34-4d23-943f-c955e12f0718.png)
```
https://www.youtube.com/watch?v=3K1hUwxxYek&ab_channel=DavidBombal
```

## Nginx

  1- install nginx :
```
sudo apt install nginx
```
  
 2-  adjusting the Firewall : 
```
sudo ufw allow 'Nginx HTTP'
```

 #### check if nginx service is running    
```
systemctl status nginx
```
  
3- to re-enable the service to start up at boot :
```
sudo systemctl enable nginx
```
Managing the Nginx Process : 
```
sudo systemctl start nginx
sudo systemctl stop  nginx
sudo systemctl restart  nginx
sudo systemctl reload  nginx
```
  #### More Info :
```
https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-20-04#step-1-installing-nginx
```

## NodeJs

  1- install nodejs :
```  
sudo apt install nodejs
```    
 #### check node version and if it install successfully
``` 
node -v 
node –version
``` 
## Git

  1- install Git :
``` 
sudo apt-get install git
``` 
 #### check git version and if it install successfully
```  
git --version
```       
2- to configure your Git `username` and `email` using  :
``` 
 git config --global user.name "Haytham Salama"
 git config --global user.email "haythamasalama@gmail.com"
``` 


## PHP 8

1-  install PPA for PHP 8.1 Add the `ndrej/php` which has `PHP 8.0` package and other required PHP extensions

``` 
sudo apt install software-properties-common
sudo add-apt-repository ppa:ondrej/php
```    
    
2- install php 8 for `nginx` : 
```
sudo apt install php8.0-fpm
```
    
2- install php 8 for `Apache` :
```
sudo apt install php8.0
```    

 #### check if php8 service is running 
``` 
systemctl status php8.0-fpm
```      

3- to Installing PHP extension :

```
sudo apt install php8.0-[extname] 
```

for example to install `MySQL` , `GD` , `intl` , `fileinfo` and `curl` extensions, you would run the following command:
```
sudo apt install php8.0-gd php8.0-curl php8.0-intl php8.0-fileinfo php8.0-mysql
```
     

## php composer

1
``` 
sudo apt install php-cli unzip
``` 

2-
```
  cd ~
  curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
  HASH=`curl -sS https://composer.github.io/installer.sig`
```
3- to install composer globally and install Composer as a system-wide command named composer, under /usr/local/bin:

```
sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
```

 #### check if composer if it install successfully
```
composer
```    
 
  #### More Info :
```
https://www.digitalocean.com/community/tutorials/how-to-install-and-use-composer-on-ubuntu-20-04#step-1-installing-php-and-additional-dependencies
```   

## MySQL

1- install mysql : 
```
sudo apt install mysql-server
```   
2- Securing MySQL : 
```
sudo mysql_secure_installation
```    
3- output for ``mysql_secure_installation`` : 

```
$ Press y|Y for Yes, any other key for No:  Y 
LOW    Length >= 8
MEDIUM Length >= 8, numeric, mixed case, and special characters
STRONG Length >= 8, numeric, mixed case, special characters and dictionary  file
Please enter 0 = LOW, 1 = MEDIUM and 2 = STRONG:  2

Please set the password for root here.
$ New password:
$ Re-enter new password:

Estimated strength of the password: 100
$ Do you wish to continue with the password provided?(Press y|Y for Yes, any other key for No) : Y
```

    
4- Creating a Dedicated MySQL User and Granting Privileges :  

 mysql :
 
```
sudo mysql
```    

2- creat any user :

```mysql
CREATE USER 'username'@'host' IDENTIFIED WITH authentication_plugin BY 'STRONG_PASSWORD_HERE';
FLUSH PRIVILEGES;
``` 

3-  root user : 

```mysql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'STRONG_PASSWORD_HERE';
FLUSH PRIVILEGES;
``` 
    
4- to re-enable the service to start up at boot :

```
  sudo systemctl enable mysql
``` 
  

 #### check if mysql service  is running :
     sudo systemctl status mysql
