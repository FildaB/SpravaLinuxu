# Debian
## Základní informace
ℹ **Debian je populární a jednou z nejstarších aktivních distribucí Linuxu.**
<br>ℹ Vhodný pro začátečníky.

### Proč vybrat Debian
✅ Velice rozšířený (až do státní správy), má velkou komunitu
<br>✅ Nekomerční
<br>✅ Nenáročný, jednoduchý a stabilní

### Proč nevybrat Debian
❌ Co si správce nestáhne přes `apt`, to nemá.

### Historie
- Vyvinul ho německý programátor **Ian Murdock** (* 28. dubna 1973, † 28. prosince 2015)
- Vydán v září 1993

### Větve
- `stable` - plně stabilní a otestovaná verze, určená pro produkční prostředí
- `testing` - nestabilní verze, která může obsahovat chyby
- `unstable` - nestabilní verze, která je určená pro vývojáře a není zcela vhodná pro produkční prostředí

### Verze k 2020
| Podporováno      | Verze   | Označení | Vydáno      | Ukončení podpory | Ukočení podpory LTS | Ukončení podpory ETLS            |
|------------------|---------|----------|-------------|------------------|---------------------|----------------------------------|
| ✅                | 13      | Trixie   | Očekává se  |                  |                     |                                  |
| ✅                |  12     | Bookworm | Očekává se  |                  |                     |                                  |
| ✅                |  11     | Bullseye | Očekává se  |                  |                     |                                  |
| ✅                |  10     | Buster   | 2019-07-06  | ~2022            |                     |                                  |
| ✅                |  9      | Stretch  | 2017-06-17  | 2020-07-06       | ~2022               |                                  |
| ❌                |  8      | Jessie   | 2015-04-25  | 2018-06-17       | ~2020-06-30         | ~2022-06-30                      |
| ❌                |  7      | Wheezy   | 2013-05-04  | 2016-04-25       | 2018-05-31          | ~2019-12-31                      |
| ❌                |  6.0    | Squeeze  | 2011-02-06  | 2014-05-31       | 2016-02-29          |                                  |
| ❌                |  5.0    | Lenny    | 2009-02-14  | 2012-02-06       |                     |                                  |
| ❌                |  4.0    | Etch     | 2007-04-08  | 2010-02-15       |                     |                                  |
| ❌                |  3.1    | Sarge    | 2005-06-06  | 2008-03-31       |                     |                                  |
| ❌                |  3.0    | Woody    | 2002-07-19  | 2006-06-30       |                     |                                  |
| ❌                |  2.2    | Potato   | 2000-08-15  | 2003-06-30       |                     |                                  |
| ❌                |  2.1    | Slink    | 1999-03-09  | 2000-09-30       | 2000-10-30          |                                  |
| ❌                |  2.0    | Hamm     | 1998-07-24  | -                |                     |                                  |
| ❌                |  1.3    | Bo       | 1997-07-02  | -                |                     |                                  |
| ❌                |  1.2    | Rex      | 1996-12-12  | -                |                     |                                  |
| ❌                |  1.1    | Buzz     | 1996-06-17  | -                |                     |                                  |
| ❌                |  0.93R6 |          | 1995-10-26  | -                |                     |                                  |
| ❌                |  0.93R5 |          | ~1995-03-01 | -                |                     |                                  |
| ❌                |  0.91   |          | ~1994-01-01 | -                |                     |                                  |

## Balíčkovací systém
Debian používá balíčkovací systém `deb`.
- Vydán 1. 1. 1994
- Je napsaný v C, C++ a Perl
- Licence GPLv2

### Fungování
Balíček je v binární podobě šířen pomocí jednoho zkompilovaného souboru. Název souboru je ve formátu `NAZEV_VERZE-REVIZE_ARCHITEKTURA.deb`, přičemž se jedná o typ archivu, ve kterém se nachází další soubory. Konkrétně tři:
- `debian-binary`
- `control.tar.gz`
- `data.tar.gz`

#### `dpkg`
`dpkg` (z angl. *debian package*) se stará o balíčky na daném zařízení - provádí jejich instalaci, odinstalaci, kontrolu závislostí atd.

##### Příkazy
- `dpkg -i UMISTENI_BALICKU` - instaluje balíček
- `dpkg -r BALICEK` - odinstaluje balíček, ale zanechá konfigurační soubory
- `dpkg -p BALICEK` - odinstaluje balíček a odebere i konfigurační soubory
- `dpkg --search UMISTENI` - vyhledá balíčky v určitém umístění

##### Umístění logu
Log dpkg se nachází ve výchozím nastavení v `/var/log/dpkg.log`.

#### `apt`
`apt` (z angl. *advanced packaging tool*) umožňuje stahovat a instalovat balíčky z různých zdrojů (typicky `ftp.debian.org`) a provádět jejich další správu. Pracuje jako nadstavba `dpkg`.

##### Příkazy
- `apt update` - aktualizuje lokální databázi verzí nainstalovaných balíčků.
- `apt upgrade` - stáhne nejaktuálnější verze balíčků podle své lokální databáze (pokud se nepoužije `apt update`, nemá v podstatě smysl).
- `apt install NAZEV_BALICKU` - nainstaluje balíček
- `apt remove NAZEV_BALICKU` - odinstaluje balíček, ale zanechá jeho konfigurační soubory
- `apt purge NAZEV_BALICKU` - odinstaluje baláček a odstraní i všechny konfigurační soubory
- `apt autoremove` - odstraní balíčky, které nejsou potřeba (hodí se provést po odinstalaci balíčků)
