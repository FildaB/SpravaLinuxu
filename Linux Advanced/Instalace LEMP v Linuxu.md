# Instalace LEMP v Linuxu
**LEMP** - Linux, Nginx, MySQL, php

## Nginx
1. `apt install nginx`
1. `ufw allow Nginx HTTP` - *lze přeskočit*

## php
1. `apt install php-fpm`

## MySQL
1. `apt-get install mariadb-server mariadb-client`
1. `mariadb_secure_installation`
1. Provede různým nastavením zabezpečení. Může požadovat heslo uživatele root.

## První doména
1. Zjistěte php-socket `cat /etc/php/$(php -r "echo PHP_VERSION;" | grep --only-matching --perl-regexp "7.\d+")/fpm/pool.d/www.conf | grep 'listen ='`
1. `nano /etc/nginx/sites-enabled/<DOMÉNA>.conf`

```
server {
  listen 80;
  listen [::]:80;
  
  root /var/www/html;
	index index.php index.htm index.html default.php default.htm default.html;

  server_name <DOMÉNA>
		
  location / {
	  try_files $uri $uri/ =404;
	}
    
  location ~ \\.php$ {
    include snippets/fastcgi-php.conf;
    fastcgi_pass unix:<NALEZENY_PHP_SOCKET>;
  }
}
```

1. Uložit.
1. `service nginx restart`
