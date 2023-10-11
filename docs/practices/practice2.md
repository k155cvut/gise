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

# Vector data, attribute queries, spatial queries

<!-- ## Cíl cvičení -->

## Basic terms

### Vector and raster spatial data

<div class="process_container" style="flex-wrap:wrap;align-items:stretch;">
  <div class="grid" style="flex:1 1 300px;">
    <span class="twemoji"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M2 3v6h2.95l2 6H6v6h6v-4.59L17.41 11H22V5h-6v4.57L10.59 15H9.06l-2-6H8V3M4 5h2v2H4m14 0h2v2h-2M8 17h2v2H8Z"></path></svg></span>&nbsp;
    <strong>Vector data</strong>
    <hr style="margin:10px 0;">
    <p>Formed by <strong>vertices</strong> and <strong>paths</strong> - these are determined by actual coordinates. </p>
    <p>The detail is determined by the <strong>detail of the vertex coordinates.</strong></p>
    <p>Suitable for <strong>discretely distributed data</strong> (e.g. point locations, land cover categories)</p>
    <p>Possible <strong>topology</strong> problems (gaps and overlaps)</p>
  </div>
  <div class="grid" style="flex:1 1 300px;">
    <span class="twemoji"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M10 4v4h4V4h-4m6 0v4h4V4h-4m0 6v4h4v-4h-4m0 6v4h4v-4h-4m-2 4v-4h-4v4h4m-6 0v-4H4v4h4m0-6v-4H4v4h4m0-6V4H4v4h4m2 6h4v-4h-4v4M4 2h16a2 2 0 0 1 2 2v16a2 2 0 0 1-2 2H4c-1.08 0-2-.9-2-2V4a2 2 0 0 1 2-2Z"></path></svg></span>&nbsp;
    <strong>Raster data</strong>
    <span style="font-size:60%;font-style:italic;vertical-align:10%;margin-left:15px;color:#888">part of future exercises</span>
    <hr style="margin:10px 0;">
    <p>Formed by a regular grid of <strong>pixels</strong> – these are determined by pixel coordinates (row/column order)</p>
    <p>Detail is determined by <strong>pixel size</strong> (in meters)</p>
    <p>Suitable for phenomena changing <strong>continuously </strong> (e.g. terrain model, air pollution) and <strong>discretely</strong>,  as well as <strong>image data</strong> (e.g. satellite)</p>
  </div>
</div>

<!-- ## Použité datové podklady -->

## Practice content

### Attribute queries

Attribute Query is a method of selecting/filtering elements based on **attribute values**. It complements the [interactive feature selection](/practices/practice1/#select-tool) method from exercise 1. The basis is a selection rule - called **Expression**. ArcGIS Pro allows you to build expressions interactively using dialogs, but to use the full potential of expressions, it is recommended to use _SQL_ code.
<br><br>

<style>
  code.AGPF {border:2px solid var(--md-primary-fg-color);padding:.1em .4em !important;/*transition: all .1s ease-in-out !important; display:inline-block !important;*/}
  code.AGPF .twemoji {vertical-align:-10% !important;}
  /* code.AGPF:hover {transform: scale(0.96);} */
</style>

**Attribute query** (over map data): <code class="AGPF">:material-tab: Map</code> → <code class="AGPF">:material-button-cursor: Select By Attributes</code> → fill in the dialog..
[:material-open-in-new: Select features using attributes](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/select-features-using-attributes.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}

![](../assets/cviceni1/img_33.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_34.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_35.png)
{: .process_container}

<figcaption>The <code>Input Rows</code> field is automatically prepopulated with the layer selected in the map content </figcaption>

Using the ![](../assets/cviceni1/img_36.png){ switch: .off-glb style="vertical-align: -20%;margin:0px 5px;"} you can change the notation between the interactive dialog entry and the SQL expression.

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
<details class="example page_color_admonition" open="">
<summary>Example to try<div style="display:inline-block; border-left: 1px solid var(--md-admonition-fg-color); height:.9rem;vertical-align:-20%;margin:0px 20px"></div><span style="font-weight:normal;">testing attribute queries on real data</span></summary>
  <iframe style="filter:none !important;margin-top:.6rem;" width="100%" height="500" frameborder="0" allowfullscreen src="https://geo.fsv.cvut.cz/data/hoffmann/appqueryGISE/"></iframe>
  <hr class="l1" style="margin-bottom:0px !important;">
  <div style="margin-top:10px;margin-left:10px;font-weight:bold;font-size:larger;">Layer attributes scheme:</div>
  
  <style>
    #small_table_padding :is(th,td) {padding:5px 10px;}
    .md-typeset__table {width:100%;}
    .md-typeset__scrollwrap {margin-top:5px !important;}
    tbody {width:100%;display:table;}
  </style>
  <table id="small_table_padding">
    <tr>
      <th>attribute</th>
      <th>data type</th>
      <th>description</th>
    </tr>
    <tr>
      <td>TOTPOP_CY</td>
      <td><code>Integer</code></td>
      <td>Total Population</td>
    </tr>
    <tr>
      <td>POPDENS_CY</td>
      <td><code>Double</code></td>
      <td>Population Density (Population per Square Kilometer)</td>
    </tr>
    <tr>
      <td>POPPRM_CY</td>
      <td><code>Double</code></td>
      <td>Population Per Mill</td>
    </tr>
    <tr>
      <td>MALES_CY</td>
      <td><code>Integer</code></td>
      <td>Total Male Population</td>
    </tr>
    <tr>
      <td>FEMALES_CY</td>
      <td><code>Integer</code></td>
      <td>Total Female Population</td>
    </tr>
    <tr>
      <td>TOTHH_CY</td>
      <td><code>Integer</code></td>
      <td>Total Households</td>
    </tr>
    <tr>
      <td>AVGHHSZ_CY</td>
      <td><code>Double</code></td>
      <td>Average Household Size</td>
    </tr>
    <tr>
      <td>PAGE01_CY</td>
      <td><code>Integer</code></td>
      <td>Total Population Age 0-14</td>
    </tr>
    <tr>
      <td>PAGE02_CY</td>
      <td><code>Integer</code></td>
      <td>Total Population Age 15-29</td>
    </tr>
    <tr>
      <td>PAGE03_CY</td>
      <td><code>Integer</code></td>
      <td>Total Population Age 30-44</td>
    </tr>
    <tr>
      <td>PAGE04_CY</td>
      <td><code>Integer</code></td>
      <td>Total Population Age 45-59</td>
    </tr>
    <tr>
      <td>PAGE05_CY</td>
      <td><code>Integer</code></td>
      <td>Total Population Age 60+</td>
    </tr>
    <tr>
      <td>MAGE01_CY</td>
      <td><code>Integer</code></td>
      <td>Male Population Age 0-14</td>
    </tr>
    <tr>
      <td>MAGE02_CY</td>
      <td><code>Integer</code></td>
      <td>Male Population Age 15-29</td>
    </tr>
    <tr>
      <td>MAGE03_CY</td>
      <td><code>Integer</code></td>
      <td>Male Population Age 30-44</td>
    </tr>
    <tr>
      <td>MAGE04_CY</td>
      <td><code>Integer</code></td>
      <td>Male Population Age 45-59</td>
    </tr>
    <tr>
      <td>MAGE05_CY</td>
      <td><code>Integer</code></td>
      <td>Male Population Age 60+</td>
    </tr>
    <tr>
      <td>FAGE01_CY</td>
      <td><code>Integer</code></td>
      <td>Female Population Age 0-14</td>
    </tr>
    <tr>
      <td>FAGE02_CY</td>
      <td><code>Integer</code></td>
      <td>Female Population Age 15-29</td>
    </tr>
    <tr>
      <td>FAGE03_CY</td>
      <td><code>Integer</code></td>
      <td>Female Population Age 30-44</td>
    </tr>
    <tr>
      <td>FAGE04_CY</td>
      <td><code>Integer</code></td>
      <td>Female Population Age 45-59</td>
    </tr>
    <tr>
      <td>FAGE05_CY</td>
      <td><code>Integer</code></td>
      <td>Female Population Age 60+</td>
    </tr>
    <tr>
      <td>HINC01_CY</td>
      <td><code>Integer</code></td>
      <td>Total Households in 1st (lowest) Income Quintile (Below 382,242 CZK)</td>
    </tr>
    <tr>
      <td>HINC02_CY</td>
      <td><code>Integer</code></td>
      <td>Total Households in 2nd Income Quintile (382,242 to 469,620 CZK)</td>
    </tr>
    <tr>
      <td>HINC03_CY</td>
      <td><code>Integer</code></td>
      <td>Total Households in 3rd Income Quintile (469,621 to 640,510 CZK)</td>
    </tr>
    <tr>
      <td>HINC04_CY</td>
      <td><code>Integer</code></td>
      <td>Total Households in 4th Income Quintile (640,511 to 864,545 CZK)</td>
    </tr>
    <tr>
      <td>HINC05_CY</td>
      <td><code>Integer</code></td>
      <td>Total Households in 5th Income Quintile (864,546 CZK and above)</td>
    </tr>
    <tr>
      <td>HTYP01_CY</td>
      <td><code>Integer</code></td>
      <td>Households by Type: Single Person - Living Alone</td>
    </tr>
    <tr>
      <td>HTYP02_CY</td>
      <td><code>Integer</code></td>
      <td>Households by Type: Single Person - Living with Another Household</td>
    </tr>
    <tr>
      <td>HTYP03_CY</td>
      <td><code>Integer</code></td>
      <td>Households by Type: Multi-Person Non-Family Households</td>
    </tr>
    <tr>
      <td>HTYP04_CY</td>
      <td><code>Integer</code></td>
      <td>Households by Type: Family Households - Couple without Children</td>
    </tr>
    <tr>
      <td>HTYP05_CY</td>
      <td><code>Integer</code></td>
      <td>Households by Type: Family Households - Couple with Children</td>
    </tr>
    <tr>
      <td>HTYP06_CY</td>
      <td><code>Integer</code></td>
      <td>Households by Type: Single Parent - Male</td>
    </tr>
    <tr>
      <td>HTYP07_CY</td>
      <td><code>Integer</code></td>
      <td>Households by Type: Single Parent - Female</td>
    </tr>
    <tr>
      <td>HTYP08_CY</td>
      <td><code>Integer</code></td>
      <td>Households by Type: Households with Two or More Families</td>
    </tr>
    <tr>
      <td>HTYP_BASE</td>
      <td><code>Integer</code></td>
      <td>Households by Type Base</td>
    </tr>
    <tr>
      <td>MRST01_CY</td>
      <td><code>Integer</code></td>
      <td>Marital Status: Single</td>
    </tr>
    <tr>
      <td>MRST02_CY</td>
      <td><code>Integer</code></td>
      <td>Marital Status: Married</td>
    </tr>
    <tr>
      <td>MRST03_CY</td>
      <td><code>Integer</code></td>
      <td>Marital Status: Divorced</td>
    </tr>
    <tr>
      <td>MRST04_CY</td>
      <td><code>Integer</code></td>
      <td>Marital Status: Widowed</td>
    </tr>
    <tr>
      <td>MRST_BASE</td>
      <td><code>Integer</code></td>
      <td>Marital Status Base</td>
    </tr>
    <tr>
      <td>EDUC01A_CY</td>
      <td><code>Integer</code></td>
      <td>Population by Education: No Formal Education (ISCED 0)</td>
    </tr>
    <tr>
      <td>EDUC02A_CY</td>
      <td><code>Integer</code></td>
      <td>Population by Education: Primary Not Completed</td>
    </tr>
    <tr>
      <td>EDUC03A_CY</td>
      <td><code>Integer</code></td>
      <td>Population by Education: Primary and Lower Secondary Education (ISCED 1, 2)</td>
    </tr>
    <tr>
      <td>EDUC04A_CY</td>
      <td><code>Integer</code></td>
      <td>Population by Education: Secondary General</td>
    </tr>
    <tr>
      <td>EDUC05A_CY</td>
      <td><code>Integer</code></td>
      <td>Population by Education: Secondary Technical</td>
    </tr>
    <tr>
      <td>EDUC06A_CY</td>
      <td><code>Integer</code></td>
      <td>Population by Education: Post-Secondary Education Non-Tertiary (ISCED 4)</td>
    </tr>
    <tr>
      <td>EDUC07B_CY</td>
      <td><code>Integer</code></td>
      <td>Population by Education: Post-Secondary Professional Education (ISCED 5B)</td>
    </tr>
    <tr>
      <td>EDUC08B_CY</td>
      <td><code>Integer</code></td>
      <td>Population by Education: Bachelor (ISCED 5A)</td>
    </tr>
    <tr>
      <td>EDUC09B_CY</td>
      <td><code>Integer</code></td>
      <td>Population by Education: Master (ISCED 5A)</td>
    </tr>
    <tr>
      <td>EDUC10_CY</td>
      <td><code>Integer</code></td>
      <td>Population by Education: Doctoral</td>
    </tr>
    <tr>
      <td>EDUC11_CY</td>
      <td><code>Integer</code></td>
      <td>Population by Education: Secondary Including Vocational Education (ISCED 3C)</td>
    </tr>
    <tr>
      <td>EDUC12_CY</td>
      <td><code>Integer</code></td>
      <td>Population by Education: Undefined (Younger Than 15 Years)</td>
    </tr>
    <tr>
      <td>EDUC13_CY</td>
      <td><code>Integer</code></td>
      <td>Population by Education: Unknown</td>
    </tr>
    <tr>
      <td>EDUC_BASE</td>
      <td><code>Integer</code></td>
      <td>Education Attainment Base</td>
    </tr>
    <tr>
      <td>UNEMP_CY</td>
      <td><code>Integer</code></td>
      <td>Unemployed Population (2021)</td>
    </tr>
    <tr>
      <td>PP_CY</td>
      <td><code>Double</code></td>
      <td>Purchasing Power: Total</td>
    </tr>
    <tr>
      <td>PPPRM_CY</td>
      <td><code>Double</code></td>
      <td>Purchasing Power: Per Mill</td>
    </tr>
    <tr>
      <td>PPPC_CY</td>
      <td><code>Double</code></td>
      <td>Purchasing Power: Per Capita</td>
    </tr>
    <tr>
      <td>PPIDX_CY</td>
      <td><code>Double</code></td>
      <td>Purchasing Power: Index</td>
    </tr>
    <tr>
      <td>CS01_CY</td>
      <td><code>Double</code></td>
      <td>Food & Non-Alcoholic Beverage Expenditures: Total</td>
    </tr>
    <tr>
      <td>CS01PRM_CY</td>
      <td><code>Double</code></td>
      <td>Food & Non-Alcoholic Beverage Expenditures: Per Mill</td>
    </tr>
    <tr>
      <td>CSPC01_CY</td>
      <td><code>Double</code></td>
      <td>Food & Non-Alcoholic Beverage Expenditures: Per Capita</td>
    </tr>
    <tr>
      <td>CS01IDX_CY</td>
      <td><code>Double</code></td>
      <td>Food & Non-Alcoholic Beverage Expenditures: Index</td>
    </tr>
    <tr>
      <td>CS02_CY</td>
      <td><code>Double</code></td>
      <td>Alcoholic Beverage Expenditures: Total</td>
    </tr>
    <tr>
      <td>CS02PRM_CY</td>
      <td><code>Double</code></td>
      <td>Alcoholic Beverage Expenditures: Per Mill</td>
    </tr>
    <tr>
      <td>CSPC02_CY</td>
      <td><code>Double</code></td>
      <td>Alcoholic Beverage Expenditures: Per Capita</td>
    </tr>
    <tr>
      <td>CS02IDX_CY</td>
      <td><code>Double</code></td>
      <td>Alcoholic Beverage Expenditures: Index</td>
    </tr>
    <tr>
      <td>CS03_CY</td>
      <td><code>Double</code></td>
      <td>Tobacco Expenditures: Total</td>
    </tr>
    <tr>
      <td>CS03PRM_CY</td>
      <td><code>Double</code></td>
      <td>Tobacco Expenditures: Per Mill</td>
    </tr>
    <tr>
      <td>CSPC03_CY</td>
      <td><code>Double</code></td>
      <td>Tobacco Expenditures: Per Capita</td>
    </tr>
    <tr>
      <td>CS03IDX_CY</td>
      <td><code>Double</code></td>
      <td>Tobacco Expenditures: Index</td>
    </tr>
    <tr>
      <td>CS04_CY</td>
      <td><code>Double</code></td>
      <td>Clothing Expenditures: Total</td>
    </tr>
    <tr>
      <td>CS04PRM_CY</td>
      <td><code>Double</code></td>
      <td>Clothing Expenditures: Per Mill</td>
    </tr>
    <tr>
      <td>CSPC04_CY</td>
      <td><code>Double</code></td>
      <td>Clothing Expenditures: Per Capita</td>
    </tr>
    <tr>
      <td>CS04IDX_CY</td>
      <td><code>Double</code></td>
      <td>Clothing Expenditures: Index</td>
    </tr>
    <tr>
      <td>CS05_CY</td>
      <td><code>Double</code></td>
      <td>Footwear Expenditures: Total</td>
    </tr>
    <tr>
      <td>CS05PRM_CY</td>
      <td><code>Double</code></td>
      <td>Footwear Expenditures: Per Mill</td>
    </tr>
    <tr>
      <td>CSPC05_CY</td>
      <td><code>Double</code></td>
      <td>Footwear Expenditures: Per Capita</td>
    </tr>
    <tr>
      <td>CS05IDX_CY</td>
      <td><code>Double</code></td>
      <td>Footwear Expenditures: Index</td>
    </tr>
    <tr>
      <td>CS06_CY</td>
      <td><code>Double</code></td>
      <td>Furniture, Furnishing, & Floor Covering Expenditures: Total</td>
    </tr>
    <tr>
      <td>CS06PRM_CY</td>
      <td><code>Double</code></td>
      <td>Furniture, Furnishing, & Floor Covering Expenditures: Per Mill</td>
    </tr>
    <tr>
      <td>CSPC06_CY</td>
      <td><code>Double</code></td>
      <td>Furniture, Furnishing, & Floor Covering Expenditures: Per Capita</td>
    </tr>
    <tr>
      <td>CS06IDX_CY</td>
      <td><code>Double</code></td>
      <td>Furniture, Furnishing, & Floor Covering Expenditures: Index</td>
    </tr>
    <tr>
      <td>CS07_CY</td>
      <td><code>Double</code></td>
      <td>Household Textiles Expenditures: Total</td>
    </tr>
    <tr>
      <td>CS07PRM_CY</td>
      <td><code>Double</code></td>
      <td>Household Textiles Expenditures: Per Mill</td>
    </tr>
    <tr>
      <td>CSPC07_CY</td>
      <td><code>Double</code></td>
      <td>Household Textiles Expenditures: Per Capita</td>
    </tr>
    <tr>
      <td>CS07IDX_CY</td>
      <td><code>Double</code></td>
      <td>Household Textiles Expenditures: Index</td>
    </tr>
    <tr>
      <td>CS08_CY</td>
      <td><code>Double</code></td>
      <td>Household Appliances Expenditures: Total</td>
    </tr>
    <tr>
      <td>CS08PRM_CY</td>
      <td><code>Double</code></td>
      <td>Household Appliances Expenditures: Per Mill</td>
    </tr>
    <tr>
      <td>CSPC08_CY</td>
      <td><code>Double</code></td>
      <td>Household Appliances Expenditures: Per Capita</td>
    </tr>
    <tr>
      <td>CS08IDX_CY</td>
      <td><code>Double</code></td>
      <td>Household Appliances Expenditures: Index</td>
    </tr>
    <tr>
      <td>CS09_CY</td>
      <td><code>Double</code></td>
      <td>Glassware, Tableware, & Household Utensils Expenditures: Total</td>
    </tr>
    <tr>
      <td>CS09PRM_CY</td>
      <td><code>Double</code></td>
      <td>Glassware, Tableware, & Household Utensils Expenditures: Per Mill</td>
    </tr>
    <tr>
      <td>CSPC09_CY</td>
      <td><code>Double</code></td>
      <td>Glassware, Tableware, & Household Utensils Expenditures: Per Capita</td>
    </tr>
    <tr>
      <td>CS09IDX_CY</td>
      <td><code>Double</code></td>
      <td>Glassware, Tableware, & Household Utensils Expenditures: Index</td>
    </tr>
    <tr>
      <td>CS10_CY</td>
      <td><code>Double</code></td>
      <td>House & Garden Tools/Equipment Expenditures: Total</td>
    </tr>
    <tr>
      <td>CS10PRM_CY</td>
      <td><code>Double</code></td>
      <td>House & Garden Tools/Equipment Expenditures: Per Mill</td>
    </tr>
    <tr>
      <td>CSPC10_CY</td>
      <td><code>Double</code></td>
      <td>House & Garden Tools/Equipment Expenditures: Per Capita</td>
    </tr>
    <tr>
      <td>CS10IDX_CY</td>
      <td><code>Double</code></td>
      <td>House & Garden Tools/Equipment Expenditures: Index</td>
    </tr>
    <tr>
    <td>CS11_CY</td>
    <td><code>Double</code></td>
    <td>2022 Routine Household Maintenance Expenditures: Total</td>
  </tr>
  <tr>
    <td>CS11PRM_CY</td>
    <td><code>Double</code></td>
    <td>2022 Routine Household Maintenance Expenditures: Per Mill</td>
  </tr>
  <tr>
    <td>CSPC11_CY</td>
    <td><code>Double</code></td>
    <td>2022 Routine Household Maintenance Expenditures: Per Capita</td>
  </tr>
  <tr>
    <td>CS11IDX_CY</td>
    <td><code>Double</code></td>
    <td>2022 Routine Household Maintenance Expenditures: Index</td>
  </tr>
  <tr>
    <td>CS12_CY</td>
    <td><code>Double</code></td>
    <td>2022 Medical Products & Equipment/Appliances Expenditures: Total</td>
  </tr>
  <tr>
    <td>CS12PRM_CY</td>
    <td><code>Double</code></td>
    <td>2022 Medical Products & Equipment/Appliances Expenditures: Per Mill</td>
  </tr>
  <tr>
    <td>CSPC12_CY</td>
    <td><code>Double</code></td>
    <td>2022 Medical Products & Equipment/Appliances Expenditures: Per Capita</td>
  </tr>
  <tr>
    <td>CS12IDX_CY</td>
    <td><code>Double</code></td>
    <td>2022 Medical Products & Equipment/Appliances Expenditures: Index</td>
  </tr>
  <tr>
    <td>CS13_CY</td>
    <td><code>Double</code></td>
    <td>2022 Consumer Electronics & Photo/IT Equipment Expenditures: Total</td>
  </tr>
  <tr>
    <td>CS13PRM_CY</td>
    <td><code>Double</code></td>
    <td>2022 Consumer Electronics & Photo/IT Equipment Expenditures: Per Mill</td>
  </tr>
  <tr>
    <td>CSPC13_CY</td>
    <td><code>Double</code></td>
    <td>2022 Consumer Electronics & Photo/IT Equipment Expenditures: Per Capita</td>
  </tr>
  <tr>
    <td>CS13IDX_CY</td>
    <td><code>Double</code></td>
    <td>2022 Consumer Electronics & Photo/IT Equipment Expenditures: Index</td>
  </tr>
  <tr>
    <td>CS14_CY</td>
    <td><code>Double</code></td>
    <td>2022 Recreation & Culture Durable Expenditures: Total</td>
  </tr>
  <tr>
    <td>CS14PRM_CY</td>
    <td><code>Double</code></td>
    <td>2022 Recreation & Culture Durable Expenditures: Per Mill</td>
  </tr>
  <tr>
    <td>CSPC14_CY</td>
    <td><code>Double</code></td>
    <td>2022 Recreation & Culture Durable Expenditures: Per Capita</td>
  </tr>
  <tr>
    <td>CS14IDX_CY</td>
    <td><code>Double</code></td>
    <td>2022 Recreation & Culture Durable Expenditures: Index</td>
  </tr>
  <tr>
    <td>CS15_CY</td>
    <td><code>Double</code></td>
    <td>2022 Toys, Games, Hobby, Sports, Garden, & Pets Expenditures: Total</td>
  </tr>
  <tr>
    <td>CS15PRM_CY</td>
    <td><code>Double</code></td>
    <td>2022 Toys, Games, Hobby, Sports, Garden, & Pets Expenditures: Per Mill</td>
  </tr>
  <tr>
    <td>CSPC15_CY</td>
    <td><code>Double</code></td>
    <td>2022 Toys, Games, Hobby, Sports, Garden, & Pets Expenditures: Per Capita</td>
  </tr>
  <tr>
    <td>CS15IDX_CY</td>
    <td><code>Double</code></td>
    <td>2022 Toys, Games, Hobby, Sports, Garden, & Pets Expenditures: Index</td>
  </tr>
  <tr>
    <td>CS16_CY</td>
    <td><code>Double</code></td>
    <td>2022 Recreational & Cultural Service Expenditures: Total</td>
  </tr>
  <tr>
    <td>CS16PRM_CY</td>
    <td><code>Double</code></td>
    <td>2022 Recreational & Cultural Service Expenditures: Per Mill</td>
  </tr>
  <tr>
    <td>CSPC16_CY</td>
    <td><code>Double</code></td>
    <td>2022 Recreational & Cultural Service Expenditures: Per Capita</td>
  </tr>
  <tr>
    <td>CS16IDX_CY</td>
    <td><code>Double</code></td>
    <td>2022 Recreational & Cultural Service Expenditures: Index</td>
  </tr>
  <tr>
    <td>CS17_CY</td>
    <td><code>Double</code></td>
    <td>2022 Books, Newspapers, & Stationery Expenditures: Total</td>
  </tr>
  <tr>
    <td>CS17PRM_CY</td>
    <td><code>Double</code></td>
    <td>2022 Books, Newspapers, & Stationery Expenditures: Per Mill</td>
  </tr>
  <tr>
    <td>CSPC17_CY</td>
    <td><code>Double</code></td>
    <td>2022 Books, Newspapers, & Stationery Expenditures: Per Capita</td>
  </tr>
  <tr>
    <td>CS17IDX_CY</td>
    <td><code>Double</code></td>
    <td>2022 Books, Newspapers, & Stationery Expenditures: Index</td>
  </tr>
  <tr>
    <td>CS18_CY</td>
    <td><code>Double</code></td>
    <td>2022 Catering Services Expenditures: Total</td>
  </tr>
  <tr>
    <td>CS18PRM_CY</td>
    <td><code>Double</code></td>
    <td>2022 Catering Services Expenditures: Per Mill</td>
  </tr>
  <tr>
    <td>CSPC18_CY</td>
    <td><code>Double</code></td>
    <td>2022 Catering Services Expenditures: Per Capita</td>
  </tr>
  <tr>
    <td>CS18IDX_CY</td>
    <td><code>Double</code></td>
    <td>2022 Catering Services Expenditures: Index</td>
  </tr>
  <tr>
    <td>CS19_CY</td>
    <td><code>Double</code></td>
    <td>2022 Personal Care Expenditures: Total</td>
  </tr>
  <tr>
    <td>CS19PRM_CY</td>
    <td><code>Double</code></td>
    <td>2022 Personal Care Expenditures: Per Mill</td>
  </tr>
  <tr>
    <td>CSPC19_CY</td>
    <td><code>Double</code></td>
    <td>2022 Personal Care Expenditures: Per Capita</td>
  </tr>
  <tr>
    <td>CS19IDX_CY</td>
    <td><code>Double</code></td>
    <td>2022 Personal Care Expenditures: Index</td>
  </tr>
  <tr>
    <td>CS20_CY</td>
    <td><code>Double</code></td>
    <td>2022 Jewelry, Watches, & Personal Effects Expenditures: Total</td>
  </tr>
  <tr>
    <td>CS20PRM_CY</td>
    <td><code>Double</code></td>
    <td>2022 Jewelry, Watches, & Personal Effects Expenditures: Per Mill</td>
  </tr>
  <tr>
    <td>CSPC20_CY</td>
    <td><code>Double</code></td>
    <td>2022 Jewelry, Watches, & Personal Effects Expenditures: Per Capita</td>
  </tr>
  <tr>
    <td>CS20IDX_CY</td>
    <td><code>Double</code></td>
    <td>2022 Jewelry, Watches, & Personal Effects Expenditures: Index</td>
  </tr>
  <tr>
  <td>OBJECTID</td>
  <td><code>ID</code></td>
  <td>OBJECTID</td>
</tr>
<tr>
  <td>Shape</td>
  <td><code>Geometry</code></td>
  <td>Shape</td>
</tr>
<tr>
  <td>ID</td>
  <td><code>String</code></td>
  <td>ID</td>
</tr>
<tr>
  <td>NAME</td>
  <td><code>String</code></td>
  <td>NAME</td>
</tr>
<tr>
  <td>AREA</td>
  <td><code>Double</code></td>
  <td>AREA</td>
</tr>
<tr>
  <td>POP</td>
  <td><code>Double</code></td>
  <td>POP</td>
</tr>
<tr>
  <td>RG_NAME</td>
  <td><code>String</code></td>
  <td>RG_NAME</td>
</tr>

  </table>
</details>

<hr class="l1">

### Spatial queries

Spatial query is a method of selecting/filtering elements of one layer based on their relative position with elements of another layer. The function uses as input <code>**the layer of selected elements**</code>, <code>**the layer for overlay analysis**</code> a <code>**the relationship for overlay analysis**</code>.

![](https://geo.fsv.cvut.cz/data/cehak/155SGEA/img_01.svg){ .off-glb style="filter:none !important;" }
![](https://geo.fsv.cvut.cz/data/cehak/155SGEA/img_02.svg){ .off-glb style="filter:none !important;" }
{: .process_container}

<style>
  .tabbed-labels {justify-content:center;}
  .tabbed-labels::before {transition:unset !important;}
</style>

=== "Select POINTS..."

    === "...using POINTS"

        ![](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/GUID-1ECFFABC-3608-4BB4-86A8-FD6FA0F16C13-web.gif){ style="filter:none !important;" }
        {: align=center}

        <table id="small_table_padding" style="width:unset;">
          <tr><td>Intersect</td><td>A</td></tr>
          <tr><td>Intersect (DBMS)</td><td>A</td></tr>
          <tr><td>Contains</td><td>A</td></tr>
          <tr><td>Contains Clementini</td><td>A</td></tr>
          <tr><td>Within</td><td>A</td></tr>
          <tr><td>Within Clementini</td><td>A</td></tr>
          <tr><td>Are identical to</td><td>A</td></tr>
          <tr><td>Have their center in</td><td>A</td></tr>
        </table>

    === "...using LINES"

        ![](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/GUID-171AD80E-550B-4017-AEB7-1A681D722F60-web.gif){ style="filter:none !important;" }
        {: align=center}

        <table id="small_table_padding" style="width:unset;">
          <tr><td>Intersect</td><td>A, C</td></tr>
          <tr><td>Intersect (DBMS)</td><td>A, C</td></tr>
          <tr><td>Within</td><td>A, C</td></tr>
          <tr><td>Completely within</td><td>A</td></tr>
          <tr><td>Within Clementini</td><td>A</td></tr>
          <tr><td>Have their center in</td><td>A, C</td></tr>
          <tr><td>Boundary touches</td><td>C</td></tr>
        </table>

    === "...using POLYGONS"

        ![](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/GUID-12153063-E9B3-42E5-A786-E3FAF6BB004E-web.gif){ style="filter:none !important;" }
        {: align=center}

        <table id="small_table_padding" style="width:unset;">
          <tr><td>Intersect</td><td>A, C</td></tr>
          <tr><td>Intersect (DBMS)</td><td>A, C</td></tr>
          <tr><td>Within</td><td>A, C</td></tr>
          <tr><td>Completely within</td><td>A</td></tr>
          <tr><td>Within Clementini</td><td>A</td></tr>
          <tr><td>Have their center in</td><td>A, C</td></tr>
          <tr><td>Boundary touches</td><td>C</td></tr>
        </table>

=== "Select LINES"

    === "...using POINTS"

        ![](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/GUID-FD60FA73-31CD-4BD7-B03C-06806851BC9E-web.gif){ style="filter:none !important;" }
        {: align=center}

        <table id="small_table_padding" style="width:unset;">
          <tr><td>Intersect</td><td>A, C, D</td></tr>
          <tr><td>Intersect (DBMS)</td><td>A, C, D</td></tr>
          <tr><td>Contains</td><td>A, C, D</td></tr>
          <tr><td>Completely contains</td><td>A, D</td></tr>
          <tr><td>Contains Clementini</td><td>A, D</td></tr>
          <tr><td>Have their center in</td><td>D</td></tr>
          <tr><td>Boundary touches</td><td>C</td></tr>
        </table>

    === "...using LINES"

        ![](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/GUID-09D6FB47-31A3-47C3-A8B8-19BB659EBA8A-web.gif){ style="filter:none !important;" }
        {: align=center}

        <table id="small_table_padding" style="width:unset;">
          <tr><td>Intersect</td><td>A, C, D, E, F, G, H, I, J</td></tr>
          <tr><td>Intersect (DBMS)</td><td>A, C, D, E, F, G, H, I, J</td></tr>
          <tr><td>Contains</td><td>G, H</td></tr>
          <tr><td>Completely contains</td><td>G</td></tr>
          <tr><td>Contains Clementini</td><td>G, H</td></tr>
          <tr><td>Within</td><td>F, H</td></tr>
          <tr><td>Completely within</td><td>F</td></tr>
          <tr><td>Within Clementini</td><td>F, H</td></tr>
          <tr><td>Are identical to</td><td>H</td></tr>
          <tr><td>Boundary touches</td><td>C, E</td></tr>
          <tr><td>Share a line segment with</td><td>F, G, H, I, J</td></tr>
        </table>

    === "...using POLYGONS"

        ![](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/GUID-54663F11-5B47-46A5-82C1-37FD1FDDC835-web.gif){ style="filter:none !important;" }
        {: align=center}

        <table id="small_table_padding" style="width:unset;">
          <tr><td>Intersect</td><td>A, C, D, E, F, G, H, I, J, K, L, M, N, O</td></tr>
          <tr><td>Intersect (DBMS)</td><td>A, C, D, E, F, G, H, I, J, K, L, M, N, O</td></tr>
          <tr><td>Within</td><td>A, D, G, H, I, O</td></tr>
          <tr><td>Completely within</td><td>A</td></tr>
          <tr><td>Within Clementini</td><td>A, D, G, H, I</td></tr>
          <tr><td>Boundary touches</td><td>F, G, H, I, K, L, M, N, O</td></tr>
          <tr><td>Share a line segment with</td><td>G, I, J, K, M, O</td></tr>
          <tr><td>Crossed by the outline of</td><td>C, E, H, L, N</td></tr>
          <tr><td>Have their center in</td><td>A, C, D, E, G, H, I, J, O</td></tr>
        </table>

=== "Select POLYGONS..."

    === "...using POINTS"

        ![](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/GUID-0973BB65-5DAE-461A-8B84-E58332CDA443-web.gif){ style="filter:none !important;" }
        {: align=center}

        <table id="small_table_padding" style="width:unset;">
          <tr><td>Intersect</td><td>A, B</td></tr>
          <tr><td>Intersect (DBMS)</td><td>A, B</td></tr>
          <tr><td>Contains</td><td>A, B</td></tr>
          <tr><td>Completely contains</td><td>A</td></tr>
          <tr><td>Contains Clementini</td><td>A</td></tr>
          <tr><td>Have their center in</td><td>A, D</td></tr>
          <tr><td>Boundary touches</td><td>B</td></tr>
        </table>

    === "...using LINES"

        ![](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/GUID-EFDE4E93-532E-4D6E-BB29-9BBFC783CEC7-web.gif){ style="filter:none !important;" }
        {: align=center}

        <table id="small_table_padding" style="width:unset;">
          <tr><td>Intersect</td><td>A, C, D, E, F, G, H, I, J, K, L, M, N, O</td></tr>
          <tr><td>Intersect (DBMS)</td><td>A, C, D, E, F, G, H, I, J, K, L, M, N, O</td></tr>
          <tr><td>Contains</td><td>A, D, G, H, I, O</td></tr>
          <tr><td>Completely contains</td><td>A</td></tr>
          <tr><td>Contains Clementini</td><td>A, D, G, H, I</td></tr>
          <tr><td>Boundary touches</td><td>F, G, H, I, K, L, M, N, O</td></tr>
          <tr><td>Share a line segment with</td><td>G, I, J, K, M, O</td></tr>
          <tr><td>Crossed by the outline of</td><td>C, E, H, L, N</td></tr>
          <tr><td>Have their center in</td><td>E, I, L</td></tr>
        </table>

    === "...using POLYGONS"

        ![](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/GUID-7802EBC1-8E73-4071-AE12-4445AB1C24B5-web.gif){ style="filter:none !important;" }
        {: align=center}

        <table id="small_table_padding" style="width:unset;">
          <tr><td>Intersect</td><td>A, C, D, E, F, G, H, I, J, K, M</td></tr>
          <tr><td>Intersect (DBMS)</td><td>A, C, D, E, F, G, H, I, J, K, M</td></tr>
          <tr><td>Contains</td><td>C, E, H, M</td></tr>
          <tr><td>Completely contains</td><td>C</td></tr>
          <tr><td>Contains Clementini</td><td>C, E, H, M</td></tr>
          <tr><td>Within</td><td>F, G, H, M</td></tr>
          <tr><td>Completely within</td><td>F</td></tr>
          <tr><td>Within Clementini</td><td>F, G, H, M</td></tr>
          <tr><td>Are identical to</td><td>H, M</td></tr>
          <tr><td>Boundary touches</td><td>D, E, G, H, I, J, M</td></tr>
          <tr><td>Share a line segment with</td><td>D, H, I, M</td></tr>
          <tr><td>Crossed by the outline of</td><td>A, E, G, J, K</td></tr>
          <tr><td>Have their center in</td><td>C, E, F, G, H, K, L</td></tr>
        </table>

[:material-open-in-new: Select features by location](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/select-features-by-location.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
[:material-open-in-new: Select Layer By Location (Data Management)](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/select-layer-by-location.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
[:material-open-in-new: Select By Location graphic examples](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/select-by-location-graphical-examples.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
{: align=center style="display:flex; justify-content:center; align-items:center; column-gap:20px; row-gap:10px; flex-wrap:wrap;"}

<br><br><br><br><br><br>

<!-- ## Zadání domácího úkolu k semestrální práci -->
