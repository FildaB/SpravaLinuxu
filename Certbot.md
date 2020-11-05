# Získání certifikátu Let's Encrypt přes Certbot

## Linux
### Debian, Ubuntu
#### Nginx
1. `sudo apt-get install certbot python3-certbot-nginx`
1. `sudo certbot --nginx -d ###DOMÉNA###`

#### Apache
1. `sudo apt-get install certbot python3-certbot-apache`
1. `sudo certbot --apache -d ###DOMÉNA###`

### Fedora
#### Nginx
1. `dnf install certbot python3-certbot-nginx`

#### Apache
1. `dnf install certbot python3-certbot-apache`

### Alpine Linux
Jen vygeneruje certifikát. Pro Alpine bez dockeru je zázrak, že vůbec něco.

1. `apk add netcat-openbsd bc curl wget git bash openssl`
1. `apk add libressl`
1. `cd /tmp/` nebo `cd /root/` (záleží, co hodí chybu)
1. `git clone https://github.com/Neilpang/acme.sh.git`
1. `cd acme.sh/`
1. `sudo -i` (lze přeskočit)
1. `./acme.sh --install`
1. `source ~/.bashrc` / `exec bash` / `bash` / `source /etc/bash.bashrc` / `reboot` (některé můžou hodit chybu)
1. `acme.sh`

## Windows Server
1. Stáhnout aplikaci z [win-acme.com](https://www.win-acme.com/) a nainstalovat
1. Po otevření se zobrazí interaktivní menu.
