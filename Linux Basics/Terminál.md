# Jak používat terminál v Linuxu
## Klávesy
1. `TAB` - dokončí příkaz (a má i další funkce)
2. `[klávesa šipka nahoru]` - hodí dříve použitý příkaz (z `history`)

## Klávesa `CTRL`
### Procesy
1. `CTRL+C` - ukončí běžící proces (užitečné když se pustí např. `ping`)
1. `CTRL+D` - ukončí relaci (obdobně jako `exit` nebo `logout`)
1. `CTRL+Z` - zastaví běžící proces

### Výstup a vstup
1. `CTRL+L` - vyčistí obrazovku
2. `CTRL+E` - *end* - přesune na konec řádku
3. `CTRL+A` - přesune na začátek řádku
4. `CTRL+B` - *backward* - posune o znak zpět
5. `CTRL+F` - *forward* - posune o znak vpřed
6. `CTRL+D` - *delete* - smaže znak za kurzorem (podobně jako klávesa `DELETE`)
9. `CTRL+K` - smaže všechen text za kurzorem (podobně jako klávesa `DELETE` až do konce řádku)
10. `CTRL+X` a ihned `BACKSPACE` - smaže celý řádek
11. `CTRL+T` - *transpose* - prohodí znak pod kurzorem se znakem před (např. z `sp` udělá `ps`)

## `!`
1. `!!` - provede poslední příkaz znovu

### Další příkazy
3. `!top` - provede příkaz `top` tak, jak byl naposledy proveden
4. `!top:p` - zobrazí jak by byl příkaz `!top` proveden
5. `!$` - provede poslední slovo posledního příkazu (pokud byl poslední příkaz `cd /slozka` pak se provede `/slozka`)
2. `!*` - zobrazí poslední slovo posledního příkazu
