# Práva v Linuxu

## Zobrazení v `ls -l`
Zobrazí práva v následujícím formátu: `drwxrwxrwx`

### Zakládní rozdělení
| d   | rwx                 | rwx                         | rwx                           |
|-----|---------------------|-----------------------------|-------------------------------|
| Typ | Oprávnění vlastníka | Oprávnění skupiny vlastníka | Oprávnění ostatních uživatelů |

1. První znak `d` znamená složka (**directory**). Pomlčka `-` by označovala soubor, např. `-rwxrwxrwx`.
1. Další tři znaky označují oprávnění vlastníka.
1. Další tři znaky označují oprávnění skupiny, do které vlastník patří.
1. Další tři znaky označují oprávnění ostatních uživatelů systému.

### Rozdělení práv
| r                | w                | x                                                    |
|------------------|------------------|------------------------------------------------------|
| přečíst (*read*) | zapsat (*write*) | spustit soubor (*execute*)<br>nebo<br>otevřít složku |

Pokud je dané právo uděleno, pak je se v označení práv zobrazí znak daného práva (`r`, `w`, `x`). Pokud právo uděleno není, zobrazí se místo něj pomlčka `-`.
Právo "`x`" může mít dva významy:
1. u souboru se jedná o právo ke spuštění souboru (podobně jako exe)
1. u složky se jedná o právo k zobrazení obsahu složky (které soubory se v ní nachází)
Každé právo je možné udělit bez ohledu na ostatní práva *(například uživatel může zapisovat do souboru, i když nemá právo soubor číst)*.

## Číselné vyjádření
Číselné vyjádření vznikne součtem udělených práv. Každé právo má své číslo:
| R | W | X |
|---|---|---|
| 4 | 2 | 1 |

Tato čísla se pak sčítají a tím vznikne číselné vyjádření daného práva. Pokud právo není uděleno, přičte se nula. Například: `r-x` znamená `4+0+1=5`. Nejvyšší možné právo je **7** - soubor/složku lze číst, zapisovat i spouštět/otevřít.
I tak platí předchozí tabulka, jen je v číselné podobně.

| 7                   | 7                           | 7                             |
|---------------------|-----------------------------|-------------------------------|
| Oprávnění vlastníka | Oprávnění skupiny vlastníka | Oprávnění ostatních uživatelů |
