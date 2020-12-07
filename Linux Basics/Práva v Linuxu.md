# Práva v Linuxu
## Co je to přístupové právo v Linuxu
Přístupové právo umožňuje definovat přístup k adresářům a souborům na základě uživatelských účtů a skupin uživatelů. Kontrola přístupu umožňuje na systémové úrovni **zabránit** uživatelům, aby **záměrně nebo omylem cizí data poškodili nebo zneužili**. (*Wikipedie, upraveno*)

## Základní rozdělení oprávnění
K souborům a složkám nemusí mít každý v systému přístup. Pomáhá to například k bezpečnosti a správná volba oprávnění ke složce může být dokonce kritická (např. na webovém serveru).

Přístup k souboru lze upravit:
1. Jednomu konkrétnímu uživateli (vlastníkovi)
1. Jedné konkrétní skupině
1. Těm ostatním (ti, co nejsou ani tím vybraným uživatelem, ani ve skupině)

## Vlastnictví souboru a složky
### Uživatel (vlastník)
Ten, kdo soubor/složku vytvoří, je jeho vlastník. Vlastník ale může být kdykoli změněn příkazem `chown` (*change owner*), například `chown uzivatel:jeho_skupina soubor.txt`.

### Skupina
V Linuxu (ale i ostatních OS) existují skupiny. Každý uživatel může do nějaké skupiny patřit.
Skupina tak může mít rozdílná oprávnění než vlastník souboru, zároveň ale i rozdílná oprávnění než všichni ostatní uživatelé.

*Například pokud vytvářím server, na který se bude přihlašovat firma, je vhodné každé oddělení dát do skupiny. Například *vedení*, *ekonomický úsek*, *zaměstnanci*, *IT*. Vzhledem k rozsáhlým kybernetickým útokům v poslední době je tento postup více než žádoucí, všechno kromě *IT* by mělo mít omezená práva. A například pokud chci, aby do složky mělo přístup jen vedení, tak vlastníkem složky nastavím danou skupinu.*

### Ostatní
Jsou ti, kteří nespadají do dvou zmíněných kategorií. *Obvykle by měli mít nižší nebo stejná práva.*

## Zobrazení v `ls -l`
Zobrazí práva v následujícím formátu: `drwxrwxrwx`

### Zakládní rozdělení
| -   | rwx                 | rwx                         | rwx                           |
|-----|---------------------|-----------------------------|-------------------------------|
| Typ | Oprávnění vlastníka | Oprávnění skupiny           | Oprávnění ostatních uživatelů |

1. První znak `-` znamená, že určujeme oprávnění k souboru. Pokud by místo něj bylo například `d`, znamenalo by to, že se jedná o složku (**directory**).
1. Další tři znaky označují oprávnění vlastníka.
1. Další tři znaky označují oprávnění určité skupiny.
1. Další tři znaky označují oprávnění ostatních uživatelů systému.

### Rozdělení práv
| r                | w                | x                                                    |
|------------------|------------------|------------------------------------------------------|
| přečíst (*read*) | zapsat (*write*) | spustit soubor (*execute*)<br>nebo<br>otevřít složku |

Pokud je dané právo uděleno, pak je se v označení práv zobrazí znak daného práva (`r`, `w`, `x`). Pokud právo uděleno není, zobrazí se místo něj pomlčka `-`.
Právo "`x`" může mít dva významy:
1. u souboru se jedná o právo ke spuštění souboru (podobně jako přípona `exe` ve Windows, ale v Linuxu jde spustit jakýkoli soubor)
1. u složky se jedná o právo k zobrazení obsahu složky (které soubory se v ní nachází)

Každé právo je možné udělit bez ohledu na ostatní práva *(například uživatel může zapisovat do souboru, i když nemá právo soubor číst)*.

## Číselné vyjádření
Číselné vyjádření vznikne součtem udělených práv. Každé právo má své číslo:
| R | W | X |
|---|---|---|
| 4 | 2 | 1 |

Tato čísla se pak sčítají a tím vznikne číselné vyjádření daného práva. Pokud právo není uděleno, přičte se nula. Pokud je uděleno, přičte se jeho hodnota. Například: `r-x` znamená `4+0+1=5`, `r--` znamená `4+0+0=4`, `---` znamená `0+0+0=0` (žádné práva). Nejvyšší možné právo je **7** - soubor/složku lze číst, zapisovat i spouštět/otevřít.
I tak platí předchozí tabulka, jen je v číselné podobně.

| 7                   | 7                           | 7                             |
|---------------------|-----------------------------|-------------------------------|
| Oprávnění vlastníka | Oprávnění skupiny           | Oprávnění ostatních uživatelů |
