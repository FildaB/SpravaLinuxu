# Zabezpečení SSH v Linuxu (Debian, Ubuntu)
**Co určitě udělat na každém serveru:**
1. Změnit port
2. Zakázat přihlášení pro uživatele root

## Konfigurace `sshd_config`
1. `nano /etc/ssh/sshd_config` (popř. jiný editor)
Tip: k vyhledávání použijte `CTRL+W`, zadejte hledaný výraz a dejte `ENTER`

Jakmile je všechno dokončeno:
1. `CTRL+X`, `Y`, `ENTER`
2. `service ssh restart`
3. `CTRL+D`
4. Přihlaste se do SSH znovu

### Změna portu
> :warning: Špatný výběr čísla portu může způsobit potíže. Před výběrem portu si ověřte, že ho nebude používat jiná aplikace.

1. Najděte `Port`
2. Číslo za `Port` změňte (např. `Port 22000`)

### Zakázání přihlášení pro uživatele root

1. Najděte `PermitRootLogin`
2. Změňte na `PermitRootLogin no` (pro zakázání `no`; pro povolení `yes`; pro povolení přihlášení pouze pomocí klíče `prohibit-password`)

### Zobrazení upozornění při přihlášení

1. Najděte `Banner`
1. `Banner /etc/banner` znamená, že při přihlášení se zobrazí text v souboru `/etc/banner`

> **K čemu to je?** Můžete zobrazit například právní upozornění pro toho, kdo se bude přihlašovat.

### Povolování a zakazování pro uživatele/skupiny
#### Povolit SSH pro konkrétní uživatele
1. Najděte nebo přidejte `AllowUsers`
1. Vyjmenujte je a oddělte mezerou `AllowUsers Uzivatel1 Uzivatel2 Uzivatel3`

#### Povolit SSH pro konkrétní skupiny
1. Najděte nebo přidejte `AllowGroups`
1. Vyjmenujte je a oddělte mezerou `AllowGroups Skupina1 Skupina2`

#### Zakázat SSH pro konkrétní uživatele
1. Najděte nebo přidejte `DenyUsers`
1. Vyjmenujte je a oddělte mezerou `DenyUsers Uzivatel1 Uzivatel2 Uzivatel3`

#### Zakázat SSH pro konkrétní skupiny
1. Najděte nebo přidejte `DenyGroups`
1. Vyjmenujte je a oddělte mezerou `DenyGroups Skupina1 Skupina2`

### Maximální čas na přihlášení
1. Najděte `LoginGraceTime`
1. Změňte na `LoginGraceTime 30s`

> **K čemu to je?** Uživatel bude mít na úspěšné přihlášení tolik času, kolik `LoginGraceTime` uvádí.

## Vygenerování a použití klíče
> :warning: Pokud používáte Fail2ban nebo firewall, **vypněte ho** po dobu testování.

### Debian (server), Windows (klient)
**Windows**:
1. `ssh-keygen`
1. Na první otázku defaultně ENTER, je vhodné nastavit i passphrase (heslo ke klíči)
1. `ssh UZIVATEL_NA_SERVERU@IP_SERVERU "umask 077; test -d .ssh || mkdir .ssh ; cat >> .ssh/authorized_keys || exit 1" < "umask 077; test -d .ssh || mkdir .ssh ; cat >> .ssh/authorized_keys || exit 1" < C:\Users\UZIVATEL_VE_WINDOWS\.ssh\id_rsa.pub`
1. Zadejte heslo do SSH.

**Debian**:
1. `nano /etc/ssh/sshd_config`
1. Nastavte `AuthenticationMethods publickey,password` (např. v tomto případě se bude vyžadovat klíč i heslo)
1. Zakažte `#PasswordAuthentication yes`
1. `service ssh restart`
