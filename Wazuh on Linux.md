# Instalace Wazuh na Linux
| OS                       | Container | CPU        | RAM         | Worked in 2020 |
|--------------------------|:---------:|:----------:|:-----------:|:--------------:|
| Debian 10 Buster         | KVM       | 8 jader    | 16 GB       |        ✅       |
| Debian 10 Buster         | KVM       | 1 jádro    |  2 GB       |        ⛔       |

Wazuh je založen na OSSEC.
K jeho instalaci je potřeba:
1. **Wazuh Server** (bude mít na starosti kontrolu ostatních stanic/serverů/desktopú)
1. **Wazuh Agent** (bude posílat svá data Wazuh Serveru)

## Instalace Wazuh Server
1. `curl -so ~/all-in-one-installation.sh https://raw.githubusercontent.com/wazuh/wazuh-documentation/4.0/resources/open-distro/unattended-installation/all-in-one-installation.sh && bash ~/all-in-one-installation.sh` - je užitečné použít `-d` (zobrazí veškerý output - debug) a `-i` (ignoruje health-check; zejména pokud se Wazuh Server instaluje na slabší server)

## Instalace Wazuh Agent
Existuje mnoho cest, jak instalovat Wazuh Agent. Ta nejjednodušší je:
1. `curl -so wazuh-agent.deb https://packages.wazuh.com/4.x/apt/pool/main/w/wazuh-agent/wazuh-agent_4.0.3-1_amd64.deb && sudo WAZUH_MANAGER='<IP_SERVERU>' dpkg -i ./wazuh-agent.deb` - *pozn. je opravdu potřeba, aby to byla IP. Doména způsobí chyby.*
1. `nano /var/ossec/etc/ossec.conf` - *lze přeskočit*
1. V `<ossec_config><client><server><address>` může být potřeba změnit IP. - *lze přeskočit*
1. service wazuh-agent start

## Informace
### Kde má Wazuh své uplatnění
Wazuh se hodí zejména pro
1. významné projekty, kde není prostor pro ruční hledání chyb v systému, logu, souborech, ...
1. provozovatele hostingu
1. bankovní, finanční a vládní sektor

Naopak zbytečný může být pro
1. osobní a domácí server
1. menší projekty
1. servery s méně než 4 GB RAM a 2 jádry (byť oficiální požadavky to netvrdí)

## Časté potíže při instalaci
### Wazuh Server
#### Čekám hodinu a nic se neděje
Nejspíš to skončilo chybou. Nejlepší je zkusit instalaci znovu s `-d`.

#### Končí s potíži s certifikátem
Nejspíš mu chybí balíčky pro generování certifikátu. Osobně doporučuji `apt install certbot`, může se hodit pro Nginx.

#### Chce to pro mě rozhodnutí, zda přepsat soubor
Potvrdit `Y`.

#### Kibana se inicializuje už přes hodinu
Upgrade serveru to vyřeší (na 2 GB RAM a 1 jádru instalace trvala přes 3 hodiny a to skončila chybou).

#### Když otevřu web, ukáže se hláška "Kibana server is not ready yet"
Opět to znamená, že Kibana se inicializuje a může to trvat nějakou dobu. Upgrade serveru to vyřeší.

#### Musím řešit zabezpečení API?
Ne, pouze u starší verze Wazuh Server.

### Wazuh Agent
#### Start skončí chybou (failed)
Možná je potřeba provést i změnu v souboru `/var/ossec/etc/ossec.conf` - kroky které lze přeskočit. Případně zkontrolujte jestli běží Wazuh Server na vzdáleném serveru.
