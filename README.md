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

 ``ssh 
  sudo apt-get install openssh-server
  ``

## SSH
  
  Install SSH server in Ubuntu :
  
  
  1- ``ssh 
  sudo apt-get install openssh-server
  ``
  
  2- ``ssh 
sudo systemctl enable ssh
  ``

 3- ``ssh 
sudo systemctl start ssh
  ``
  
   4- ``ssh 
  ssh user@server-name  
  ``
  
    For example  : haythamasalama@192.168.0.1 or  haytham@hp-pc
    
 #### Check if ssh service is running :     

   ``ssh 
 sudo systemctl status ssh
  ``
  
  #### More Info :
    https://www.cyberciti.biz/faq/ubuntu-linux-install-openssh-server/
     
     
## VNC

  1- ``ssh 
sudo apt install lightdm
  ``
  
  2- ``ssh 
sudo reboot
  ``

 3- ``ssh 
sudo apt install x11vnc
  ``
  
   4- ``ssh 
sudo nano /lib/systemd/system/x11vnc.service
  ``

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
  
 6- ``ssh 
systemctl daemon-reload
``

 7- ``ssh 
systemctl enable x11vnc.service
``

 8- ``ssh 
systemctl start x11vnc.service
``

 #### check if ssh service is running    

   ``ssh 
systemctl status x11vnc.service
  ``

 #### To use vnc viewer on windoes or other operating system : 

    https://www.realvnc.com/en/connect/download/viewer/

![image](https://user-images.githubusercontent.com/37311945/155212175-5048fa1b-0d34-4d23-943f-c955e12f0718.png)

    https://www.youtube.com/watch?v=3K1hUwxxYek&ab_channel=DavidBombal


## Nginx


## NodeJs


## Git



## PHP 8



## php composer



## MySQL


