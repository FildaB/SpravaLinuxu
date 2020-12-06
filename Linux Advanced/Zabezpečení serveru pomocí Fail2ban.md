# Zabezpečení serveru pomocí démona Fail2ban
✅ Zabezpečí SSH na fyzickém serveru a virtuálních serverech běžících na KVM, Hyper-V, ...

**⛔ Není vhodný pro virtuální servery běžících v LXC/LXD, OpenVZ kontejnerech.**

## Debian 8, 9, 10
1. `apt install fail2ban`
1. `cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local`
1. `nano /etc/fail2ban/jail.conf`
1. Projít si celý `[DEFAULT]` a nakonfigurovat jail `[sshd]` (`maxretry = 3`, `enabled = true`), pro přehled je níže tabulka s časy převedenými do sekund
1. `service fail2ban restart`

## Převody času
|             | 10 minut | 1 hodina   | 12 hodin   | 24 hodin  | 1 týden | 1 měsíc | 1 rok    | 10 let    |
|-------------|----------|------------|------------|-----------|---------|---------|----------|-----------|
| V sekundách | 600      | 3600       | 43200      | 86400     | 604800  | 2629743 | 31556926 | 315569260 |

## Fail2ban-client
1. `fail2ban-client status [JAIL]` - vrátí podrobné informace o jailu, vč. blokovaných IP adres
1. `fail2ban-client set [JAIL] unbanip [IP]` - odblokuje IP adresu v určitém jailu
1. `fail2ban-client unban --all` - amnestie na serveru
