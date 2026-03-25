# Cvičení 1: Bankovní úvěr
Cílem je spočítat výslednou částku (jistinu i s úrokem) pro různé kombinace vkladů a sazeb.

![[PNNV_E01_01.png]]

## Zadání
Vytvořte vzorec pro výpočet výsledné částky po přičtení úroku.
Matematický model:
$$
X \times (1 + Y)
$$
- **X** = původní částka (jistina)
- **Y** = úroková sazba (např. 0,045 pro 4,5 %)

## Postup v Excelu
Do buňky `D5` zadej vzorec:
```excel
=$C5 * (1 + D$4)
```
Vzorec pak stačí roztáhnout do celého sloupce a následně do všech řádků tabulky.

![[PNNV_E01_02.png]]

## Proč to takhle funguje (Fixace buněk)
Klíčem je správné použití dolarů (`$`), aby se odkazy při roztahování neposunuly tam, kam nemají:

1.  **`$C5` (Fixace sloupce):** Dolar u písmena zajistí, že i při tažení doprava se Excel pořád dívá do sloupce **C** na základní částku. Číslo řádku zůstává volné, aby se při tažení dolů braly další hodnoty v pořadí.
2.  **`D$4` (Fixace řádku):** Dolar u čísla zajistí, že při tažení dolů se Excel pořád drží řádku **4**, kde jsou úrokové sazby. Písmeno sloupce zůstává volné, aby se při tažení doprava braly různé sazby.
3.  **Důležité:** Pokud má buňka formát **Procento**, Excel s ní vnitřně pracuje jako s desetinným číslem (4,5 % = 0,045). Proto stačí sazbu k jedničce přičíst, není třeba ji znovu dělit stem.

---

# Cvičení 2: Podmíněné formátování
V tomto cvičení nastavíme automatické zvýrazňování buněk podle jejich hodnot.

![[PNNV_E01_03.png]]

## Zadání
Aplikujte pravidla podmíněného formátování podle těchto kritérií:
*   **A) Rozmezí:** Hodnoty mezi horním a spodním limitem zvýrazněte červeným písmem.
*   **B) Extrémy:** Maximální hodnotu označte červeným pozadím a bílým písmem, minimální hodnotu modrým pozadím a žlutým písmem.
*   **C) Průměr a priorita:** Nadprůměrné hodnoty zvýrazněte zeleným písmem. Přidejte pravidlo pro Maximum (zelená výplň) a ověřte, jak se pravidla ovlivňují.

## Postup

### 1. Rozsah hodnot (Mezi)
Označ data a zvol: **Podmíněné formátování -> Pravidla zvýraznění buněk -> Mezi...**
Místo pevných hodnot klikni na buňky s limity. V nastavení formátu zvol červené písmo.

![[PNNV_E01_04.png]]
![[PNNV_E01_05.png]]

### 2. Absolutní extrémy (Min/Max)
Použij: **Pravidla pro nejvyšší a nejnižší hodnoty -> Prvních 10 položek...**
V dialogu změň 10 na **1**, aby se pravidlo týkalo jen absolutního maxima (nebo minima). Nastav barvy podle zadání.

![[PNNV_E01_06.png]]
![[PNNV_E01_07.png]]
![[PNNV_E01_08.png]]

### 3. Nadprůměr a správa priorit
Zvol: **Pravidla pro nejvyšší a nejnižší hodnoty -> Nad průměrem...** a nastav zelené písmo.
Nakonec přidej další pravidlo pro **Maximum** se zelenou výplní.

![[PNNV_E01_09.png]]
![[PNNV_E01_10.png]]

## Výsledek a hierarchie pravidel
Konečný vzhled tabulky určuje pořadí v seznamu pravidel.

![[PNNV_E01_11.png]]

**Důležité k pochopení:**
Ve **Správci pravidel** mají pravidla umístěná výše přednost. Pokud buňka splňuje více podmínek najednou, Excel aplikuje formát z toho pravidla, které je v seznamu prioritnější (výše). To je důvod, proč zelená výplň u maxima může přebít předchozí nastavení.
