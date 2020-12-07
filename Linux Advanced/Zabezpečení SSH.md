# Zabezpečení SSH v Linuxu

## Vygenerování a použití klíče
> :warning: Pokud používáte Fail2ban, **vypněte ho** po dobu testování.

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
