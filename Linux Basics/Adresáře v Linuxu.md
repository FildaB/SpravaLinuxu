# Adresáře v Linuxu
Kořenem je `/`, obdobně jako `C:\` u Windows.\
Zatímco u Windows se používá obrácené lomítko (`\`), u Linuxu lze použít jedině běžné lomítko (`/`).

## Základní struktura
### Běžné adresáře
1. `/etc` - nachází se v něm konfigurační soubory systému a aplikací (např. nginx, apache2, php)
1. `/home` - domovské adresáře uživatelů (*C:\Users\* ve Windows)
1. `/root` - domovský adresář superuživatele "root"
1. `/var` - důležitý adresář obsahující např. log, cache, CRON, DHCP, DNS, ...; běžně se používá i pro hostování webových stránek
1. `/usr` - obsahuje absolutně všechno - spustitelné soubory, konfigurační soubory, zdrojové kódy, ...

### Systémové adresáře
1. `/boot` - obsahuje boot loader, zavadeče, jádro systému, Kernel (`C:\Windows` ve Windows)
1. `/dev` - abstraktní adresář, který je ale stěžejní pro OS a obsahuje různá další zařízení (klávesnice, myši, IO, harddisky)
1. `/lib` - různé zdrojové kódy systému (`C:\Users\` ve Windows)
1. `/lost+found` - "ztráty a nálezy" souborového systému; obsahuje soubory, které souborový systém (např. FAT32) opravil
1. `/mnt` - připojená zařízení (HDD disky, USB, diskety; ve Windows např. `D:\`, `E:\`, `F:\`)
1. `/proc` - nachází se v něm informace o aktuálně spuštěných procesech
1. `/sys` - systémový adresář (`C:\Windows` ve Windows)
1. `/tmp` - soubor pro odkládání dočasných souborů (např. při stahování; ve Windows se tomu říká `temp`)

### Obdoby Program Files
1. `/bin` - obsahuje aplikace (`C:\Program Files` ve Windows)
1. `/opt` - obsahuje aplikace, které nebyly dodány s Linuxem (`C:\Program Files` ve Windows)
1. `/sbin` - další adresář pro aplikace, ale tentokrát jen pro ty, které může spustit superuživatel "root"

## Podadresáře
### /etc
1. `/etc/crontab` - obsahuje data automatizovaných úloh CRON
1. `/etc/hosts` - obsahuje IP adresy počítačů
1. `/etc/mail` - určeno pro konfigurace mail serveru
1. `/etc/default` - konfigurace základních příkazů (ssh, ufw, useradd)
1. `/etc/shadow` - obsahuje uživatelská hesla
1. `/etc/host.conf` a `/etc/resolv.conf` - soubory konfigurace DNS

### /dev
1. `/dev/null` - "černá díra" v Linuxu; cokoli, co se pošle do `/dev/null` nevratně zmizí *(takový odpadkový koš, který se okamžitě vyveze na skládku a okamžitě spálí)*
1. `/dev/zero` - obdoba `/dev/null`; když se čte, vrací nulu
1. `/dev/random` - generuje náhodná data
1. `/dev/urandom` - generuje náhodná data, jen jiným způsobem než `/dev/random`

### /var
1. `/var/www` - adresář pro hostování webových stránek
1. `/var/log` - nachází se v něm logy (soubory s událostmi) aplikací a systému
1. `/var/named` - soubory pro chod DNS
1. `/var/lib` - soubory vytvářené aplikacemi za běhu; zejména používaná databázemi MySQL a MSSQL nebo DHCP
1. `/var/spool` - fronta systému (fronta automatizovaných úloh CRON, fronta mail serveru, tiskových služeb, ...)

### /usr
1. `/usr/share` - obsahuje sdílené soubory mezi aplikacemi (časové zóny, národní prostředí, fonty, ...)
1. `/usr/include` - hlavičkové soubory v jazyce C
