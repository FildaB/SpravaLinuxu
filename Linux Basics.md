# Běžné příkazy v Linuxu
1. **`man` - manuál ke každému příkazu** (`man cd`)
1. [klávesa **TAB**] - dokončí příkaz (a má i další funkce)

## Manipulace se složkami a soubory
1. `cd` - *change directory* - změní složku (`cd /etc/www/`)
1. `cp` - *copy* - kopíruje soubory (`cp /etc/www/stary_soubor.txt /root/zkopirovany_soubor.txt`)
1. `chmod` - *change mode* - změna oprávnění k souboru (`chmod 777 soubor.txt`)
1. `chmod +t` - zakáže úpravu jiným uživatelům, než jeho vlastníkovi, ale nezakáže jim ho otevřít a spustit (`chmod +t soubor.txt`)
1. `chown` - *change owner* - změna vlastníka souboru (`chown root soubor.txt`)
1. `ls` - *list* - ukáže soubory a podsložky (`ls -la`)
1. `mkdir` - *make directory* - vytvoří složku (`mkdir moje_slozka/`)
1. `mv` - *move* - přesouvá soubory (`mv soubor.txt /etc/www/`)
1. `pwd` - *print working directory* - ukáže ve které složce se nacházím (`pwd`)
1. `rmdir` - *remove directory* - smaže složku (`rmdir moje_slozka/`)
1. `rm` - *remove* - smaže soubor (`rm soubor.txt` nebo `rm -R moje_slozka` -R umí smazat i celou složku)
1. `tar` - *tape archiver* - alternativa k zip ve Windows

## Soubory
1. `cat` - *concatenate* - vypisuje obsah souboru (`cat soubor.txt`)
1. `dif` - *difference* - ukáže rozdíli mezi dvěma soubory (`dif soubor1.txt soubor2.txt`)
1. `find` - hledá v rámci jedné složky a v jejich podsložkách (`find /etc/www/ -name soubor`)
1. `grep` - *search globally for lines matching the regular expression, and print them* - hledá v souborech (`grep vyraz soubor.txt`)
1. `head` - zobrazí první řádky souboru (`head soubor.txt`)
1. `locate` - hledá v názvech souborů (`locate -i zkopirovany`)
1. `tail` - zobrazí poslední řádky souboru (`tail soubor.txt`)
1. `touch` - vytváří prázdný soubor (`touch soubor.txt`)

## SuperUser
1. `sudo` - *superuser do* - provádí příkaz jako administrátor

## Správa uživatelů
1. `useradd` - *user add* - přidá uživatele (`useradd uzivatel`)
1. `userdel` - *user delete* - smaže uživatele (`userdel uzivatel`)
1. `id` - zobrazí UID, GID aktuálního uživatele (`id`)
1. `passwd` - *password* - změní heslo (`passwd root`)

## Procesy
1. `kill` - "zabije" (okamžitě ukončí; *slovo okamžitě je však kontroverzní*) proces (`kill 7580` - číslo PID - *process ID*)
1. `top` - ukáže detailní přehled o běžících procesech, včetně zmíněného PID

## Informace o zařízení
1. `df` - *disk free* - informace o volném místě na disku
1. `du` - *disk usage* - informace o využití disku
1. `uname` - *unix name* - název Linuxu

## Ostatní
1. `echo` - výpis textu (`echo "text"`)
1. `history` - historie použitých příkazů - *o důvod víc nedávat hesla přímo do příkazů*
1. `ping` - zjistí odezvu, podobné jako ve Windows
1. `which` - hledá umístění spustitelného souboru, který má spojitost s určitým příkazem (`which mount`, `which ping`, `which apt`)
