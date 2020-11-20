# Instalace MSSQL na Linux server
| OS                       | Container | Web server | PHP version | Worked in 2020 |
|--------------------------|:---------:|:----------:|:-----------:|:--------------:|
| Ubuntu 20.04 Focal Fossa | LXC       | Nginx      | php7.4-fpm  |        ✅       |
| Debian 10 Buster         | KVM       | Nginx      | php7.3-fpm  |        ❌       |
|                          |           |            |             |                |
|                          |           |            |             |                |

## Ubuntu 20.04 Focal Fossa
1. `sudo su` (root práva jsou vyžadována pro instalaci)
1. `apt-get update`
1. `apt-get upgrade`
1. `curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -`
1. `curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list | sudo tee /etc/apt/sources.list.d/mssql-server-2017.list` nebo novější 
`sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/18.04/mssql-server-2019.list)"`
1. `sudo apt-get update`
1. `sudo apt-get install mssql-server`
1. `sudo /opt/mssql/bin/mssql-conf setup`
1. Setup provede souhlasem s podmínkami, nastavením hesla uživatele "SA" (system administrator) a vybráním edice (**Express** je zdarma).
1. `curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list` nebo novější `curl https://packages.microsoft.com/config/ubuntu/18.04/prod.list > /etc/apt/sources.list.d/mssql-release.list` (pozor na kompatibilitu)
1. `sudo apt install php-pear php-dev`
1. `sudo ACCEPT_EULA=Y apt-get install msodbcsql17`
1. `sudo ACCEPT_EULA=Y apt-get install mssql-tools`
1. `echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile`
1. `echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc`
1. `source ~/.bashrc`
1. `sudo apt-get install unixodbc-dev`
1. `sudo pecl install sqlsrv` (pozn. PECL je součást php-pear)
1. `sudo pecl install pdo_sqlsrv`
1. `printf "; priority=20\nextension=sqlsrv.so\n" > /etc/php/7.4/mods-available/sqlsrv.ini`
1. `printf "; priority=30\nextension=pdo_sqlsrv.so\n" > /etc/php/7.4/mods-available/pdo_sqlsrv.ini`
1. `sudo phpenmod -v 7.4 sqlsrv pdo_sqlsrv` (lze přeskočit)
1. `sudo service php7.4-fpm restart`
