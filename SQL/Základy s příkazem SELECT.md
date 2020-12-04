# Co je to databáze
- Databáze se skládá z tabulek.
- Tabulky se skládají ze sloupců.
- Do tabulek se ukládají data (lidé tomu s oblibou říkají **záznamy**).

Jednoduchá tabulka:

| ID | Jméno (jmeno)    | Rok narození (rok) |
|----|----------|----------|
| 1  | Daniela  | 2002 |
| 2  | Jarmila  | 2003 |
| 3  | Alena    | 2002 |

*na tuto tabulku se bude níže odkazovat

*pozn. v SQL se **nesmí používat diakritika**, ale pro jednoduchost to tady tak bude.

# Příkaz SELECT

## Přehledné vysvětlení
`SELECT` - výběr dat z tabulky. Ustálená forma (přes to nejede vlak):
```
SELECT ... FROM ... WHERE ... ORDER BY ...
```

## Základní forma
```
SELECT sloupec1, sloupec2
FROM tabulka
WHERE podmínky
ORDER BY řazení
```

### Co vybírám
1. `SELECT *` - vybere **všechny sloupce** (nejjednodušší a univerzální varianta)
1. `SELECT jmeno, rok` - vybere data **jenom ze zadaných sloupců**
1. `SELECT DISTINCT rok` - vybere jenom **jedinečné řádky** (tento příklad tudíž vybere jenom roky 2002 a 2003)

### Odkud vybírám
1. `FROM tabulka` - jediná možnost

### Jaké mám podmínky
1. `WHERE rok = "2002"` - budou se hledat řádky, u kterých **je** rok narození 2002
1. `WHERE rok LIKE "2002"` - alternativa pro 1.
1. `WHERE rok NOT LIKE "2002"` - budou se hledat řádky, u kterých **není** rok narození 2002
1. `WHERE jmeno LIKE "%e%"` - pokud se použije **%**, tak se hledá jakékoli jméno, které obsahuje písmeno e

| =          | Se rovná                  | rok = 2002                |
|------------|---------------------------|---------------------------|
| >          | Číslo je větší než        | rok > 2001                |
| <          | Číslo je menší než        | rok < 2004                |
| >=         | Číslo je větší nebo rovno | rok >= 2002               |
| <=         | Číslo je menší nebo rovno | rok <= 2003               |
| <> nebo != | Není rovno                | rok != 2002               |
| BETWEEN    | V číselném intervalu      | rok BETWEEN 2001 AND 2004 |
| LIKE       | Obsahuje zadaný text      | jmeno LIKE "%e%"          |
| IN         | Obsahuje určité hodnoty   | rok IN (2002, 2003)       |

### Jak to chci seřadit

1. `ORDER BY rok` - bude se řadit vzestupně
1. `ORDER BY rok ASC` - **ascending** - bude se řadit vzestupně (např. od 1 do 100 nebo od A do Z)
1. `ORDER BY rok DESC` - **descending** - bude se řadit sestupně (např. od 100 do 1 nebo od Z do A)
1. `ORDER BY rok, jmeno` - bude řadit vzestupně nejprve podle roku a poté i podle jména

## Propojování
### Příklad
#### Tabulka `Farma`

| ID | Jméno | Rok narození | Zvíře_ID |
|----|-------|----------|----------|
| 1  | Pepík | 2019     | 1        |
| 2  | Alík  | 2016     | 2        |
| 3  | Karel | 2020     | 1        |

#### Tabulka `Zvířata`
| ID | Zvíře | Jídlo          |
|----|-------|----------------|
| 1  | Prase | Všechno        |
| 2  | Pes   | Maso, konzervy |

### Jak propojit více tabulek
Pokud mám více tabulek, které spolu souvisí, můžu je propojit pomocí ID a dát jejich řádky dohromady.

```
SELECT * FROM Farma, Zvířata WHERE Farma.Zvíře_ID = Zvířata.ID
```
