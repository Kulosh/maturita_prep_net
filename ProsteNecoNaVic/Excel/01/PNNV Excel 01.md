# Cvičení 1: Bankovní úvěr
Výpočet celkové dlužné částky (jistina + úrok) pro různé kombinace vkladů a sazeb.

![[PNNV_E01_01.png]]

## Zadání
Vytvořte vzorec, který vypočítá výslednou částku po přičtení úroku.
Obecný matematický zápis:
$$
X \times (1 + Y)
$$
- **X** = původní částka (jistina)
- **Y** = úroková sazba (např. 0,045 pro 4,5 %)

## Výsledek
Do buňky `D5` zadejte vzorec:
```excel
=$C5 * (1 + D$4)
```
Následně vzorec roztáhněte (automatické vyplnění) do celého sloupce a poté do všech řádků tabulky.

![[PNNV_E01_02.png]]

## Vysvětlení (Smíšené odkazy)
Klíčem k úspěchu je správné zafixování buněk pomocí znaku `$`:

1. **`$C5` (Fixace sloupce):** Dolar před písmenem zajistí, že při tažení vzorce doprava zůstane odkaz stále na sloupci **C** (původní částka). Číslo řádku zůstává volné, aby se při tažení dolů braly další částky.
2. **`D$4` (Fixace řádku):** Dolar před číslem zajistí, že při tažení vzorce dolů zůstane odkaz stále na řádku **4** (úrokové sazby). Písmeno sloupce zůstává volné, aby se při tažení doprava braly různé sazby.
3. **`(1 + D$4)`:** Excel automaticky chápe formát **Procento** jako desetinné číslo (např. 4,5 % = 0,045). Proto stačí sazbu k jedničce prostě přičíst bez dělení stem.

---

# Cvičení 2: Podmíněné formátování s kritériem hodnota buňky

![[PNNV_E01_03.png]]

## Zadání
Máme nastavit různé výplně a obarvení podle kritétií.

- A) Hodnota je mezi horním a spodním limitem => má mít červené písmo
- B) Buňka s MAX hodnotou má mít červené pozadí a bílé písmo, Buňka s MIN hodnotou má mít Modré podbarvení a žluté písmo.
- C) Nadprůměrné hodnoty mají mít zelené písmo, buŇka s MAX hodnotou má mít zelenou barvu výplně
	- Zde začne plati pořadí podmínek, takže podle poskládání se pravidla aplikují.

## Výsledek + postup

Začnu tím že si vyberu formátování pro tabulku
![[PNNV_E01_04.png]]

Pro první pravidlo vyberu `Mazi` a nastavím hodnoty. Lze nastavit pomocí smazání výchozí hodnoty a poté kliknutí na danou buňku s rozmezím, také nesmím zapomenout zmněnit formát na vlastní a nastavit barvu písma na červenou.

![[PNNV_E01_05.png]]

Jako další vyberu nové pravidlo z nabídky `Pravidla pro nejvišší či nejnižší hodnoty` a zvolím `Prvních 10 položek`.
![[PNNV_E01_06.png]]
Poté přepíši počet z 10 na 1 aby to byla ta největší hodnota a zmněnim formátování.
![[PNNV_E01_07.png]]
to samé udělám poté pro nejnižší hodnotu.
![[PNNV_E01_08.png]]
Takto by tabulka poté měla vypadat.
![[PNNV_E01_09.png]]
Jako poslední zvolim nadprůměrem:
![[PNNV_E01_10.png]]
a na konec znova max ale ted na zelenou.
 Takto by měl vypadat výsledek:
 ![[PNNV_E01_11.png]]
Lze si všimnout že nejhornější pravidlo co nastavuje pozadí na zelenou přebilo nižší pravidla a pravidlo `Nad průměrem` přebarvilo tu 100 na zelené písmo a tím přebilo pravidlo `Prvních 1` které je až podtím a mělo to obarvit na bílé písmo a červené podbarvení.




