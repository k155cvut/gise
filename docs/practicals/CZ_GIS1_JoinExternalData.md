---
icon: material/numeric-4-box
title: Cvičení 4
---

# Práce s externími daty (Excel, CSV), join

## Cíl cvičení

Na rozdíl od předchozích úloh, kdy byla práce zaměřena na práci s poskytnutými prostorovými daty uloženými v geodatabázi či formátu SHP, se následující úloha soustředí na možnosti importu externích tabulárních dat a jejich připojení na prostorová data.

Prostřednictvím společného pole (klíče) lze přiřadit záznamy v jedné tabulce se záznamy v jiné tabulce (vrstvě). K vrstvě parcel můžete například přidružit tabulku informací o vlastnictví parcel, protože sdílejí pole identifikace parcely. Tato přidružení můžete vytvořit několika způsoby, včetně dočasného spojení či vytvoření trvalejších tříd vztahů uvnitř geodatabáze. Spojení může být také založeno na prostorovém umístění, jak bylo demonstrováno ve cvičení 3.

## Základní pojmy

[<span>:material-open-in-new: pro.arcgis.com</span><br>Join the attributes from a table](https://pro.arcgis.com/en/pro-app/latest/help/data/tables/joins-and-relates.htm#GUID-39C9610A-6A73-4985-ADB8-7354EA9DB8BF){ .md-button .md-button--primary .url-name target="_blank"}
[<span>:material-open-in-new: pro.arcgis.com</span><br>Join data by location (spatially)](https://pro.arcgis.com/en/pro-app/latest/help/data/tables/joins-and-relates.htm#GUID-7B11EAA4-35E0-4B8D-AFB6-4A435761574B){ .md-button .md-button--primary .url-name target="_blank"}
[<span>:material-open-in-new: pro.arcgis.com</span><br>Remove join](https://pro.arcgis.com/en/pro-app/latest/help/data/tables/joins-and-relates.htm#ESRI_SECTION1_6507320BCB1E45219A88F1AA0A24F7B9){ .md-button .md-button--primary .url-name target="_blank"}
{: align=center style="display:flex; justify-content:center; align-items:center; column-gap:20px; row-gap:10px; flex-wrap:wrap;"}


## Použité datové podklady

- Polygony [městských částí](../assets/cviceni4/MESTSKECASTI.zip) Prahy
- Tabulka pražských [poboček Městské policie](../assets/cviceni4/objekty_MPP.xlsx) ve fromátu XLSX

Pozn. Data jsou dostupná rovněž na S:\K155\Public\155GIS1

## Pracovní postup

**1.** Přidáme polygonovou vrstvu městských částí Prahy do projektu, prohlédneme atributovou tabulku, seznámíme se s daty. V nastavení projektu zvolíme souřadnicový systém S-JTSK (EPSG:5514).

**2.** Dále otevřeme tabulku poboček městské policie v Praze v MS Excel. Jelikož tabulka obsahuje také sloupce se souřadnicemi v S-JTSK, bude možné ji připojit do projektu a vykreslit. Zavřeme Excel a pomocí *Add Data* a *XY Point Data* vyhledáme tabulku (je nutné vybrat přímo list souboru XLSX) viz obrázek. Souřadnice X, Y asociujeme s příslušnými poly tabulky (propíší se pravděpodobně automaticky) a zvolíme správný souřadnicový systém (EPSG:5514).

<figure markdown>
  ![AddXYData](../assets/cviceni4/addXYData.png)
  <figcaption>Přidání bodových dat do projektu</figcaption>
</figure>

<figure markdown>
  ![XYTabletoPoint](../assets/cviceni4/XYTabletoPoint.png)
  <figcaption>Dialogové okno pro nahrání bodových dat se souřadnicemi z tabulky</figcaption>
</figure>

**3.** V této fázi máme dvě vrstvy: bodovou (pobočky MPP) a polygonovou (MČ Prahy). Pro zopakování bude nejprve vhodné vyzkoušet prostorové připojení prvků. Např. bychom mohli zjistit, kolik poboček MPP se nachází v každé MČ Prahy a dále, jaká je jejich celková kapacita, jinými slovy, kolik příslušníků Městské policie spadá do každé městské části. Ačkoliv jsou dotazy dva, je možné je zpracovat najednou. Pravým kliknutím na vrstvu MČ vyvoláme přes *Joins and Relates* a *Add Spatial Join* dialogové okno. Defaultní nastavení je nutné upravit. Za prvé, v sekci *Output Fields* lze definovat pravidla pro připojení jednotlivých polí z tabulky. Vzhledem k tomu, že úkolem je zjistit celkovou kapacitu, lze všechna pole kromě kapacity smazat a pro pole kapacita vybrat z nabídky pravidel (*Merge Rule*) sumu (viz obrázek). Za druhé je potřeba zaškrtnout parametr *Keep All Target Features*, aby byly zachovány všechny původní prvky, včetně takových, ke kterým nebude prostorově připojen žádný prvek.

<figure markdown>
  ![SumKapacita](../assets/cviceni4/SumKapacita.png)
  <figcaption>Atributové pravidlo u prostorového připojení dat</figcaption>
</figure>

**4.** Tímto způsobem se obohatí původní vrstva MČ o nová data dle definovaných pravidel. Po otevření atributové tabulky jsou nově připojené záznamy přidruženy z pravé strany. Zajímavý atribut, který se vytváří automaticky pro každý *Spatial Join*, představuje *Join_Count*. Ten obsahuje počet prvků, které byly k danému (původnímu) prvku připojeny (zde se jedná o počet poboček MPP v dané MČ). Tímto způsobem je např. možné zjistit:

>>**a.** která MČ disponuje nejvíce pobočkami MPP

>>**b.** ve kterých MČ není žádná pobočka MPP

>>**c.** ve které MČ pracuje nejvíce pracovníků městské policie

**5.** K vrstvě dat je všakmožné připojit data i na základě jiného vztahu než prostorového. Např. bychom mohli zjistit, kolik policistů v dané MČ připadá na 100 místních obyvatel. Nejprve je nutné získat data: největším poskytovatelem otevřených statistických dat v ČR je Český statistický úřad. Na jeho webu v sekci [veřejná databáze](https://vdb.czso.cz/) otevřeme *vlastní výběr* a v tabulce *ukazatele* vybereme postupně *Sčítání lidu, domů a bytů 2021 – Obyvatelstvo – Počet obyvatel s obvyklým pobytem – celkem*. Vybraný ukazatel se zobrazí v pravé části okna a postoupíme dále k definici území. Zde zvolíme *městské části* a výběr omezíme filtrem na Prahu (tzn. výběr zahrne pouze 57 MČ Prahy). V dalším kroku zatrhneme nejnovější období a v interaktivním náhledu struktury tabulky prohodíme pozice *území* a *ukazatele* tak, aby MČ byly v řádcích a ukazatel ve sloupci. V posledním kroku se zobrazí náhled tabulky (viz obrázek) a data lze exportovat ve formátu XLSX (pomocí ikony diskety; není nutné zahrnouvat poznámky k textu ani hodnotám).

<figure markdown>
  ![VDB](../assets/cviceni4/VDB.png)
  <figcaption>Náhled na první řádky vygenerované tabulky z veřejné databáze ČSÚ</figcaption>
</figure>

**6.** Po stažení tabulky s demografickým údaji MČ Prahy je vhodné data zkontrolovat a upravit. Soubor obsahuje tři listy, přičemž jsou zapsána hned na prvním (DATA). Ideální postup na úpravu dat zní následovně: vložit nový list, označit všechny buňky tabulky (57 MČ a příslušné počty obyvatel), překopírovat označené do nového listu (pomocí *Vložit jinak – Hodnoty*), přidat první řádek a pojmenovat sloupce (např. NAZEV_MC a POCET_OBYV).

Dále je nutná rozvaha, na základě čeho tabulární data propojit s prostorovými. V polygonové vrstvě MČ jsou obsaženy 2 varianty názvů, které se však neshodují s názvem v tabulce. Nicméně není problém tabulku upravit: pomocí funkce *najít a nahradit* (klávesová zkratka CTRL + H) lze upravit názvy MČ. Konkrétně odstranit výrazy "městká část " a " (obec Praha)". Pozor, důležité je vždy zahrnout mezeru za, resp. před daným výrazem. Tímto postupem lze tedy vyhledat všechny výskyty daných výrazů a hromadně je nahradit prázdným řetězcem (do pole *nahradit* nevyplníte nic).

Nakonec ještě pro jistotu změňte formát buněk s počty obyvatel na *číslo* (datový typ buněk lze změnit případně i v ArcGIS Pro). Takto připravená data uložte jako soubor CSV UTF-8.

**7.** Následuje připojení tabulárních dat k vrstvě MČ. Znovu pomocí volby *Joins and Relates* a tentokrát *Add Join* otevřeme dialogové okno. *Input table* představuje vrstvu, ke které se data připojují, *Target table* označuje připojovanou tabulku. *Join field* pro každou z tabulek představuje atribut, na základě kterého se budou tabulky připojovat.

???+ note "&nbsp;<span style="color:#448aff">Pozn.</span>"
      Pokud připojujeme tabulky ve smyslu 1:1, jako ideální *Input/Target Join field* volte unikátní identifikátor s datovým typem integer. Textové řetězce mohou být při propojování tabulek zrádné, některé znaky nemusí být podporovány a řetězce musí být 100% shodné (např. mezera je platný znak a může způsobit nepřipojení prvků).

Výběr *Target Join field* nenabízí mnoho možností: pouze název MČ a počet obyvatel. Vzhledem k tomu, že ČSÚ v datové sadě neposkytuje kódy MČ, bude nutné připojit záznamy na základě textových řetězců, proto zvolíme *MC_NAZEV*. V atributové tabulce MČ se nachází dvojice různých názvů: *NAZEV_1* a *NAZEV_MC*. Vybereme tedy jeden z nich jako *Input Join field*.

<figure markdown>
  ![Join](../assets/cviceni4/AddJoin.png)
  <figcaption>Dialogové okno pro připojení tabulky</figcaption>
</figure>

V této fázi je vždy rozumné provést validaci pomocí *Validate Join*. Jedná se o rychlou kontrolu, resp. report o performanci připojení. Pozornost věnujte zejména posledním řádkům, ze kterých vyplývá, kolik záznámů bylo připojeno (v našem případě je nutné připojit k 57 MČ 57 záznamů z ČSÚ – viz obrázek).

<figure markdown>
  ![Validate](../assets/cviceni4/ValidateJoin.png)
  <figcaption>Validace připojení tabulky</figcaption>
</figure>

**8.** Nyní si lze prohlédnout atributovou tabulku MČ, ke které byla pomocí *Spatial Join* připojena bodová vrstva poboček MPP a přes *Add Join* tabulární data s počtem obyvatel. Pro výpočet úlohy s počtem policistů na 100 obyvatel je nutné vytvořit nové pole atributové tabulky (s názvem např. *PREPOCET*), ve kterém bude kýžená hodnota vypočtena pomocí *Calculate Field* a zadáním správného výrazu, který kombinuje data ze všech připojených zdrojů (celková kapacita, počet obyatel).

<figure markdown>
  ![Calculate](../assets/cviceni4/Calculate.png)
  <figcaption>Zadání výrazu pro výpočet počtu policistů na 100 obyvatel MČ</figcaption>
</figure>

???+ note "&nbsp;<span style="color:#448aff">Pozn.</span>"
      Pokud si přejeme vrstvu s připojenými daty trvale uložit např. do geodatabáze, lze po pravém kliknutí na vrstvu vybrat *Data* a funkci *Export Features*. Takto exportovaná data budou o nové záznamy obohacena, tzn. budou obsahovat veškerá původně připojená data. Naopak, pokud připojená data sloužila např. pouze k výpočtu nového atributu a pro další práci již nejsou potřeba, je vhodné *joiny* odstranit pomocí *Joins and relates* a *Remove Join* (s následným výběrem daného joinu) či *Remove all joins* pro kompletní odebrání připojených dat.

**9.** Výsledek však nemusí zůstat jen u čtení tabulárních dat; relativní data vztažená k administrativním dílům lze vizualizovat pomocí kartografické metody zvané kartogram
(více o metodách tematické kartografie se dozvíte v předmětech Kartografie 2 a Kartografie 3 viz [samostatná dokumentace](../kar2/kartogram)). Po pravém kliknutí na vrstvu
a kliknutí na *Symbology* lze změnit *Primary symbology* na *Graduated Colors* z kategorie vizualizace kvantitativních dat. Pak stačí zvolit atribut, který bude pro vizualizaci
použit (případně další parametry, podrobněji viz zmíněná dokumentace kartografických předmětů).

Kompozici možno doplnit o názvy; v panelu *Labeling* stačí aktivovat popis a vybrat atribut, kterým budou polygony popsány. Opět se jedná o téma, kterému se věnuje detailně [samostatná dokumentace](../kar2/popisy).
      
## Úlohy k procvičení

!!! task-fg-color "Úlohy"

    K řešení následujích úloh použijte datovou sadu [ArcČR
    500](../../data/#arccr-500) verzi 3.3 dostupnou na disku *S* ve složče
    ``K155\Public\data\GIS\ArcCR500 3.3``. Zde také najdete souboru s
    popisem dat ve formátu PDF. Další datové vrstvy, která budete
    potřebovat pro vyřešení následujících úloh, jsou dostupné ke stažení
    jako [zip archiv](https://geo.fsv.cvut.cz/vyuka/155gis1/geodata/gis1-cviceni04.zip).

    1. Zjistěte kolik kamer pro měření rychlosti se nachází na území hlavního města Prahy?

    2. Určete celkovou výměru budov m^2^. Vrstvu budov je třeba
       transformovat na 2 měřené body podobnostní transformací

    3. Kolik vodojemů leží na území obcí pro které platí, že leží na
       hranici mapového listu TM100 a mají statuskod roven 3?
