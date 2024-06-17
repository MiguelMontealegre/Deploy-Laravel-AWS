# Deploy Laravel 8 en AWS 


### Actualización de paquetes Ubuntu
`sudo apt-get update`  

`sudo apt-get upgrade`  

`sudo apt-get update`  

### Apache2
`sudo apt-get install apache2`  

### PHP 7.4
`sudo apt install php php-cli php-fpm php-json php-common php-mysql php-zip php-gd php-mbstring php-curl php-xml php-pear php-bcmath`  

### Composer
A continuacion los comandos para instalar composer a la fecha, pero idealmente entrar a la pagina y usar los correspondientes:

[https://getcomposer.org/download/](https://getcomposer.org/download/)  
`php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"`

`sudo mv composer.phar /usr/local/bin/composer`

### Modo reescritura Apache2
`sudo a2enmod rewrite`  


### Configuración Apache2 
`sudo nano /etc/apache2/apache2.conf`  

`<Directory /home/ubuntu/>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
</Directory>
`  

###  Sitio por defecto Apache2  
`sudo nano /etc/apache2/sites-enabled/000-default.conf`  

### Configuración php.ini
`sudo nano /etc/php/7.4/apache2/php.ini`

### Reinicio del servidor Apache2
`sudo service apache2 restart`

### Instalación proyecto Laravel 8
`composer create-project laravel/laravel nombre_proyecto`  

### Video explicativo:
[https://youtu.be/uNjyopVYqHU](https://youtu.be/uNjyopVYqHU)

