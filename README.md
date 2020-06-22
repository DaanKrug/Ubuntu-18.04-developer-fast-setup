# Ubuntu-18.04-developer-fast-setup - Last update on: 22/06/2020
Change Theme, Tunning Ubuntu and Comands for Install: Apache2, PHP 7.2, Elixir, Maria DB, NodeJs + NPM

This is a Step by Step for install and configure some programs. This is a compilation 
of various websites. The origin sites are above in right side
of each topic, there are the respectives descriptions.
Feel free to use this by yourself responsability. This is intended for use in development
machines, don't put it directly in production whitout test and required adjusts.


======================================================================================

 Install Apache2 - https://thishosting.rocks/how-to-install-optimize-apache-ubuntu/

======================================================================================

sudo apt update

sudo apt upgrade

sudo apt install apache2 apache2-utils

sudo systemctl status apache2

sudo apachectl -v

sudo ufw allow 'Apache Full'

sudo wget https://dl-ssl.google.com/dl/linux/direct/mod-pagespeed-stable_current_amd64.deb

sudo dpkg -i mod-pagespeed-stable_current_amd64.deb 

sudo apt -f install

sudo wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | sudo apt-key add -

sudo systemctl restart apache2

sudo systemctl reload apache2

sudo a2enmod rewrite

sudo a2enmod allowmethods

sudo systemctl restart apache2

sudo apt install curl

sudo apt install net-tools

sudo su

curl -sL https://raw.githubusercontent.com/richardforth/apache2buddy/master/apache2buddy.pl | perl

exit

sudo apt update

sudo apt upgrade

sudo gedit /etc/apache2/apache2.conf

   add the following, (after <Directory /var/www> section):

   <Directory /var/www/html>

      Options Indexes FollowSymLinks

      AllowOverride All

      AllowMethods OPTIONS HEAD GET POST PUT PATCH DELETE

      Require all granted

   </Directory>

sudo systemctl restart apache2

======================================================================================

 Install Maria DB - https://thishosting.rocks/install-mysql-mariadb-ubuntu/

======================================================================================

sudo apt install software-properties-common

sudo apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xF1656F24C74CD1D8

sudo add-apt-repository 'deb [arch=amd64,arm64,ppc64el] http://mirror.lstn.net/mariadb/repo/10.4/
ubuntu bionic main'

sudo apt update

sudo apt install mariadb-server

sudo mysql_secure_installation


======================================================================================

 Install PHP 7.2 - https://thishosting.rocks/install-php-on-ubuntu/

======================================================================================

sudo apt update

sudo apt upgrade

sudo apt install software-properties-common

sudo apt install php php7.2

sudo apt install php-pear php7.2-curl php7.2-gd php7.2-mbstring php7.2-zip php7.2-mysql php7.2-xml

sudo systemctl restart apache2


=====================================================================================

 Install Elixir - https://elixir-lang.org/install.html

=====================================================================================

sudo apt update

sudo apt upgrade

sudo wget https://packages.erlang-solutions.com/erlang-solutions_2.0_all.deb

sudo dpkg -i erlang-solutions_2.0_all.deb

sudo apt update

sudo apt upgrade

sudo apt install esl-erlang

sudo apt install elixir

elixir --version


=====================================================================================

 Install NodeJs/NPM - https://www.hostinger.com.br/tutoriais/instalar-node-js-ubuntu/

=====================================================================================

sudo apt update

sudo apt upgrade

sudo apt install nodejs

sudo apt install npm

sudo npm install -g @angular/cli

sudo npm cache clean -f

sudo npm install -g n

sudo n stable

=====================================================================================

 Install GNOME Tweaks

=====================================================================================

Go to ubuntu software and search "GNOME Tweaks". Install.

Launch and adjust settings as you need.


=====================================================================================

 Instal the Theme: Flat-Remix - https://www.youtube.com/watch?v=epiyExCyb2s

=====================================================================================

sudo apt install git

sudo mkdir Themes

sudo chmod 777 Themes

cd Themes

git clone https://github.com/daniruiz/flat-remix

git clone https://github.com/daniruiz/flat-remix-gtk

mkdir -p ~/.icons

mkdir -p ~/.themes

cp -r flat-remix/Flat-Remix* ~/.icons/

cp -r flat-remix-gtk/Flat-Remix-GTK* ~/.themes/

sudo apt install fonts-hack-ttf -y

use "GNOME Tweaks" to apply the theme and font that was installed. 


=====================================================================================

 Tunning / Adjusts

=====================================================================================

sudo sed -i s/NoDisplay=true/NoDisplay=false/g /etc/xdg/autostart/*.desktop

  Open the "startup applications" and unmark the undesired/unnecessary applications. 
  Take care.

sudo sysctl vm.swappiness=10

  Test if this configuration works well. Dont make this if you have low RAM.
  Case this works for you, use the following commands above. Otherwise only 
  restart the system to back the "vm.swappiness" value to default.

  sudo gedit /etc/sysctl.conf

  add "vm.swappiness=10" on end

  sudo reboot

  to confirm that was adjusted: cat /proc/sys/vm/swappiness


To solve problems whit screen (Leg/Screen Blocking sometimes) - Intel Processors

  Backup grub initialization file:
  cp /etc/default/grub /etc/default/grub.bkp

  Change the line: GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash”
  to: GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash intel_idle.max_cstate=1” 
  close the file.

  Update the grub initialization:
  sudo update-grub

  Then restart system to take new configuration working.


======================================================================================

Install Eclipse IDE - 
https://askubuntu.com/questions/1031171/eclipse-doesnt-start-on-ubuntu-18-04

======================================================================================
  
sudo apt install default-jre

sudo snap install --classic eclipse  

sudo chmod 777 /var/www/html

run Eclipse Ide, then choice "/var/www/html" as eclipse workspace, 

then you can code PHP and other apache applications and the changes already visible when access http://localhost/app-name. 

Go to window -> preferences -> General -> Appearance, adjust 
   the theme, font and colors, according whit ubuntu theme that are applied.
   

======================================================================================

Install PhpMyAdmin as MariaDB client - https://www.phpmyadmin.net/

======================================================================================

download from https://www.phpmyadmin.net/

copy the .zip file to "/var/www/html"

sudo unzip filezip.zip 

sudo mv filezip newName

Access http://localhost/newName

