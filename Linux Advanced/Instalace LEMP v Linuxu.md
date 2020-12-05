# Instalace LEMP v Linuxu
| OS                       | Container | Web server | PHP version |  RAM   | Worked in 2020 |
|--------------------------|:---------:|:----------:|:-----------:|:------:|:--------------:|
| Ubuntu 20.04 Focal Fossa | LXC       | Nginx      | php7.4-fpm  |  2 GB  |       ✅       |
| Debian 10 Buster         | LXC       | Nginx      | php7.4-fpm  |  2 GB  |       ✅       |
| Debian 10 Buster         | KVM       | Nginx      | php7.3-fpm  |  2 GB  |       ✅       |
| Debian 10 Buster         | KVM       | Nginx      | php7.3-fpm  | 512 MB |       ⚠       |
| Debian 9 Stretch         | KVM       | Nginx      | php7.3-fpm  | 512 MB |       ⚠       |

⚠ U nižší RAM občas při velké zátěži spadla MariaDB.

**LEMP** - Linux, Nginx, MySQL, php

## Debian, Ubuntu
### Nginx
1. `apt install nginx`
1. `ufw allow Nginx HTTP` - *lze přeskočit*

### php
1. `apt install php-fpm`

### MySQL
1. `apt-get install mariadb-server mariadb-client`
1. `mariadb_secure_installation`
1. Provede různým nastavením zabezpečení. Může požadovat heslo uživatele root.

### První doména
1. Zjistěte php-socket `cat /etc/php/$(php -r "echo PHP_VERSION;" | grep --only-matching --perl-regexp "7.\d+")/fpm/pool.d/www.conf | grep 'listen ='`
1. `nano /etc/nginx/sites-enabled/<DOMÉNA>.conf`

```
server {
	listen 80;
	listen [::]:80;
	
	root /var/www/html;
	index index.php index.html index.htm;

	server_name <DOMÉNA>
	
	location / {
		try_files $uri $uri/ =404;
	}
	
	location ~ \\.php$ {
		include snippets/fastcgi-php.conf;
		fastcgi_pass unix:<NALEZENÝ_PHP_SOCKET>;
	}
}
```

1. Uložit.
1. `service nginx restart`

### Co dál
1. Vložit do `/var/www/html` (pro tuto doménu root adresář) nějaký obsah.
1. Nastavit DNS záznamy, tak aby uživatele dovedli na server (obvykle je potřeba do záznamu `A` zadat IP serveru, `AAAA` pro IPv6)
1. Zajistit SSL certifikát (umožní důvěryhodné HTTPS)
1. *Číst log ke každé snídani*
