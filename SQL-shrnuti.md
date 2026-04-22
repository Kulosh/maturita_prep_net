# SQL

## Před začátkem

Pokud si nevíš rady jak se píšou triggery apod. tak je tu karta `Template Explorer`.

Tuto kartu najdeš a spustíš v záložce `View`/`Zobrazit` v horní liště SQL Studia a nebo pomocí zkratky `CTRL + ALT + T`.

---

## Vytváření Databází

Podmínka pro **opakované** spuštění vytvářecího scriptu

> *Tato podmínka kontroluje jestli DB již neexistuje a pokud ano, tak ji smaže*

```SQL
USE master;
GO

IF EXISTS (SELECT * FROM sys.databases WHERE name = N'<jméno-databáze>')
BEGIN
    ALTER DATABASE <jméno-databáze> SET SINGLE_USER WITH ROLLBACK IMMEDIATE;
    DROP <jméno-databáze>;
END;
GO
```

Vytvoření a přepnutí databáze

```SQL
CREATE DATABASE <jméno-databáze>;
GO

USE <jméno-databáze>;
GO
```

---

## Vytváření tabulek

Vytvoření tabulek

```SQL
CREATE TABLE tbCustomers (
    Id INT PRIMARY KEY IDENTITY(1,1),    -- Identity nastavuje automatické navýšení Id
    [Name] NVARCHAR(255) NOT NULL,    -- Name je v [], aby bylo jasné, že to není sys. funkce/proměnná
    Email NVARCHAR(255) NOT NULL UNIQUE,    -- Email musí být unikátní
    Age INT NOT NULL CHECK(Age >= 18),    -- Kontrola že je osobě min. 18
    RegistrationDate DATE NOT NULL DEFAULT GETDATE(),    -- Nastavi datum registrace na aktuální
    Phone NVARCHAR(9) NULL,
    Active BIT NOT NULL DEFAULT 1    -- Alternativa pro Boolean -> hodnoty 0/1
);
```

```SQL
CREATE TABLE tbOrders (
    Id INT PRIMARY KEY IDENTITY(1,1),
    CustomerId INT,
    OrderDate DATETIME NOT NULL DEFAULT GETDATE(),

    CONSTRAINT FK_tbOrders_tbCustomers FOREIGN KEY (CustomerId)
    REFERENCES tbCustomers(Id)

    /*
        Pokud nechceme řešit FK_constraint při mazání záznamu z tbCustomers
        a chceme aby se se zákazníkem smazali i objednávky, tak bude Constraint
        vypadat následovně
    */

    CONSTRAINT FK_tbOrders_tbCustomers FOREIGN KEY (CustomerId)
    REFERENCES tbCustomers(Id) ON DELETE CASCADE
);
```

---

## Vkládání dat do tabulky

Template

```sql
INSERT INTO <jméno-tabulky> (<pole1>, <pole2>,...)
VALUES
(<hodnotaPole1>, <hodnotaPole2>,...),
(<hodnotaPole1>, <hodnotaPole2>,...);
GO
```

Příklad

```sql
INSERT INTO tbCustomers ([Name], Email, Age, Phone)
VALUES
(N'Franta', N'franta@example.com', 23, null),
(N'Pepa', N'pepa@example.com', 19, N'123456789');
GO
```

Vkládat lze i pomocí `SELECT`

```sql
INSERT INTO <jméno-tabulky> (<pole1>, <pole2>,...)
SELECT <pole1>, <pole2>,... FROM <tabulka>;    -- Případně WHERE atd...
GO
```

---

## Mazání tabulek a DB

> **POZOR** na Foreign Keys a Constraints

Tabulku smažeme pomocí `DROP TABLE`

```sql
DROP TABLE <jméno-tabulky>;
GO
```

Pokud chceme tabulku jenom vyprázdnit tak můžeme použít příkaz `TRUNCATE TABLE`

```sql
TRUNCATE TABLE <jméno-tabulky>;
GO
```

---

> **POZOR** Před smazáním DB je potřeba změnit aktuálně používanou DB např. z `Northwind` na `master`
>
>```sql
> USE master;
> GO
>```

DB smažeme pomocí `DROP DATABASE`

```sql
DROP DATABASE <jméno-databáze>;
GO
```

---

## Zobrazování dat pomocí `SELECT`

`SELECT` syntaxe (asi nejuniverzálnější template)

```sql
-- Zobrazení dat z tabulky
SELECT
    
    -- zobrazí unikátní hodnoty (bez duplicit)
    [ DISTINCT ]

    -- Zobrazí určité množství řádků na vršku tabulky
    [ TOP <počet> (defaultně řádky) [ PERCENT ] ]

    -- všechny pole z tabulky | uživatelem vybraná pole
    * | <pole1>,...

-- Výběr základní tabulky
FROM <tabulka>

-- propojení více tabulek
[ [ INNER | LEFT [ OUTER ] | RIGHT [ OUTER ] | [ FULL ] OUTER ] JOIN <tabulka> ON <tabulka1>.<pole> = <tabulka2>.<pole> ]

-- Normální filtr na základě Bool nebo logických operátorů
[ WHERE <podmínky> ]

-- Seskupení podle pole (povinné při SELECTu s agr. fn. a normálníma polema)
[ GROUP BY <pole1>,... ]

-- Filtrace pomocí agr. fn. na základě Bool nebo logických operátorů
[ HAVING <podmínky> ]

-- Seřazení podle pole vzestupně/sestupně
[ ORDER BY <pole1>,... [ ASC | DESC ] ]
```

---

### Příklad {selects}

Zobrazení celé tabulky tbCustomers

```sql
SELECT *
FROM tbCustomers;
GO
```

| Id | Name            | Email                     | Age | RegistrationDate | Phone     | Active |
|----|-----------------|---------------------------|-----|------------------|-----------|--------|
| 1  | Sammy Smiley    | ssmiley0@guardian.co.uk   | 100 | 2025-04-18       | 439255962 | 1      |
| 2  | Andriana Meegin | ameegin1@sciencedaily.com | 76  | 2025-09-21       | 726853768 | 0      |
| 3  | Bell Bye        | bbye2@tripadvisor.com     | 90  | 2025-08-12       | 542206133 | 1      |
| 4  | Phedra Spuffard | pspuffard3@phpbb.com      | 57  | 2025-10-16       | 459920176 | 1      |
| 5  | Iggie Larmet    | ilarmet4@soup.io          | 62  | 2026-01-24       | 295882967 | 0      |

---

Všechna pole, ale jen aktivní zákazníci

```sql
SELECT * 
FROM tbCustomers
WHERE Active = 1;
GO
```

| Id | Name            | Email                     | Age | RegistrationDate | Phone     | Active |
|----|-----------------|---------------------------|-----|------------------|-----------|--------|
| 1  | Sammy Smiley    | ssmiley0@guardian.co.uk   | 100 | 2025-04-18       | 439255962 | 1      |
| 3  | Bell Bye        | bbye2@tripadvisor.com     | 90  | 2025-08-12       | 542206133 | 1      |
| 4  | Phedra Spuffard | pspuffard3@phpbb.com      | 57  | 2025-10-16       | 459920176 | 1      |

---

Jméno, Počet objednávek (včetně zákazníku s 0 objednávkami)

```SQL
SELECT
    c.Name,
    COUNT(o.Id) AS OrdersCount    -- COUNT() spočítá Id objednávek pro daného zákazníka,,, AS pojmenuje pole s počtem objednávek
FROM tbCustomers c -- c je alias pro tabulku tbCustomers
LEFT JOIN tbOrders o ON c.Id = o.CustomerId    -- Kdyby tu byl pouze INNER JOIN tak se nezobrazí Iggie Larmet s 0 objednávkami
GROUP BY c.Name;    -- Kvůli agr. fn. zde musí být GROUP BY, jinak chyba
GO
```

| Name            | OrdersCount |
|-----------------|-------------|
| Andriana Meegin | 13          |
| Bell Bye        | 14          |
| Iggie Larmet    | 0           |
| Phedra Spuffard | 9           |
| Sammy Smiley    | 14          |

---

Jméno, Počet objednávek, kde je počet objednávek vyšší než 10

```sql
SELECT
    c.Name,
    COUNT(o.Id) AS OrdersCount
FROM tbCustomers c
LEFT JOIN tbOrders o ON c.Id = o.CustomerId
GROUP BY c.Name
HAVING COUNT(o.Id) > 10;
GO
```

| Name            | OrdersCount |
|-----------------|-------------|
| Andriana Meegin | 13          |
| Bell Bye        | 14          |
| Sammy Smiley    | 14          |

---

Stejné co předchozí, ale seřadit podle jmen sestupně

```sql
SELECT
    c.Name,
    COUNT(o.Id) AS OrdersCount
FROM tbCustomers c
LEFT JOIN tbOrders o ON c.Id = o.CustomerId
GROUP BY c.Name
HAVING COUNT(o.Id) > 10
ORDER BY c.Name DESC;
GO
```


| Name            | OrdersCount |
|-----------------|-------------|
| Sammy Smiley    | 14          |
| Bell Bye        | 14          |
| Andriana Meegin | 13          |

---

> Lze toho vymyslet spoustu, tyto příklady slouží pouze na pochopení, složitější úlohy jsou na disku nebo ve videu

---

## Úprava dat `UPDATE`

Upravý hodnotu pole u všech záznamů v tabulce nebo u vybraných na základě podmínky

```sql
UPDATE <tabulka>
SET <pol1> = hodnota,...
[ WHERE <podmínka> ];
GO
```

---

## Smazání dat `DELETE`

Smaže záznam na základě podmínky z dané tabulky

```sql
DELETE FROM <tabulka>
WHERE <podmínka>;
GO
```

---

## Funkce

Funkce je blok s SQL dotazem, který lze opakovaně volat, má návratový typ a neumí upravovat data v DB

> Jako návratová hodnota může být datový typ nebo tabulka

```sql
CREATE OR ALTER FUNCTION fn_<název funkce>
(
    [ @<parametr1> <datový typ> ],
    ...
)
RETURNS <návratová hodnota>
AS
BEGIN
    <SQL statement>
    RETURN <hodnota (výsledek statementu)>
END;
GO
```

Pro zavolání používáme `dbo.fn_<název funkce>`

```sql
SELECT dbo.fn_<název funkce>(<parametr1>,...)

-- nebo

PRINT dbo.fn_<název funkce>(<parametr1>,...)
```

### Příklad {functions}

```sql
CREATE OR ALTER FUNCTION fn_Sum
(
    @Value1 INT,
    @Value2 INT
)
RETURNS INT
AS
BEGIN
    RETURN @Value1 + @Value2;
END;
GO
```

```sql
DECLARE @Sum INT = dbo.fn_Sum(1,2);
PRINT CONCAT(N'RESULT: ', @Sum);
GO
```

Output:

```bash
RESULT: 3
```

---

## Uložené procedury

Jsou podobné jako funkce, ale na rozdíl od nich můžou vykonávat datové operace a nemusí mít návratovou hodnotu

```sql
CREATE OR ALTER PROCEDURE sp_<název procedury>
    [ @<parametr1> <datový typ> [ = <defaultní hodnota> ] [ OUTPUT ]], -- OUTPUT = při zavoální vrátí poslední hodnotu parametru
    ...
AS
BEGIN
    <SQL statement>
END;
GO
```

### Příklad {procedures}

```sql
CREATE OR ALTER PROCEDURE sp_Sum
    @Value1 INT = 0,
    @Value2 INT = 0
AS
BEGIN
    DECLARE @Result INT = @Value1 + @Value2;
    PRINT CONCAT(N'Result: ', @Result);
END;
GO
```

Pro zavolání použijeme příkaz `EXEC` / `EXECUTE`

```sql
EXEC sp_Sum 1, 2;
GO

-- Pokud bychom chtěli využít defaultní hodnoty

EXEC sp_Sum default, 2;
GO
```

Output:

```bash
Result: 3

# s defaultní hodnotou

Result: 2
```

---

## `TRIGGER`

Učel triggeru, nebo spouště, je spustit nadefinovaný `SQL statement` na základě události, která se stala na zvolené tabulce. (v podstatě JS EventListener())

`TRIGGER` syntax

```sql
CREATE OR ALTER TRIGGER trg_<jméno triggeru>
ON <tabulka>    -- Tabulka na které poslouchá
AFTER | INSTEAD OF < UPDATE | INSERT | DELETE >    -- Operace na kterou čeká
AS
    <SQL statement>
GO
```

`AFTER` - pustí `SQL statement` v triggeru až po úspěšném dokončení operace

`INSTEAD OF` - pustí `SQL statement` v triggeru místo dané operace

### Příklad {triggers}

Trigger, který smaže objednávky s Id zákazníka, kterému se změní Active 1 => 0

```sql
CREATE OR ALTER TRIGGER trg_RemoveOrdersForInactiveCustimers
ON tbCustomers
AFTER UPDATE
AS
    IF UPDATE(Active)
    BEGIN
        DELETE FROM tbOrders
        WHERE CustomerId IN (
            SELECT c.Id
            FROM tbCustomers c
            INNER JOIN inserted i ON c.Id = i.Id
        );
    END;
GO 
```

---

Trigger, který vrátí chybu, pokud zákazník má objednávky

```sql
CREATE OR ALTER TRIGGER trg_ThrowErrorIfCustomerHasOrders
ON tbCustomers
INSTEAD OF DELETE
AS
    IF EXISTS (
        SELECT 1
        FROM tbOrders o
        INNER JOIN tbCustomers c ON o.CustomerId = c.Id
        INNER JOIN deleted d ON c.Id = d.Id
        WHERE o.CustomerId = d.Id
    )
    BEGIN
        RAISERROR(N'ERROR! Customer has existing orders', 16, 1);
    END
    ELSE
    BEGIN
        DELETE FROM tbCustomers
        WHERE Id IN (SELECT Id FROM deleted)
    END;
GO
```

---

## Pivot

Pivot, přezdívaný tak jako crosstab query, je typ dotazu, který nám v podstatě umožňuje groupovat ne jenom v řádcích ale i v námi definovaných sloupcích

`PIVOT` syntax

```sql
SELECT <pole1>,..., <[user-defined pole1]>,...
FROM
(
    <SQL statement>
) ds    -- na pojmenování aliasu nezáleží ale musí tu být
PIVOT
(
    <agr. fn>(<pole z from>)    -- jak chceme seskupit
    IN <pole z from> FOR ([user-defined pole1],...)    -- podle ceho
) pvt;
GO
```

### Příklad {pivots}

`PIVOT`, který ukáže počet objednávek v jednotlivých letech podle zákazníka

```sql
-- Pole v [] jsou většinou user-defined a slouží jako filtr/group
-- POZOR, v user-defined polích je potřeba si uvědomit, že jeho název
-- je hodnota podle který se filtruje/groupuje v sloupcích, takže bacha
-- na to co do nich dáte
SELECT Id, [2025], [2026]
FROM
(
    SELECT
        c.Id,    -- Hodnoty pro pole Id
        o.Id AS OrderId,    -- Data pro COUNT() v pivotu
        YEAR(o.OrderDate) AS OrderYear    -- Data pro filtr/group pivot
    FROM tbCustomers c
    LEFT JOIN tbOrders o ON c.Id = o.CustomerId    -- Ať vidím i zákazníky bez objednávek
) ds
PIVOT
(
    COUNT(OrderId)    -- hodnoty v sloupcích
    FOR OrderYear IN ([2025], [2026])    -- doplnění hodnot do sloupců
) pvt;
GO
```

OUTPUT:

| Id | 2025 | 2026 |
|----|------|------|
| 1  | 11   | 3    |
| 2  | 10   | 3    |
| 3  | 8    | 6    |
| 4  | 7    | 2    |
| 5  | 0    | 0    |

---

## Switch-case

Elegantnější forma IF-ELSE, na základě známé hodnoty můžeme udělat určitou operaci.

`CASE` syntax

```sql
CASE
    WHEN <podmínka1> THEN <výsledek1>
    WHEN <podmínka2> THEN <výsledek2>
    ...
    ELSE <výsledek, když žádná podmínka nesplněná>
END;
GO
```

### Příklad {case}

| User            | RoleId |
|-----------------|--------|
| Sammy Smiley    | 1      |
| Andriana Meegin | 2      |
| Bell Bye        | 1      |
| Phedra Spuffard | 3      |
| Iggie Larmet    | 2      |

```sql
SELECT
    [User],
    CASE
        WHEN RoleId = 1 THEN 'User'
        WHEN RoleId = 2 THEN 'Operator'
        ELSE 'Admin'
    END AS Role
FROM tbUsers;
GO
```

| User            | Role     |
|-----------------|----------|
| Sammy Smiley    | User     |
| Andriana Meegin | Operator |
| Bell Bye        | User     |
| Phedra Spuffard | Admin    |
| Iggie Larmet    | User     |
