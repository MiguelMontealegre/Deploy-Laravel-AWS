# Deploy Laravel en AWS 

En la carpeta donde se almacena el .pem (maquina local)

`CHMOD 400 MyFirstKP.pem`


### Actualización de paquetes Ubuntu
`sudo apt-get update`  

`sudo apt-get upgrade`  

`sudo apt-get update`  

### Apache2
`sudo apt-get install apache2`  

### PHP 7.4
`sudo apt install php php-cli php-fpm php-json php-common php-mysql php-zip php-gd php-mbstring php-curl php-xml php-pear php-bcmath`  

### Composer
[https://getcomposer.org/download/](https://getcomposer.org/download/)

A continuacion los comandos para instalar composer a la fecha, pero idealmente entrar a la pagina y usar los correspondientes:
  
`php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"`

`sudo mv composer.phar /usr/local/bin/composer`

### Modo reescritura Apache2
`sudo a2enmod rewrite`  


### Configuración Apache2 
`sudo nano /etc/apache2/apache2.conf`  

`User ubuntu`
`Group ubuntu`

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

memory_limit = 2048M

post_max_size = 2048M

upload_max_filesize = 2048M

### Reinicio del servidor Apache2
`sudo service apache2 restart`


### Instalar Redis en el servidor
`sudo apt install redis-server`

`sudo systemctl status redis-server`

`redis-cli ping`



### Instalación proyecto Laravel (crear desde 0)
`composer create-project laravel/laravel nombre_proyecto`  


### Instalación proyecto
`composer update`  
`composer install`

### Generar llave en el proyecto
`php artisan key:generate`


### Archivo .htaccess para proyectos NO dockerizados
`<IfModule mod_rewrite.c>
    <IfModule mod_negotiation.c>
        Options -MultiViews -Indexes
    </IfModule>

    RewriteEngine On

    # Handle Authorization Header
    RewriteCond %{HTTP:Authorization} .
    RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]

    # Redirect Trailing Slashes If Not A Folder...
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteCond %{REQUEST_URI} (.+)/$
    RewriteRule ^ %1 [L,R=301]

    # Handle Front Controller...
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteRule ^ index.php [L]
</IfModule>`




### Ejemplo de como conectarse
`http://54.234.85.213:80/api`



### Video explicativo:
[https://youtu.be/uNjyopVYqHU](https://youtu.be/uNjyopVYqHU)

https://www.youtube.com/watch?v=4SBFz4jG7KU&t=9s

