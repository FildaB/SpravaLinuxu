# Instalace Mailcow: dockerized
| OS                       | Container | CPU         |  RAM   | Worked in 2020 | Worked in 2021 |
|--------------------------|:---------:|:-----------:|:------:|:--------------:|:--------------:|
| Debian 10 Buster         | KVM       | 2 vCPU      | 2 GB   |       ✅      |       ✅       |
| Debian 10 Buster         | KVM       | 1 vCPU      | 2 GB   |       ✅      |                |
| Debian 10 Buster         | Fyzický   | 4x Intel i5 | 8 GB   |       ✅      |                |
| Debian 10 Buster         | LXC       | 2 vCPU      | 2 GB   |       ❌      |                |

> :warning: OpenVZ, Virtuozzo and LXC kontejnery nebudou s Mailcow: dockerized fungovat. Synology NAS také ne.

> Podporované OS (podle dokumentace): **CentOS 7, Debian 9/10 a Ubuntu 18.04/20.04**

## Proč Mailcow: dockerized
1. Je nenáročný na systémové prostředky
1. Je jednoduše nastavitelný (přes webové rozhraní)
1. Obsahuje webmail (SoGo), antispam i administraci
1. Je rozšířitelný
1. Je zdarma

## Příprava
1. Ověřte, zda jsou porty volné (`ss -tlpn | grep -E -w '25|80|110|143|443|465|587|993|995|4190|5222|5269|5443'`)
2. Ověřte, zda je čas na serveru správný (`timedatectl status`)

## Instalace
1. `curl -sSL https://get.docker.com/ | CHANNEL=stable sh`
1. `systemctl enable docker.service`
1. `systemctl start docker.service`
1. `curl -L https://github.com/docker/compose/releases/download/$(curl -Ls https://www.servercow.de/docker-compose/latest.php)/docker-compose-$(uname -s)-$(uname -m) > /usr/local/bin/docker-compose`
1. `chmod +x /usr/local/bin/docker-compose`
1. `su`
1. `cd /opt`
1. `git clone https://github.com/mailcow/mailcow-dockerized`
1. `cd mailcow-dockerized`
1. `./generate_config.sh` (FQDN = např. `mail.example.com`)
1. Další konfiguraci lze udělat pomocí `nano mailcow.conf`
1. `docker-compose pull`
1. `docker-compose up -d`

## Nainstalováno
1. Mailcow najdete na zvolené FQDN (např. `https://mail.example.com`)
