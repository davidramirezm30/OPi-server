# OPi-server

This tutorial is to install Apache, Mysql, Php, Git and Symfony in the Orange Pi.

## Apache
    $ sudo apt-get update && sudo apt-get upgrade -y
    $ sudo apt-get install apache2 -y
    
## MySQL
    $ sudo apt-get install mysql-server mysql-client -y
    
    $ sudo mysql_secure_installation -y
    
    $ sudo mysql -u root -p
    
    $ CREATE USER 'phpmyadminuser'@'localhost' IDENTIFIED BY 'password';
    
    $ GRANT ALL PRIVILEGES ON *.* TO 'phpmyadminuser'@'localhost' WITH GRANT OPTION;

## PHP
    $ sudo apt-get install php libapache2-mod-php libapache2-mod-perl2 php php-cli php-common php-curl php-dev php-gd php-imap php-ldap php-mysql php-odbc php-pear php-zip php-xml phpmyadmin php-mbstring php-gettext -y
    
    $ sudo phpenmod mbstring
    $ sudo systemctl restart apache2
    
    $ sudo chown www-data:www-data /var/www/
    $ sudo chmod 775 /var/www/
    $ sudo usermod -a -G www-data *nombre-de-usuario*
    
## Git
    $ sudo apt-get install git
    
## Composer & Symfony
    $ sudo apt-get install composer
    
Download de Symfony app in /var/www/ and changing the current name of the folder to html.

    $ mv /var/www/current-name /var/www/html

    $ cd /var/www/html
    
    $ composer install
    
    $ php bin/console avanzu:admin:initialize
    
    $ chmod -R 777 *

    $ composer update
If you get the error message proc_open(): fork failed - Cannot allocate memory try this:

    $ /bin/dd if=/dev/zero of=/var/swap.1 bs=1M count=1024
    $ /sbin/mkswap /var/swap.1
    $ /sbin/swapon /var/swap.1
