# Instalace MSSQL na Linux server
Postup zkoušen na LXC s Ubuntu 20.04 Focal Fossa (2 GB RAM a 1 vCPU). Server v následující konfiguraci: PHP7.4 a NGINX.

## Ubuntu 20.04 Focal Fossa
1. `apt-get update`
1. `apt-get upgrade`
1. `wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -`
1. `sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/18.04/mssql-server-2019.list)"`
1. `sudo apt-get update`
1. `sudo apt-get install mssql-server`
1. `sudo /opt/mssql/bin/mssql-conf setup`
1. Setup provede souhlasem s podmínkami, nastavením hesla uživatele "SA" (system administrator) a vybráním edice (**Express** je zdarma).
1. `sudo apt install php-pear php-dev`
1. `sudo ACCEPT_EULA=Y apt -y install msodbcsql17 mssql-tools`
1. `sudo apt -y install unixodbc-dev`
1. `sudo apt -y install gcc g++ make autoconf libc-dev pkg-config`
1. `sudo pecl install sqlsrv` (pozn. PECL je součást php-pear)
1. `sudo pecl install pdo_sqlsrv`
1. `sudo bash -c "echo extension=sqlsrv.so > /etc/php/7.4/fpm/conf.d/sqlsrv.ini"`
1. `sudo bash -c "echo extension=pdo_sqlsrv.so > /etc/php/7.4/fpm/conf.d/sqlsrv.ini"`
1. `sudo phpenmod -v 7.4 sqlsrv pdo_sqlsrv` (lze přeskočit)
1. `sudo service php7.4-fpm restart`
