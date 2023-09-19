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
  .process_container {display:flex !important; justify-content:center; align-items:center; gap:calc((100vw * 0.03) - 6px) calc((100vw * 0.03) - 6px);} /* Kontejner pro content = FlexBox */
  .process_container div {display:flex;}                                                                                           /* Obsah (obrazky a sipky) */
  .process_container .process_icon {width:/*40px*/calc((100vw * 0.01) + 25px); flex-shrink:0;filter:none !important;}              /* Velikost ikony (bacha na mobily) */
  .process_container img {max-height:150px;}                                                                                       /* Obrazky ve flexboxech maji maximalni vysku */

  /* Grids */
  .grid {display:inline-block !important;border:.05rem solid var(--md-default-fg-color--lightest);border-radius:.1rem;padding:.8rem;transition: all .1s ease-in-out;}
  .grid:hover {transition: all .1s ease-in-out;box-shadow: 0 10px 16px rgba(0,0,0,0.2);}
</style>

# Vektorová data, atributové dotazy, prostorové dotazy

<!-- ## Cíl cvičení -->

## Základní pojmy

### Vektorová a rastrová prostorová data

<div class="process_container" style="flex-wrap:wrap;align-items:stretch;">
  <div class="grid" style="flex:1 1 300px;">
    <span class="twemoji"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M2 3v6h2.95l2 6H6v6h6v-4.59L17.41 11H22V5h-6v4.57L10.59 15H9.06l-2-6H8V3M4 5h2v2H4m14 0h2v2h-2M8 17h2v2H8Z"></path></svg></span>&nbsp;
    <strong>Vektorová data</strong>
    <hr style="margin:10px 0;">
    <p>Tvořena <strong>vrcholy</strong> (Vertices) a <strong>cestami</strong> (Paths) – ty jsou určeny skutečnými souřadnicemi</p>
    <p>Podrobnost je určena <strong>podrobností souřadnic vrcholů</strong></p>
    <p>Vhodné pro <strong>diskrétně rozložená data</strong> (např. poloha bodů, kategorie pokrytí půdy)</p>
    <p>Možné problémy s <strong>topologií</strong> (mezery a překryvy)</p>
  </div>
  <div class="grid" style="flex:1 1 300px;">
    <span class="twemoji"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M10 4v4h4V4h-4m6 0v4h4V4h-4m0 6v4h4v-4h-4m0 6v4h4v-4h-4m-2 4v-4h-4v4h4m-6 0v-4H4v4h4m0-6v-4H4v4h4m0-6V4H4v4h4m2 6h4v-4h-4v4M4 2h16a2 2 0 0 1 2 2v16a2 2 0 0 1-2 2H4c-1.08 0-2-.9-2-2V4a2 2 0 0 1 2-2Z"></path></svg></span>&nbsp;
    <strong>Rastrová data</strong>
    <span style="font-size:60%;font-style:italic;vertical-align:10%;margin-left:15px;color:#888">součástí budoucích cvičení</span>
    <hr style="margin:10px 0;">
    <p>Tvořena pravidelnou mřížkou <strong>pixelů</strong> – ty jsou určeny pixelovými souřadnicemi (pořadí řádku/sloupce)</p>
    <p>Podrobnost je určena <strong>velikostí pixelu</strong> (v metrech)</p>
    <p>Vhodné pro jevy měnící se <strong>spojitě</strong> (např. model terénu, znečištění ovzduší) i <strong>diskrétně</strong>, dále pak <strong>obrazová data</strong> (např. satelitní)</p>
  </div>
</div>

<!-- ## Použité datové podklady -->

## Náplň cvičení

### Atributové dotazy

Atributový dotaz (Attribute Query) je metoda výběru/filtrace prvků na základě **hodnot jejich atributů**. Doplňuje tak metodu [interaktivního výběru prvků](/cviceni/cviceni1/#select-tool) z 1. cvičení. Základem je pravidlo pro výběr – tzv. **výraz** (Expression). ArcGIS Pro umožňuje sestavovat výrazy interaktivně pomocí dialogu, nicméně pro využití plného potenciálu výrazů je vhodné využít kód v jazyce _SQL_.
<br><br>

<style>
  code.AGPF {border:2px solid var(--md-primary-fg-color);padding:.1em .4em !important;/*transition: all .1s ease-in-out !important; display:inline-block !important;*/}
  code.AGPF .twemoji {vertical-align:-10% !important;}
  /* code.AGPF:hover {transform: scale(0.96);} */
</style>

**Atributový dotaz** (nad daty v mapě): <code class="AGPF">:material-tab: Map</code> → <code class="AGPF">:material-button-cursor: Select By Attributes</code> → vyplnit údaje do dialogu nástroje...
[:material-open-in-new: Select features using attributes](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/select-features-using-attributes.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}

![](../assets/cviceni1/img_33.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_34.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_35.png)
{: .process_container}

<figcaption>Do pole <code>Input Rows</code> je automaticky předvyplněna vrstva vybraná v obsahu mapy </figcaption>

Pomocí přepínátka ![](../assets/cviceni1/img_36.png){: .off-glb style="vertical-align: -20%;margin:0px 5px;"} lze měnit zápis mezi interaktivním dialogovým zadáním a výrazem v jazyce SQL.

[:material-open-in-new: Introduction to query expressions](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/write-a-query-in-the-query-builder.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
[:material-open-in-new: Construct and modify queries](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/construct-and-modify-queries.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
{: align=center style="display:flex; justify-content:center; align-items:center; column-gap:20px; row-gap:10px; flex-wrap:wrap;"}

<style>
  details.page_color_admonition summary:first-child::before {background-color:var(--md-primary-fg-color) !important;}
  /* details.page_color_admonition summary:first-child         {color:#009485 !important;} */
  details.page_color_admonition summary:first-child::after  {color:var(--md-primary-fg-color) !important;}
  details.page_color_admonition {border-color: var(--md-primary-fg-color) !important;margin:50px 0px;}
  details.page_color_admonition summary {background-color: #0094851a !important;}
</style>
<details class="example page_color_admonition">
  <summary>Příklad k vyzkoušení<div style="display:inline-block; border-left: 1px solid var(--md-admonition-fg-color); height:.9rem;vertical-align:-20%;margin:0px 20px"></div><span style="font-weight:normal;">testování atributových dotazů na skutečných datech</span></summary>
  <iframe style="filter:none !important;margin-top:.6rem;" width="100%" height="500" frameborder="0" allowfullscreen src="https://experience.arcgis.com/experience/cbee738914f543748264319797ea0711/?draft=true&org=CTUPrague"></iframe>
  <hr class="l1" style="margin-bottom:0px !important;">
  <div style="margin-top:10px;margin-left:10px;font-weight:bold;font-size:larger;">Schéma atributů vrstvy:</div>
  
  <style>
    #small_table_padding :is(th,td) {padding:5px 10px;}
    .md-typeset__table {width:100%;}
    .md-typeset__scrollwrap {margin-top:5px !important;}
    tbody {width:100%;display:table;}
  </style>
  <table id="small_table_padding">
    <tr>
      <th>atribut</th>
      <th>datový typ</th>
      <th>popis</th>
    </tr>
    <tr>
      <td>stop_name</td>
      <td><code>string</code></td>
      <td>Název zastávky</td>
    </tr>
    <tr>
      <td>routes_nam</td>
      <td><code>string</code></td>
      <td>Označení linek, které obsluhují zastávku, ve formátu <code>-cislolinky-,-cislolinky-</code> řazeno vzestupně</td>
    </tr>
    <tr>
      <td>route_type</td>
      <td><code>integer</code></td>
      <td>ID druhu dopravy, které obsluhují zastávku, <br><code>0=tramvaj</code>, <code>1=metro</code>, <code>2=vlak</code>, <code>3=autobus</code>, <code>4=přívoz</code>, <code>7=lanovka</code>, <code>8=tramvaj i autobus</code></td>
    </tr>
    <tr>
      <td>on_request</td>
      <td><code>integer</code></td>
      <td>Zastávka na znamení <code>0=není na znamení</code>, <code>1=je na znamení</code></td>
    </tr>
    <tr>
      <td>platf_len</td>
      <td><code>float</code></td>
      <td>Délka nástupiště (metry)</td>
    </tr>
  </table>
</details>

<hr class="l1">

### Prostorové dotazy

Prostorový dotaz (Spatial Query) je metoda výběru/filtrace prvků jedné vrstvy na základě vzájemné polohy s prvky druhé vrstvy.

[:material-open-in-new: Select features by location](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/select-features-by-location.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
[:material-open-in-new: Select Layer By Location (Data Management)](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/select-layer-by-location.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
[:material-open-in-new: Select By Location graphic examples](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/select-by-location-graphical-examples.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
{: align=center style="display:flex; justify-content:center; align-items:center; column-gap:20px; row-gap:10px; flex-wrap:wrap;"}

<br><br><br><br><br><br><br><br><br><br><br><br><br><br>

<!-- ## Zadání domácího úkolu k semestrální práci -->
