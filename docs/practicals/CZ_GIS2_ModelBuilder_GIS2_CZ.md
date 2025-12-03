---
icon: material/numeric-1-box
title: Cvičení 1
---

<style>
  .md-typeset__scrollwrap {text-align: center;}                                                      /* Zarovnani tabulek na stred */
  /* tbody {width: 100%;display: table;}                                                             /* Roztazeni tabulek na celou sirku */
  h2 {font-weight:700 !important;}                                                                   /* Pokus – zmena formatu nadpisu 2 */
  figcaption {font-size:12px;margin-top:5px !important;text-align:center;line-height:1.2em;}         /* Formatovani Popisku obrazku */
  hr.l1 {background-color:var(--md-primary-fg-color);height:2px;margin-bottom:3em !important;}       /* Formatovani Break Line – LEVEL 1 */
  /* img,iframe {box-shadow: 0 10px 16px 0 rgba(0,0,0,0.2),0 6px 20px 0 rgba(0,0,0,0.2) !important;} /* Stin pod obrazky a videi */
  img,iframe {filter:drop-shadow(0 10px 16px rgba(0,0,0,0.2)) drop-shadow(0 6px 20px rgba(0,0,0,0.2)) !important; object-fit:contain;} /* Stin pod obrazky a videi */

  /* TLACITKA */
  .md-button {text-align:center;transition: all .1s ease-in-out !important;}  /* Button – zarovnani textu */
  .md-button:hover {transform: scale(1.04);opacity:.8;background-color:var(--md-primary-fg-color) !important;border-color:var(--md-primary-fg-color) !important;color:var(--md-primary-bg-color) !important;/*filter: brightness(80%);*/}            /* Button Hover – animace zvetseni a zmeny barvy */
  .md-button:focus {opacity:.8;background-color:var(--md-primary-fg-color) !important;border-color:var(--md-primary-fg-color) !important;color:var(--md-primary-bg-color) !important;}                                                                /* Button Focus – stejny vzhled jako hover */
  .url-name {line-height:1.2;/*padding-top:5px !important;*/}                 /* Button s URL */
  .url-name span:first-child {font-size:.7em; font-weight:300;}               /* Button s URL – format*/
  .url-name span.twemoji {vertical-align:-0px;}                               /* Button s URL – zarovnani ikony*/
  .md-button.button_smaller {font-size:smaller; padding:1px 5px;}             /* Mensi button (bez URL) */

  /* FLEXBOXY */
  .process_container {display:flex !important; justify-content:center; align-items:center; column-gap:calc((100vw * 0.03) - 6px);} /* Kontejner pro content = FlexBox */
  .process_container div {display:flex;}                                                                                           /* Obsah (obrazky a sipky) */
  .process_container .process_icon {width:/*40px*/calc((100vw * 0.01) + 25px); flex-shrink:0;filter:none !important;}              /* Velikost ikony (bacha na mobily) */
  .process_container img {max-height:150px;}                                                                                       /* Obrazky ve flexboxech maji maximalni vysku */

  code.AGPF {border:2px solid var(--md-primary-fg-color);padding:.1em .4em !important;/*transition: all .1s ease-in-out !important; display:inline-block !important;*/}
  code.AGPF .twemoji {vertical-align:-10% !important;}
</style>

<!-- Definice sipky do FlexBoxu (pro referenci) – UZ NENI TREBA
<svg style="display: none" version="2.0">
  <defs>
    <symbol id="rect-arrow-right" viewBox="0 0 24 24">
      <path d="M5,21A2,2 0 0,1 3,19V5A2,2 0 0,1 5,3H19A2,2 0 0,1 21,5V19C21,20.11 20.1,21 19,21H5M6,13H14.5L11,16.5L12.42,17.92L18.34,12L12.42,6.08L11,7.5L14.5,11H6V13Z"
        style="fill:var(--md-primary-fg-color)" />
    </symbol>
    <symbol id="caret-right" height="1em" viewBox="0 0 256 512">
      <path d="M246.6 278.6c12.5-12.5 12.5-32.8 0-45.3l-128-128c-9.2-9.2-22.9-11.9-34.9-6.9s-19.8 16.6-19.8 29.6l0 256c0 12.9 7.8 24.6 19.8 29.6s25.7 2.2 34.9-6.9l128-128z" style="fill:var(--md-primary-fg-color)" />
    </symbol>
  <defs>
</svg> -->

# ModelBuilder, Batch processing

Ve cvičení se naučíte
{: align=center style="font-size: 1.25rem; font-weight: bold; margin-bottom: 10px;"}

<style>
    .smaller_padding li {padding:.4rem .8rem !important;}
    .primary_color {color:var(--md-primary-fg-color);}
</style>

<div class="grid cards smaller_padding" markdown>

-   :octicons-ai-model-16:{ .xxxl .middle }
    {.middle style="display:table-cell;min-width:40px;padding-right:.8rem;"}

    pracovat s nástrojem __ModelBuilder__ pro __automatizaci__ prostorové analýzy v ArcGIS Pro
    {.middle style="display:table-cell;line-height:normal;"}

-   :material-cog:{ .xxxl .middle }
    {.middle style="display:table-cell;min-width:40px;padding-right:.8rem;"}
    
    __dávkové__ spouštění geoprocessingových funkcí
    {.middle style="display:table-cell;line-height:normal;"}
</div>

<hr class="l1">

## Základní pojmy

- [**ModelBuilder**](https://pro.arcgis.com/en/pro-app/latest/help/analysis/geoprocessing/modelbuilder/what-is-modelbuilder-.htm)
- [**Batch geoprocessing**](https://pro.arcgis.com/en/pro-app/latest/help/analysis/geoprocessing/basics/batch-geoprocessing.htm)

### ModelBuilder

ModelBuilder slouží jako vizuální programovací jazyk pro vytváření geoprocesních pracovních postupů. Tyto postupy automatizují a dokumentují vaše prostorové analýzy a procesy správy dat. Model je zobrazen jako diagram, který spojuje sekvenci geoprocessingových funkcí a jiných nástrojů. Výstup jedné funkce slouží jako vstup do navazující.

### Batch geoprocessing

ArcGIS Pro poskytuje efektivní možnost automatizace opakujících se úkolů pomocí dávkového režimu nástrojů pro geoprocessing. Tato funkce umožňuje uživatelům spouštět nástroje s různými vstupními datovými sadami nebo parametry bez nutnosti opakovaně interagovat s aplikací.

<figure markdown>
  ![](../assets/cviceni1/BatchProcessing.png){ width="400" }
  <figcaption>Dávkový výpočet</figcaption>
</figure>

Pro ilustraci můžeme použít nástroj "Clip" pro oříznutí několika datových sad do zájmové oblasti. Postupujte následovně:

## Použité datové podklady

- [Pobočky](../assets/cviceni3/PobockyCP_PlzenskyKraj.zip) České pošty v Plzeňském kraji (bodová vrstva)
- Obce ČR ([ArcČR 500](../../data/#arccr-500), polygonová vrstva)

## Náplň cvičení

### 1. pošty

Představte si, že pracujete jako GIS analytik pro Českou poštu a vaším úkolem je z důvodu úspor navrhnout řešení snížení počtu poboček. Snahou tohoto kroku je však i minimalizace negativních dopadů na obyvatele, proto bylo rozhodnuto o následujících podmínkách, které musíte ve svém návrhu dodržet:

1. Rušení poboček nebude probíhat v obcích s méně než 2500 obyvateli.
2. V obcích nad 2500 obyvatel neklesne počet poboček pod 1.
3. Vzájemná vzdálenost poboček v jedné obci nebude nižší než 3 km vzdušnou čarou.

Jakou finanční úsporu jste schopni svým návrhem zajistit, pokud by provoz jedné pobočky vycházel ročně na 2,5 milionu CZK? Pro zjednodušení budete úlohu řešit pouze v rámci Plzeňského kraje a ke každé pobočce přistupovat rovnocenně.

Pracovní postup najdete ve cvičení 3 předmětu [**GIS1**](https://k155cvut.github.io/gis-1/cviceni/cviceni3/)

Shodný postup budeme aplikovat přímo v ModelBuilderu.

## Pracovní postup

**1.** Založení nového modelu.

Možnost vytvoření nového modelu nalezneme na záložce Analysis.

<figure markdown>
![CO](../assets/cviceni1/MB_Analysis.png){ width="400" }
    <figcaption>Založení modelu</figcaption>
</figure>

Nový model se nám tak přidá do toolboxu našeho projektu a otevře se v novém okně.

<figure markdown>
![CO](../assets/cviceni1/MB_Catalog.png ){ width="900" }
    <figcaption>Nový model</figcaption>
</figure>

**2.** Přidání dat

Data přidáme jako položku do ModelBuideru přetažením vrstvy z panelu obsahu do plátna modelu.

<figure markdown>
![CO](../assets/cviceni1/MB_DragADrop.png){ width="500" }
    <figcaption>Přidání dat do modelu</figcaption>
</figure>

**3.** Výběr obcí v Plzeňském kraji s více než 2500 obyvateli (atributový dotaz) a tvorba samostatné vrstvy selektovaných prvků.

V sekci vložení na záožce ModelBuilderu můžeme z výběru nástrojů vyhledat požadovaný nástroj a buď pomocí dvojkliku nebo přetažením do modelu se nám v modelu graficky zobrazí. Jelikož však nástroj není napojený na stávající model, zobrazuje se šedou barvou.

<figure markdown>
![CO](../assets/cviceni1/MB_SBA.png){ width="500" }
    <figcaption>Výběr prvků atributovým výrazem</figcaption>
</figure>

Pro propojení vstupnách dat s funkcí musíme kliknout na položku dat, na která chceme výběr aplikovat, a přetáhnout kurzor myši na požadovanou funkci a zvolit význam vstupních dat v nástroji. Po propojení se graf vybarví, což znamená, že je aktivní.

![](../assets/cviceni1/MB_connect.png)
![](../assets/cviceni1/MB_connectDone.png)
{: .process_container}

<figcaption>Provázání modelu</figcaption>

Po dvojkliku na nástroj (označený žlutou barvou) se zobrazí jeho konfigurace, tak jak ji známe. Můžeme zde tedy vyplnit podmínky.

<figure markdown>
![CO](../assets/cviceni1/MB_SBAconfig.png){ width="400" }
    <figcaption>Konfigurační panel nástroje</figcaption>
</figure>

Klikneme-li na výsledek operace (zelený) pravým tlačátkem myši, můžeme zvolit, aby se po provedení zobrazil v mapě. Kliknutím pravým tlačítkem myši nad nástroj (žlutý) pak můžeme jednotlivé geoprocesingové nástroje spouštět.

![](../assets/cviceni1/MB_Add2Display.png)
![](../assets/cviceni1/MB_run.png)
{: .process_container}

<figcaption>Spuštění nástroje a přidání výsledku do mapy</figcaption>

Postupně přidáme další geoprocessingové funkce odpovídající cvičení 3 z předmětu GIS1

<figure markdown>
![CO](../assets/cviceni1/MB_full.png){ width="900" }
    <figcaption>Celý model</figcaption>
</figure>

Nakonec můžeme ze vstupních proměnných vytvořit parametry, které bude uživatel moci konfigurovat.

![](../assets/cviceni1/MB_parameter.png)
![](../assets/cviceni1/MB_paramExp.png)
{: .process_container}

<figcaption>Zvolení parametrů</figcaption>

## Úlohy k procvičení

!!! task-fg-color "Úlohy"

    K řešení následujích úloh použijte datovou sadu [ArcČR
    500](../../data/#arccr-500) verzi 3.3 dostupnou na disku *S* ve složce
    ``K155\Public\data\GIS\ArcCR500 3.3``. Pro výpočet úloh využijte Model Builder.

    1. Nalezněte všechny chráněné krajinné oblasti, které se nacházejí do 20 km od dálnice.

    2. Vyberte všechny polygony obcí s počtem obyvatel vyšším než 5000, které patří do Pardubického kraje. Dále zjistěte celkovou rozlohu lesa (v hektarech) na území vybraných obcí.

    3. Vyfiltrujte jednokolejné elektrifikované železnice. Zjistěte, jestli některá ze stanic na jejich trase patří do obce s počtem obyvatel větším než 10 000 obyvatel.
