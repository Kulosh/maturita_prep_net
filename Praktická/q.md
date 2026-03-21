> [!question] # 10. Základy programování
> Datové struktury, datové typy, konverze hodnot datových typů, práce se vstupem, práce s výstupem, procedury, funkce, práce s parametry procedury a funkce, operátory, rozhodovací konstrukce, cykly (for, while, foreach, ...), práce s polem, práce s řetězci, dynamické datové struktury.

## ODPOVĚĎ:

### 1. Proměnné a datové typy
Proměnná je pojmenované místo v paměti, které uchovává určitou hodnotu. Datový typ pak určuje, co v proměnné může být, kolik paměti zabírá a jaké operace s ní lze provádět.

**Základní datové typy:**
- **int:** Celá čísla (např. `10`, `-5`).
- **double / float:** Desetinná čísla (např. `3.14`).
- **bool:** Logické hodnoty (`true` / `false`).
- **char:** Jeden znak (např. `'A'`).
- **string:** Textový řetězec (např. `"Ahoj"`).

```csharp
int a = 5;
int b = 10;
int soucet = a + b;

Console.WriteLine("Součet: " + soucet);
```
*Výstup: Součet: 15*

```csharp
double cena = 1.99;
double dph = 0.21;

double vysledek = cena * dph;

Console.WriteLine(vysledek);
```
*Výstup: 0,4179*

```csharp
bool jePlnolety = true;
bool maRidicak = false;

if (jePlnolety && maRidicak)
{
    Console.WriteLine("Můžeš řídit auto.");
}
else
{
    Console.WriteLine("Nemůžeš řídit auto.");
}
```

```csharp
char pismeno = 'A';

Console.WriteLine(pismeno);
```
*Výstup: A*

```csharp
string jmeno = "Jan";
string prijmeni = "Novak";

Console.WriteLine("Jmeno:" + jmeno + " Prijmeni:" + prijmeni);
```
*Výstup: Jmeno:Jan Prijmeni:Novak*

---

### 2. Práce s řetězci (String)
String je v C# objekt, který nabízí mnoho užitečných metod pro manipulaci s textem.

```csharp
string delkaTextu = "Anakonda";

Console.WriteLine(delkaTextu.Length);
```
*Výstup: 8*

```csharp
string delkaTextu = "Anakonda";

Console.WriteLine(delkaTextu.ToUpper());
```
*Výstup: ANAKONDA*

```csharp
string delkaTextu = "Anakonda";

Console.WriteLine(delkaTextu.ToLower());
```
*Výstup: anakonda*

---

### 3. Konverze datových typů
Někdy potřebujeme změnit jeden typ na druhý.

- **Implicitní (automatická):** Menší typ se bezpečně převede na větší.
- **Explicitní (přetypování):** Musíme ručně uvést typ v závorce.
- **Convert:** Třída pro převody.

---

### 4. Vstup a výstup dat

```csharp
Console.WriteLine("Zadejte jméno:");

string jmeno = Console.ReadLine();

Console.WriteLine( "Ahoj " + jmeno + "!");
```

```csharp
Console.WriteLine("Zadejte věk:");

int vek = Convert.ToInt32(Console.ReadLine());

Console.WriteLine( "Ahoj " + vek + " let starý");
```

---

### 5. Operátory

```csharp
int a = 10;
int b = 3;

Console.WriteLine(a + b);
Console.WriteLine(a - b);
Console.WriteLine(a * b);
Console.WriteLine(a / b);
Console.WriteLine(a % b);
```

---

### 6. Rozhodovací konstrukce

**IF - ELSE IF - ELSE**
```csharp
int znamka = 2;

if (znamka == 1)
{
    Console.WriteLine("Výborný");
}
else if (znamka == 2)
{
    Console.WriteLine("Chvalitebný");
}
else
{
    Console.WriteLine("Jiná známka");
}
```

**SWITCH**
```csharp
int den = 3;

switch (den)
{
    case 1:
        Console.WriteLine("Pondělí");
        break;

    case 2:
        Console.WriteLine("Úterý");
        break;

    case 3:
        Console.WriteLine("Středa");
        break;

    default:
        Console.WriteLine("Jiný den");
        break;
}
```

---

### 7. Cykly

**FOR Cyklus**
```csharp
for (int i = 0; i < 5; i++)
{
    Console.WriteLine(i);
}
```

**FOREACH Cyklus**
```csharp
string[] jmena = { "Petr", "Jan", "Eva" };

foreach (string jmeno in jmena)
{
    Console.WriteLine(jmeno);
}
```

---

### 8. Datové struktury

**Pole (Array)**
```csharp
int[] cisla = new int[10];

cisla[0] = 1;
cisla[1] = 2;
cisla[2] = 3;
cisla[3] = 4;
cisla[4] = 5;
cisla[5] = 6;
cisla[6] = 7;
cisla[7] = 8;
cisla[8] = 9;
cisla[9] = 10;

Console.WriteLine(cisla[0]);
Console.WriteLine(cisla[1]);
Console.WriteLine(cisla[2]);
```

---

### 9. Procedury a funkce

**Procedura**
```csharp
void Pozdrav(){
    Console.WriteLine("AHOJ Čau");
}

Pozdrav(); // zde proceduru volám
```

---

### 10. Pokročilé příklady (Pole a funkce)

**Součet pole**
```csharp
int[] cisla = { 5, 10, 15, 20 };

int soucet = 0;

for (int i = 0; i < cisla.Length; i++)
{
    soucet += cisla[i];
}

Console.WriteLine("Součet je: " + soucet);
```

**Největší číslo v poli**
```csharp
int[] cisla = { 3, 8, 2, 10, 6 };

int max = cisla[0];

for (int i = 1; i < cisla.Length; i++)
{
    if (cisla[i] > max)
    {
        max = cisla[i];
    }
}

Console.WriteLine("Největší číslo: " + max);
```
