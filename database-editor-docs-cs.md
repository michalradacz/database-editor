# Editor databáze - Uživatelská příručka

https://github.com/michalradacz/database-editor

---

## Úvod

Editor databáze je webová aplikace pro vytváření a správu jednoduchých relačních databází. Umožňuje definovat více tabulek s různými typy polí, vytvářet vztahy mezi tabulkami a pracovat s daty bez nutnosti instalace nebo serveru.

### Hlavní funkce

- Vytváření více tabulek v jedné databázi
- 9 různých typů polí včetně vztahů mezi tabulkami
- Složená pole pro dynamické názvy záznamů
- Filtrování a vyhledávání v záznamech
- Import a export dat ve formátech CSV a TSV
- Generování textu ze záznamů pomocí šablon
- Automatické ukládání do prohlížeče
- Podpora Markdown v textových polích
- Kompletně offline funkčnost
- Dvojjazyčné rozhraní (čeština/angličtina)

### Formát souboru

Aplikace používá vlastní formát `.jsondb` - lidsky čitelný JSON soubor obsahující strukturu i data databáze.

---

## Začínáme

### První spuštění

1. Otevřete [online editor](https://mrt.site44.com/database-editor.html) / nebo po stažení Otevřete soubor `database-editor.html` v moderním webovém prohlížeči (Chrome, Firefox, Edge, Safari)
2. Aplikace se spustí s prázdnou databází nazvanou "Nová databáze"
3. Automaticky se zobrazí karta **⚙️ Správa**

### Vytvoření první databáze

1. V kartě **Správa** → podkarta **Databáze** zadejte název vaší databáze
2. Přejděte na podkartu **Tabulky** a klikněte **Přidat tabulku**
3. Pojmenujte tabulku (např. "Kontakty") a klikněte **Uložit**
4. Klikněte na tlačítko **Pole** u vytvořené tabulky
5. Přidejte potřebná pole (např. Jméno, Email, Telefon)
6. Označte jedno pole jako **Primární** - bude sloužit jako název záznamu
7. Klikněte na kartu s názvem tabulky v horní liště
8. Přidávejte záznamy tlačítkem **➕ Přidat záznam**

### Uložení a načtení databáze

| Akce | Popis |
|------|-------|
| **Nová** | Vytvoří novou prázdnou databázi (pozor, smaže aktuální data) |
| **Načíst** | Otevře existující soubor `.jsondb` z disku |
| **Uložit** | Stáhne databázi jako soubor `.jsondb` |
| **Kopírovat JSON** | Zkopíruje celou databázi do schránky |
| **Vložit JSON** | Načte databázi ze schránky (nebo otevře okno pro vložení na mobilech) |

### Automatické ukládání

Aplikace automaticky ukládá stav databáze do úložiště prohlížeče. Po obnovení stránky nebo zavření a znovuotevření prohlížeče najdete data tak, jak jste je zanechali.

⚠️ **Důležité:** Pro trvalé uložení vždy použijte tlačítko **Uložit** a stáhněte soubor `.jsondb`. Úložiště prohlížeče může být vymazáno při čištění historie nebo v anonymním režimu.

---

## Rozhraní aplikace

### Hlavička

Horní část obrazovky obsahuje:

- **Editor databáze** - název aplikace
- **Nová** - vytvoří novou prázdnou databázi
- **Načíst** - načte databázi ze souboru
- **Uložit** - stáhne databázi jako soubor
- **Kopírovat JSON** - zkopíruje databázi do schránky
- **Vložit JSON** - načte databázi ze schránky
- **Jazyk** - přepínač mezi češtinou (CS) a angličtinou (EN)

### Karty tabulek

Pod hlavičkou se nachází řada karet:

- **Karty jednotlivých tabulek** - kliknutím zobrazíte data tabulky
- **⚙️ Správa** - nastavení databáze, správa tabulek a nástroje

Aktivní karta je zvýrazněna.

### Titulek okna

Titulek okna prohlížeče zobrazuje:
- Název databáze
- Název aktuálně zobrazené tabulky

Formát: `Databáze: [název] | [tabulka]`

---

## Správa databáze

Karta **⚙️ Správa** obsahuje tři podkarty:

### Podkarta Databáze

Obsahuje:
- **Název databáze** - textové pole pro změnu názvu
- **Statistiky** - přehled počtu tabulek a celkového počtu záznamů

### Podkarta Tabulky

Seznam všech tabulek v databázi. U každé tabulky se zobrazuje:
- Název tabulky
- Počet polí
- Počet záznamů

**Tlačítka u každé tabulky:**

| Tlačítko | Akce |
|----------|------|
| ▲ | Přesune tabulku nahoru |
| ▼ | Přesune tabulku dolů |
| **Pole** | Zobrazí a umožní upravit definice polí |
| ✏️ | Přejmenuje tabulku |
| 🗑️ | Smaže tabulku včetně všech dat |

**Přidání nové tabulky:**
1. Klikněte **Přidat tabulku**
2. Zadejte název
3. Klikněte **Uložit**

### Podkarta Nástroje

Obsahuje **Generátor textu** - viz sekce [Generátor textu](#generátor-textu).

---

## Práce s tabulkami

### Vytvoření tabulky

1. Přejděte na **⚙️ Správa** → **Tabulky**
2. Klikněte **Přidat tabulku**
3. Zadejte název tabulky
4. Klikněte **Uložit**

Nová tabulka se objeví v seznamu a jako nová karta.

### Přejmenování tabulky

1. Klikněte na ✏️ u tabulky
2. Upravte název
3. Klikněte **Uložit**

### Smazání tabulky

1. Klikněte na 🗑️ u tabulky
2. Potvrďte smazání v dialogu

⚠️ **Varování:** Smazání tabulky je nevratné a odstraní všechna data i definice polí. Před smazáním si databázi uložte.

### Změna pořadí tabulek

Použijte šipky ▲ a ▼ pro přesunutí tabulky v seznamu. Pořadí určuje pořadí karet v horní liště.

---

## Definice polí

### Zobrazení polí tabulky

1. V **⚙️ Správa** → **Tabulky** klikněte **Pole** u požadované tabulky
2. Zobrazí se karta **Pole tabulky** se seznamem všech polí

### Přidání pole

1. Klikněte **Přidat pole**
2. Vyplňte **Název pole**
3. Vyberte **Typ pole** (viz níže)
4. Podle typu vyplňte další nastavení
5. Volitelně zaškrtněte:
   - **Primární (název záznamu)** - hodnota tohoto pole bude reprezentovat záznam
   - **Povolit filtrování** - zobrazí filtr pro toto pole v zobrazení tabulky
   - **Seskupovat****: V tavulce se výsledky seskupují podle pole, lze sbalit a rozbalit
6. Klikněte **Uložit**

### Typy polí

#### Text

Jednořádkové textové pole pro krátké texty (jména, názvy, kódy).

#### Víceřádkový text / Markdown

Víceřádkové textové pole s podporou formátování Markdown. Při zobrazení záznamu se text renderuje jako formátovaný.

**Podporované formátování:**
- `# Nadpis 1`, `## Nadpis 2`, `### Nadpis 3`
- `**tučný text**`
- `*kurzíva*`
- `- položka seznamu` nebo `* položka seznamu`
- `1. číslovaný seznam`
- `` `inline kód` ``
- ` ``` blok kódu ``` `
- `> citace`
- `[text odkazu](URL)`
- `---` horizontální čára

#### Číslo

Numerické pole pro celá čísla i desetinná čísla. Umožňuje správné řazení podle hodnoty.

#### Datum

Pole s výběrem data pomocí kalendáře. Data se ukládají ve formátu ISO (YYYY-MM-DD) a zobrazují v lokálním formátu.

#### Ano/Ne

Zaškrtávací pole pro logické hodnoty (boolean). Zobrazuje se jako "Ano" nebo "Ne".

#### Výběr ze seznamu

Rozbalovací nabídka s předdefinovanými hodnotami.

**Nastavení:**
- V poli **Hodnoty (oddělené čárkou)** zadejte možnosti
- Příklad: `Nízká,Střední,Vysoká,Kritická`

#### URL

Odkaz ve formě URL adresy, po zadání je klikatelný odkaz.

#### Složený

Vypočítané pole kombinující hodnoty jiných polí pomocí šablony.

**Nastavení:**
1. Klikejte na tlačítka s názvy polí pro vložení do šablony
2. Nebo ručně pište šablonu s placeholdery `{Název pole}`

**Příklad šablony:** `{Jméno} {Příjmení} ({Oddělení})`

**Vlastnosti:**
- Hodnota se počítá automaticky při zobrazení
- Pole nelze přímo editovat
- Může být označeno jako primární pro dynamické názvy záznamů
- Podporuje hodnoty z polí typu: text, číslo, datum, ano/ne, výběr, nadřazený záznam

#### Nadřazený záznam

Vytváří vztah typu N:1 (mnoho ku jedné) na záznamy v jiné tabulce.

**Nastavení:**
- Vyberte **Cílová tabulka** - tabulka, ze které se vybírá nadřazený záznam

**Použití:**
- Při editaci záznamu vyberete nadřazený záznam z rozbalovacího seznamu
- Tlačítko ➕ umožňuje vytvořit nový nadřazený záznam přímo při editaci
- V zobrazení záznamu je odkaz na nadřazený záznam klikatelný

#### Podřízené záznamy

Zobrazuje seznam záznamů z jiné tabulky, které na tento záznam odkazují (inverzní vztah).

**Nastavení:**
- **Cílová tabulka** - tabulka obsahující podřízené záznamy
- **Pole odkazující zpět** (volitelné) - konkrétní pole typu "Nadřazený záznam" v cílové tabulce

**Vlastnosti:**
- Toto pole se needituje přímo
- Záznamy se zobrazují automaticky na základě vztahů
- Ve výchozím stavu je skryto v tabulkovém zobrazení (lze zapnout)

### Úprava pole

1. Klikněte na ✏️ u pole
2. Upravte nastavení
3. Klikněte **Uložit**

### Smazání pole

1. Klikněte na 🗑️ u pole
2. Potvrďte smazání

⚠️ **Varování:** Data v tomto poli budou u všech záznamů nevratně smazána.

### Změna pořadí polí

Použijte šipky ▲ a ▼. Pořadí ovlivňuje:
- Pořadí sloupců v tabulce
- Pořadí polí ve formuláři pro editaci
- Pořadí polí v detailu záznamu

---

## Práce se záznamy

### Zobrazení záznamů

Klikněte na kartu tabulky v horní liště. Zobrazí se:

1. **Název tabulky** a tlačítka Export/Import/Přidat záznam
2. **Vyhledávací pole** a filtry
3. **Počet záznamů** (filtrované / celkem)
4. **Tabulka se záznamy** a akcemi
5. **Zobrazení sloupců** (sbalitelná sekce)

### Přidání záznamu

1. Klikněte **➕ Přidat záznam**
2. Vyplňte hodnoty polí ve formuláři
3. Klikněte **Uložit**

**Vytvoření nadřazeného záznamu za běhu:**

Pokud potřebujete vybrat nadřazený záznam, který ještě neexistuje:
1. Klikněte ➕ vedle rozbalovacího seznamu nadřazeného záznamu
2. Vyplňte a uložte nový nadřazený záznam
3. Vrátíte se k původnímu formuláři s automaticky vybraným novým záznamem

### Zobrazení detailu záznamu

Klikněte na:
- Hodnotu primárního pole (název záznamu) v tabulce
- Odkaz na nadřazený/podřízený záznam
- Tlačítko 👁️ v řádku záznamu

**V detailu záznamu vidíte:**
- Všechna pole s hodnotami
- Formátovaný Markdown text
- Klikatelné odkazy na související záznamy
- Tlačítko **Upravit** pro přechod do editace

### Úprava záznamu

1. Klikněte ✏️ u záznamu v tabulce, nebo
2. V detailu záznamu klikněte **Upravit**
3. Změňte hodnoty ve formuláři
4. Klikněte **Uložit**

### Smazání záznamu

1. Klikněte 🗑️ u záznamu
2. Potvrďte smazání v dialogu

⚠️ Smazání záznamu může ovlivnit záznamy v jiných tabulkách, které na něj odkazují.

---

## Filtrování a vyhledávání

### Fulltextové vyhledávání

Pole **Hledat...** nad tabulkou prohledává všechna pole záznamu.

**Vlastnosti:**
- Hledání není citlivé na velikost písmen
- Hledá kdekoli v textu (nejen na začátku)
- Výsledky se aktualizují okamžitě při psaní
- Prohledává i hodnoty v polích, která nejsou zobrazena

### Filtry

U polí s povoleným filtrováním se zobrazí rozbalovací nabídka.

**Možnosti filtru:**
- **Všechny hodnoty** - zobrazí všechny záznamy (bez filtru)
- **(bez hodnoty)** - zobrazí záznamy s prázdným polem
- **Konkrétní hodnota** - zobrazí pouze záznamy s touto hodnotou

**Kombinace filtrů:**
- Filtry lze kombinovat s vyhledáváním
- Při použití více filtrů se zobrazí pouze záznamy splňující všechny podmínky (logické AND)

### Řazení

Klikněte na záhlaví sloupce pro seřazení:
- **První klik:** vzestupně (▲ za názvem)
- **Druhý klik:** sestupně (▼ za názvem)
- **Třetí klik:** výchozí pořadí

**Řazení podle typu pole:**
- Text: abecedně
- Číslo: numericky
- Datum: chronologicky
- Ano/Ne: Ne před Ano
- Složené pole: podle vypočítané textové hodnoty

### Viditelnost sloupců

1. Klikněte na **Zobrazení sloupců** pod tabulkou pro rozbalení
2. Zaškrtněte nebo odškrtněte sloupce
3. Změny se projeví okamžitě

**Poznámky:**
- Pole typu **Podřízené záznamy** je ve výchozím stavu skryté
- Nastavení viditelnosti se ukládá s databází

---

## Import a export dat

### Export do CSV/TSV

1. V zobrazení tabulky klikněte **📤 Export**
2. Vyberte formát:
   - **CSV (čárka)** - hodnoty oddělené čárkou
   - **TSV (tabulátor)** - hodnoty oddělené tabulátorem
3. Data se zobrazí v textovém poli
4. Použijte:
   - **📋 Kopírovat** - zkopíruje do schránky
   - **💾 Uložit soubor** - stáhne jako soubor .csv nebo .tsv

**Export obsahuje:**
- Záhlaví s názvy polí
- Všechny záznamy tabulky
- Pole typu Podřízené záznamy a Složený se neexportují (jsou vypočítané)

### Import z CSV/TSV

1. V zobrazení tabulky klikněte **📥 Import**
2. Vyberte formát (CSV nebo TSV)
3. Načtěte data:
   - **Načíst soubor** - vyberte soubor z disku, nebo
   - **Vložte data** - přímo do textového pole
4. Zaškrtněte **První řádek obsahuje názvy sloupců** pokud ano
5. Klikněte **Importovat**

**Chování importu (Upsert):**
- Sloupce se párují podle názvu s existujícími poli
- Pokud existuje záznam se stejnou hodnotou primárního pole → **aktualizuje se**
- Pokud záznam neexistuje → **vytvoří se nový**
- Po importu se zobrazí počet nových a aktualizovaných záznamů

**Tipy pro import:**
- Názvy sloupců v CSV musí přesně odpovídat názvům polí
- Pro pole Ano/Ne použijte: true/false, 1/0, ano/ne, yes/no
- Pro pole Datum použijte formát YYYY-MM-DD
- Pole Nadřazený záznam vyžaduje ID existujícího záznamu

---

## Generátor textu

Generátor textu umožňuje vytvořit hromadný textový výstup ze záznamů pomocí šablony.

### Použití

1. Přejděte na **⚙️ Správa** → **Nástroje**
2. V sekci **Generátor textu**:
   - Vyberte tabulku
   - Klikejte na tlačítka polí pro vložení do šablony
   - Nebo pište šablonu ručně s placeholdery `{Název pole}`
3. Vyberte zdroj dat:
   - **Všechny záznamy** - použije všechny záznamy v tabulce
   - **Filtrované záznamy** - použije pouze záznamy odpovídající aktuálnímu filtru
4. Klikněte **Generovat**
5. Výsledek zkopírujte tlačítkem **Kopírovat**

### Příklady šablon

**Email seznam:**
```
{Jméno} <{Email}>
```

**Štítky:**
```
{Jméno} {Příjmení}
{Ulice}
{PSČ} {Město}
---
```

**CSV export vlastního formátu:**
```
"{Jméno}";"{Příjmení}";"{Telefon}"
```

**HTML seznam:**
```
<li><a href="mailto:{Email}">{Jméno} {Příjmení}</a></li>
```

### Podporované placeholdery

- `{Název pole}` - hodnota textového, číselného pole
- Pro Ano/Ne pole: zobrazí "Ano" nebo "Ne"
- Pro Datum: zobrazí v lokálním formátu
- Pro Nadřazený záznam: zobrazí název nadřazeného záznamu
- Pro neexistující pole: placeholder zůstane nezměněn

---

## Tipy a triky

### Efektivní struktura databáze

1. **Používejte vztahy** místo opakování dat
   - Špatně: V každém kontaktu opakovat celou adresu firmy
   - Dobře: Tabulka Firmy + tabulka Kontakty s odkazem na firmu

2. **Nastavte primární pole** u každé tabulky
   - Usnadňuje identifikaci záznamů
   - Zobrazuje se v odkazech a seznamech

3. **Používejte složená pole** pro komplexní názvy
   - Příklad: `{Příjmení}, {Jméno}` jako primární pole

4. **Zapněte filtrování** pouze u polí, kde má smysl
   - Typicky: Stav, Kategorie, Typ, Priorita
   - Není vhodné pro: Poznámky, Popis, unikátní hodnoty

### Zálohování

- Pravidelně ukládejte databázi tlačítkem **Uložit**
- Uchovávejte více verzí souborů `.jsondb`
- Automatické ukládání v prohlížeči je pouze dočasné

### Práce na mobilu

- Aplikace je responzivní a funguje na mobilních zařízeních
- Pro vložení JSON na mobilu se automaticky otevře textové pole (Clipboard API často nefunguje)
- Použijte horizontální scroll pro široké tabulky

### Přenos mezi zařízeními

1. **Pomocí souboru:** Uložte `.jsondb`, přeneste, načtěte
2. **Pomocí schránky:** Kopírovat JSON → přenést text → Vložit JSON

---

## Řešení problémů

### Data se neukládají

**Příčina:** Automatické ukládání do prohlížeče může selhat v anonymním režimu nebo při plném úložišti.

**Řešení:** Vždy používejte tlačítko **Uložit** pro stažení souboru `.jsondb`.

### Nelze vložit JSON ze schránky (mobil)

**Příčina:** Mobilní prohlížeče často blokují Clipboard API.

**Řešení:** Aplikace automaticky otevře textové pole, kam můžete JSON vložit ručně (dlouhý stisk → Vložit).

### Import nefunguje správně

**Možné příčiny a řešení:**

1. **Špatné názvy sloupců** - Názvy musí přesně odpovídat názvům polí (včetně diakritiky)
2. **Špatný formát** - Zkontrolujte, zda používáte správný oddělovač (čárka vs. tabulátor)
3. **Chybějící záhlaví** - Zaškrtněte/odškrtněte "První řádek obsahuje názvy sloupců"

### Záznamy zmizely po importu

**Příčina:** Import používá upsert logiku - záznamy se stejným primárním polem se přepíší.

**Řešení:** Před importem si uložte zálohu databáze.

### Vztahy mezi tabulkami nefungují

**Kontrolní seznam:**
1. Pole typu "Nadřazený záznam" má nastavenou správnou cílovou tabulku
2. V cílové tabulce existují záznamy
3. Pro pole "Podřízené záznamy" existuje odpovídající pole "Nadřazený záznam" v druhé tabulce

### Aplikace je pomalá

**Možné příčiny:**
- Příliš mnoho záznamů (tisíce) v jedné tabulce
- Příliš mnoho sloupců zobrazených najednou
- Starší prohlížeč nebo zařízení

**Řešení:**
- Skryjte nepotřebné sloupce
- Rozdělte data do více tabulek
- Použijte moderní prohlížeč

---

## Podpora

Editor databáze je open-source aplikace. 

**Formát souboru:** Specifikace formátu `.jsondb` je dostupná v dokumentu `JSONDB-FORMAT.md` včetně JSON Schema pro validaci.

---

*Poslední aktualizace: 2025*
