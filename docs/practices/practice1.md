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

# Introduction to ArcGIS, spatial data, data sources

<hr class="l1">

## Goal

Introduction to ArcGIS Pro, basic orientation in the program environment, adding data to the map and controlling the map

<hr class="l1">

## Basic terms

### Software for education

**ArcGIS Pro**, an advanced desktop geographic information system (GIS) developed by **Esri**, will be used during most of the class. It allows users to **create**, **edit**, **analyze**, and **visualize** spatial data in various layers, including **raster** and **vector** maps, **orthophotos**, **digital elevation model**, and other datasets.  
Users can create and edit **attributes** and **geometry** of features, perform advanced **analysis**, create and **publish map layers**, and create **interactive map applications**. The program also includes tools for **visualizing** data, creating map presentations, and **sharing results** with other users.

![](../assets/cviceni1/agp_logo.png#only-light){ .off-glb width=200px style="filter:none !important;"}
![](../assets/cviceni1/agp_logo2.png#only-dark){ .off-glb width=200px style="filter:none !important;"}
{: align=center}

<span style="color:#448aff">Note:</span>
Due to the high acquisition costs, ArcGIS is mainly used in large companies and government agencies. Its open source alternative QGIS is more widespread in smaller companies (this will be discussed at the end of the course).

### Spatial (GIS) data <span style="font-size:60%;font-style:italic;vertical-align:10%;margin-left:15px;">(vector)</span>

Geographic Information System (GIS) generally uses any data containing **spatial (location) information**. A location can be represented not only by a combination of coordinates (_X + Y_, _latitude + longitude_, etc.), but also by, for example, an address (of arbitrary detail). In addition to the position information, any other information is usually added in the form of attributes in the **attribute table**.

![](../assets/cviceni1/img_28.png){ style="width:80%;"}
{: style="margin-bottom:0px;" align=center }

<figcaption>Schematic illustration of spatial data and associated attribute tables</figcaption>

**Save spatial data**: Data can be stored in many different ways. There are many different data formats, but to start with, here are some basic ones.

- **Shapefile**: a format from _Esri_ with a mostly open specification. It contains the geometry and properties (attributes) of spatial features, probably the most widely used at present, although it has many disadvantages and is somewhat outdated from today's point of view. One of the characteristics of the format is mandatory division into multiple files (`.shp`, `.shx` and `.dbf`, possibly other optional), which brings difficulties when moving, copying, etc.
- **Geodatabase (GDB)**: the native data structure of the _ArcGIS_ system - the primary data format for data management and editing, it contains a collection of datasets of various types (vector, raster and others) and can also store data integrity (domains, subtypes, etc.) or topology
- **GeoJSON**: an open standard representing vector data and associated attributes, based on the `JSON` format and is therefore user-readable and widely used
- **GML / KML**: similar to GeoJSON - an open standard representing vector data and associated attributes, based on the `XML` format, thus again user-readable
- **GeoPackage (GPKG)**: relatively new format of the _OGC_ standard, supports both vector and raster data, overcomes many limitations of the `Shapefile` format (e.g. it is only 1 file), default format of _QGIS_
- **CSV**: although not a format directly intended for spatial data, it is often used as an exchange format, the file contains only attributes

<!-- Ve výčtu chybí některé __rastrové formáty__, těm se bude výuka věnovat v průběhu pozdějších cvičení. -->

<hr class="l1">

## Practice content

### Starting and basic orientation in the program

At launch, the license is verified through the affiliation to the organization (CTU in Prague) - by logging in to the university account. The address (URL) for CTU is _ctuprague.maps.arcgis.com_ - then an automatic redirection to the university login page (in the format *username@cvut.cz* and password to KOS) takes place.

<div class="process_container">
  <div class="process_image"><iframe src="https://www.youtube.com/embed/8nDVpVmxM-0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe></div>
  <div class="process_image"><img src="../../assets/cviceni1/img_01.png"></div>
</div>

<table>
  <tbody>
    <tr>
      <td><strong>RIBBON</strong></td>
      <td>menu of program functions (element identical to other programs, e.g. Microsoft Word), menu changes contextually according to user actions</td>
    </tr>
    <tr>
      <td><strong>PANE</strong></td>
      <td>panels and function properties, many functions trigger opening their own Panel, through which the function is controlled, e.g. Map Contents, Symbology</td>
    </tr>
    <tr>
      <td><strong>VIEW</strong></td>
      <td>a window with a map (2D) or a scene (3D)</td>
    </tr>
  </tbody>
</table>

![](../assets/cviceni1/img_02.png)
![](../assets/cviceni1/img_03.png)
{: .process_container}

<figcaption>All VIEWs and PANEs are dockable - they can be freely moved around the screen and attached to other elements</figcaption>

<!-- :fontawesome-brands-youtube:{: style="color: #EE0F0F" } [__Working with Panes in ArcGIS Pro__](https://www.youtube.com/watch?v=qNDwVJV_kFk).
{: align=center } -->

[:material-open-in-new: Working with Panes in ArcGIS Pro](https://www.youtube.com/watch?v=qNDwVJV_kFk){ .md-button .md-button--primary .button_smaller target="\_blank"}
{: align=center style="display:flex; justify-content:center; align-items:center; column-gap:20px; row-gap:10px; flex-wrap:wrap;"}

---

<br>
<div style="text-align:center;font-weight:bold;text-decoration:underline">Other sources:</div>

[<span>:material-open-in-new: pro.arcgis.com</span><br>Introduction to ArcGIS Pro](https://pro.arcgis.com/en/pro-app/latest/get-started/get-started.htm){ .md-button .md-button--primary .url-name target="\_blank"}
[<span>:material-open-in-new: pro.arcgis.com</span><br>Introducing ArcGIS Pro](https://pro.arcgis.com/en/pro-app/latest/get-started/introducing-arcgis-pro.htm){ .md-button .md-button--primary .url-name target="\_blank"}
{: align=center style="display:flex; justify-content:center; align-items:center; column-gap:20px; row-gap:10px; flex-wrap:wrap;"}

<hr class="l1">

### Adding data to the map

**Creating a map**:&nbsp;<code class="AGPF">:material-tab: Insert</code>&nbsp;→&nbsp;<code class="AGPF">:material-button-cursor: New Map</code>
![](../assets/cviceni1/img_09.png){: style="margin-left:calc((100vw \* 0.03) - 6px)"}
{: style="display:flex !important; justify-content:flex-start; align-items:center;"}

[:material-open-in-new: Create a map or scene](https://pro.arcgis.com/en/pro-app/latest/help/projects/add-maps-to-a-project.htm#GUID-660CA711-919A-44B0-952A-F2054937077B){ .md-button .md-button--primary .button_smaller target="\_blank"}
{: align=center style="display:flex; justify-content:center; align-items:center; column-gap:20px; row-gap:10px; flex-wrap:wrap;"}

---

**Adding data to the map** (stored locally): <code class="AGPF">:material-tab: Map</code> → <code class="AGPF">:material-button-cursor: Add Data</code> → <code class="AGPF">:material-button-cursor: Data</code> → select a file...

![](../assets/cviceni1/img_10.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_11.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_12.png)
{: .process_container}

<figcaption>If the file does not appear in the structure, the dialog can be refreshed with F5</figcaption>

[:material-open-in-new: Add data from the Add Data dialog box](https://pro.arcgis.com/en/pro-app/latest/help/mapping/layer-properties/add-layers-to-a-map.htm#ESRI_SECTION2_1C48753A1FD546F385580EF9197DBB8C){ .md-button .md-button--primary .button_smaller target="\_blank"}
{: align=center style="display:flex; justify-content:center; align-items:center; column-gap:20px; row-gap:10px; flex-wrap:wrap;"}

---

To avoid having to go through the directory structure each time to browse the data, it's a good idea to _join the data directories to the project_.

**Adding a directory to a project**: V _Catalog Pane_ ( <code class="AGPF">:material-tab: View</code> → <code class="AGPF">:material-button-cursor: Catalog Pane</code> ) right click on "_Folders_" select <code class="AGPF">:material-form-dropdown: Add Folder Connection</code> → insert or select a path... → drag & drop the data in the folder into the map area

![](../assets/cviceni1/img_05.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_04.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_06.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_23.png)
{: .process_container}

<figcaption>The path to the selected folder will remain in the menu under "Folders". The directory does not have to be local, e.g. a faculty disk H:\ can be mounted this way.</figcaption>

[:material-open-in-new: Connect to a folder](https://pro.arcgis.com/en/pro-app/latest/help/projects/connect-to-a-folder.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
[:material-open-in-new: The Project Pane](https://pro.arcgis.com/en/pro-app/latest/help/projects/the-project-pane.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
{: align=center style="display:flex; justify-content:center; align-items:center; column-gap:20px; row-gap:10px; flex-wrap:wrap;"}

---

...the same can be done with a geodatabase. The geodatabase stores data more efficiently, but you can't put anything in it.

**Connecting the geodatabase to the project**: In _Catalog Pane_ ( <code class="AGPF">:material-tab: View</code> → <code class="AGPF">:material-button-cursor: Catalog Pane</code> ) right click on "_Databases_" select <code class="AGPF">:material-form-dropdown: Add Database</code> → insert or select a path to geodatabase... → drag and drop the data in the folder into the map area

![](../assets/cviceni1/img_05.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_07.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_08.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_24.png)
{: .process_container}

<figcaption>The path to the selected geodatabase remains in the menu between the "Databases" items. Again, the path does not have to be local only.</figcaption>

[:material-open-in-new: Connect to a database](https://pro.arcgis.com/en/pro-app/latest/help/projects/connect-to-a-database.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
{: align=center style="display:flex; justify-content:center; align-items:center; column-gap:20px; row-gap:10px; flex-wrap:wrap;"}

---

**Layer order**: The map content (_Contents Pane_) shows all layers contained in the map. The visibility of each layer can be switched with the checkbox on the left. By changing the order of the layers in the table of contents, the order in which they are rendered in the map is changed.

![](../assets/cviceni1/img_29.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_30.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_31.png)
{: .process_container}

<figcaption>Contents Pane and reorder and toggle layer visibility</figcaption>

---

**Map settings**: In the _Contents Pane_ right-click on the map name to select<code class="AGPF">:material-form-dropdown: Properties</code>

![](../assets/cviceni1/img_21.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_22.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_25.png)
{: .process_container}

For starters, these items are of interest:

- **Tab "_General_"**:

  - **Name**
  - **Reference scale**: Fixes the size of the map symbology for the specified scale.
    [:material-open-in-new: Map reference scales](https://pro.arcgis.com/en/pro-app/latest/help/mapping/properties/map-reference-scales.htm){ .md-button .md-button--primary .button_smaller target="\_blank" align=right}
  - **Rotation**: Map rotation angle

- **Tab "_Coordinate systems_"**: Information about the map display coordinate system (separately for position and elevation).

  - WARNING**, if the coordinate system of the **inserted data** differs from the **map** system, the data is **temporarily** converted to the **map** coordinate system. However, this is an **On-the-fly** transformation, which is **simplified** for some coordinate system combinations, and the data may not relate to each other correctly. This situation is **not recommended** as it can produce **inaccurate results** for map visualization and data analysis. <a href="https://www.esri.com/arcgis-blog/products/arcgis-pro/mapping/projection-on-the-fly-and-geographic-transformations">**More information\*\*</a>
    {: style="color:#888;font-size:smaller; line-height:1.1;"}

<br>
<hr class="l1">

### Where to get data

**Locally stored files**: access via system path, e.g.:

_C:\Users\Student1\Documents\Geodatabase.gdb\Layer1_
{: align="center" style="font-size:smaller;line-height:1.1;"}

_\\\\data.fsv.cvut.cz\Shares\K155\Public\data\PragueRoads.gdb_
{: align="center" style="font-size:smaller;line-height:1.1;"}

**Online downloadable data**: download from any source to a local disk in the form of files, same access as with locally stored files (see above)

[:material-open-in-new: ArcČR](https://www.arcgis.com/home/item.html?id=16fd9804dac04020938452a77c1ed350){ .md-button .md-button--primary .button_smaller target="\_blank"}
[:material-open-in-new: Geoportal Praha](https://www.geoportalpraha.cz/cs/data/otevrena-data/seznam){ .md-button .md-button--primary .button_smaller target="\_blank"}
[:material-open-in-new: Geoportal data.Brno](https://data.brno.cz/explore){ .md-button .md-button--primary .button_smaller target="\_blank"}
[:material-open-in-new: otevřená data AOPK](https://gis-aopkcr.opendata.arcgis.com/){ .md-button .md-button--primary .button_smaller target="\_blank"}
{: align=center style="display:flex; justify-content:center; align-items:center; column-gap:20px; row-gap:10px; flex-wrap:wrap;"}

**Connecting streaming data**: _will be part of future exercises_
{: style="color:#888"}

- connection of data services via URL, does not require manual local storage, there are multiple standards for providing these services
  {: style="color:#888;font-size:smaller; line-height:1.1;"}

<br>
<hr class="l1">

### Map controls

**Explore Tool**: Movement in the map and pop-ups (pop-ups), see Fig.

- **Pop-up**: It is one of the basic elements of the graphical environment of GIS applications. Its (most common) purpose is to provide a quick preview of information about a given feature by clicking on its geometry. However, the form of the window is configurable and the editing tools very variable. By default, the pop-up displays a listing of attributes in table form (Figure).
  [:material-open-in-new: Pop-ups](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/pop-ups.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
- **Map scale**: Indicates the ratio of the map size to reality. In the corner of the map window (fig.) you can select from the offered scales or set any custom value.
  [:material-open-in-new: Map scales and scale properties](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/map-scales-and-scale-properties.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}

![](../assets/cviceni1/img_13.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_16.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_26.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_27.png)
{: .process_container}

[:material-open-in-new: Navigation](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/navigation-in-arcgis-pro.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
[:material-open-in-new: Navigate maps and scenes](https://pro.arcgis.com/en/pro-app/latest/get-started/navigate-your-data.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
{: align=center style="display:flex; justify-content:center; align-items:center; column-gap:20px; row-gap:10px; flex-wrap:wrap;"}

---

**Select Tool**: Map movement and interactive cursor selection. To deselect, see Fig.
{: #select-tool}

![](../assets/cviceni1/img_14.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_17.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_18.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_32.png)
{: .process_container}

[:material-open-in-new: Select features interactively](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/select-features-interactively.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
[:material-open-in-new: Select features for editing](https://pro.arcgis.com/en/pro-app/latest/help/editing/select-features-for-editing.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
{: align=center style="display:flex; justify-content:center; align-items:center; column-gap:20px; row-gap:10px; flex-wrap:wrap;"}

---

**Measure Tool**: Interactive measurement of distances, angles, etc.

![](../assets/cviceni1/img_15.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_19.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_20.png)
{: .process_container}

[:material-open-in-new: Measure](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/measure.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
{: align=center style="display:flex; justify-content:center; align-items:center; column-gap:20px; row-gap:10px; flex-wrap:wrap;"}

<br>
<hr class="l1">

<br>
<div style="text-align:center;font-weight:bold;text-decoration:underline">Additional resources:</div>

[<span>:material-open-in-new: pro.arcgis.com</span><br>ArcGIS Pro keyboard shortcuts](https://pro.arcgis.com/en/pro-app/latest/get-started/arcgis-pro-keyboard-shortcuts.htm){ .md-button .md-button--primary .url-name target="\_blank"}
[<span>:material-open-in-new: PDF</span><br>ArcGIS Pro shortcuts](https://www.esri.com/content/dam/esrisites/en-us/media/pdf/g526942-arcgis-pro-kybrd-shrtct-FINAL.pdf){ .md-button .md-button--primary .url-name target="\_blank"}
{: align=center style="display:flex; justify-content:center; align-items:center; column-gap:20px; row-gap:10px; flex-wrap:wrap;"}

<br>
<hr class="l1">

<br><br><br><br><br><br><br><br><br><br><br>

<!--
<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>



<hr class="l1">

<span style="font-size:50px;text-transform:uppercase;font-weight:800;">Test nadpisů:</span>

# Nadpis 1

## Nadpis 2

### Nadpis 3

#### Nadpis 4

##### Nadpis 5

###### Nadpis 6

...další text...

 -->
