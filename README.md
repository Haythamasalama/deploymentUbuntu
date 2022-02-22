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


    sudo apt-get install openssh-server


## SSH
  
  1- install SSH server in Ubuntu :
  
    sudo apt-get install openssh-server
  
   2 - to re-enable the service to start up at boot 
  
    sudo systemctl enable ssh

   3 - to start the service :

     sudo systemctl start ssh
  
  4  haythamasalama@192.168.0.1 or  haytham@hp-pc
  
    ssh user@server-name  
  
 #### to check if ssh service is running :     

    sudo systemctl status ssh
  
  #### More Info :
    https://www.cyberciti.biz/faq/ubuntu-linux-install-openssh-server/
     
     
## VNC

  1- install lightdm :
   
    sudo apt install lightdm
  
  2- reboot :

    sudo reboot

 3- install x11vnc :

    sudo apt install x11vnc
  
   4
  
    sudo nano /lib/systemd/system/x11vnc.service

   5- Copy and paste these commands and change the password (yourPassword) to strong password
   this password that request when you use vnc viewer  
   
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
  
 6
   
    sudo systemctl daemon-reload
   

 7- to re-enable the service to start up at boot :
 
    sudo systemctl enable x11vnc.service

 8- to re-enable the service to start up at boot 
   
    sudo systemctl start x11vnc.service

 #### check if ssh service is running :

    sudo systemctl status x11vnc.service

 #### to use vnc viewer on windoes or other operating system : 

    https://www.realvnc.com/en/connect/download/viewer/

![image](https://user-images.githubusercontent.com/37311945/155212175-5048fa1b-0d34-4d23-943f-c955e12f0718.png)

    https://www.youtube.com/watch?v=3K1hUwxxYek&ab_channel=DavidBombal


## Nginx

  1- install nginx :

    sudo apt install nginx

  
 2-  adjusting the Firewall : 

    sudo ufw allow 'Nginx HTTP'


 #### check if ssh service is running    
    systemctl status nginx

  
3- to re-enable the service to start up at boot :

    sudo systemctl enable nginx

Managing the Nginx Process : 

    sudo systemctl start nginx
    sudo systemctl stop  nginx
    sudo systemctl restart  nginx
    sudo systemctl reload  nginx



## NodeJs


## Git



## PHP 8



## php composer



## MySQL


