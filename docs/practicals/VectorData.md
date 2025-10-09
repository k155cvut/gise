---
icon: material/numeric-3-box
title: Practical 3
---

# Vector data, attribute queries, spatial queries

__Spatial data__ is any type of data that directly or indirectly references a specific geographical area or location. A location can be represented not only by a combination of coordinates (X + Y, latitude + longitude, etc.), but also by, for example, an address (of arbitrary detail). The two most common data formats used to store (geo)spatial data are vector and raster.

## Spatial data types

<div class="grid cards" markdown>

-   :material-vector-polyline:{ .lg .middle } __Vector data__

    ---

    - represent elements of the real world using basic geometric elements: __points, lines and surfaces__ (called polygons)

    - the detail of the data is determined by the __detail of the coordinates of the vertices__ of the geometric feature

    - suitable for modelling and analysis of __discrete objects__ (e.g. location of points, land cover categories)

    - suitable for __map creation, length measurements, geometric calculations__

    - possible problems with __topology__ (gaps and overlaps)

    - basic vector data formats are __Esri Shapefile, GeoJSON, GeoPackage__ or __KML/GML__



-   :material-grid:{ .lg .middle } __Raster data__

    ---

    - represent real world elements in the form of a regular grid made up of  __pixels__ (from *picture element*)

    - the detail of the data is determined by the __spatial resolution__ of the grid, i.e. the __size__ of the __pixel__ edge (in meters)

    - suitable for modeling and analysis of __continuous phenomena__ (elevation, temperature, precipitation)
    
    - used for __image data__ (e.g. satellite imagery)

    - raster datasets can become potentially very large

    - basic raster data formats are __GeoTIFF, JPEG, PNG__ or __GIF__


</div>


<figure markdown>
  ![Difference in graphical representation of vector and raster data](../assets/cviceni3/VectorVsRaster.png "Difference in graphical representation of vector and raster data"){ width=600px }
  <figcaption>Difference in graphical representation of vector and raster data (Geletič et al. 2019)</figcaption>
</figure>


## Contents

### Attribute queries

Attribute Query is a method of selecting/filtering elements based on __attribute values__. It complements the interactive feature selection method from practical 1. The basis is a selection rule - called __Expression__. ArcGIS Pro allows you to build expressions interactively using a dialog, but to use the full potential of expressions, it is recommended to use SQL code.
<br><br>

__Attribute query__ (over map data): _:material-tab: Map_{: .outlined} → _:material-button-cursor: Select By Attributes_{: .outlined} → fill in the dialog...
[Select features using attributes](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/select-features-using-attributes.htm){ .md-button .md-button--primary .button_smaller .external_link_icon target="_blank"}

![](../assets/cviceni1/img_33.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_34.png)
![](../assets/cviceni1/arrow.svg){: .off-glb .process_icon}
![](../assets/cviceni1/img_35.png)
{: .process_container}

<figcaption markdown>The `Input Rows` field is automatically prepopulated with the layer selected in the map content</figcaption>

Using the ![](../assets/cviceni1/img_36.png){: .off-glb style="vertical-align: -20%;margin:0px 5px;"} you can change the notation between the interactive dialog entry and the SQL expression.

[Introduction to query expressions](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/write-a-query-in-the-query-builder.htm){ .md-button .md-button--primary .button_smaller .external_link_icon target="\_blank"}
[Construct and modify queries](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/construct-and-modify-queries.htm){ .md-button .md-button--primary .button_smaller .external_link_icon target="\_blank"}
{: .button_array}

<style>
  details.page_color_admonition summary:first-child::before {background-color:var(--md-primary-fg-color) !important;}
  /* details.page_color_admonition summary:first-child         {color:#009485 !important;} */
  details.page_color_admonition summary:first-child::after  {color:var(--md-primary-fg-color) !important;}
  details.page_color_admonition {border-color: var(--md-primary-fg-color) !important;margin:50px 0px;}
  details.page_color_admonition summary {background-color: #4051b51a !important;}
</style>
<details class="task-fg-color page_color_admonition" open="">
  <summary>Example to try<div style="display:inline-block; border-left: 1px solid var(--md-admonition-fg-color); height:.9rem;vertical-align:-20%;margin:0px 20px"></div><span style="font-weight:normal;">testing attribute queries on real data</span></summary>
  <iframe style="filter:none !important;margin-top:.6rem;" width="100%" height="500" frameborder="0" allowfullscreen src="https://geo.fsv.cvut.cz/data/hoffmann/appqueryGISE/"></iframe>
  <hr class="level-1" style="margin-top:5px !important; margin-bottom:0px !important;">
  <div style="margin-top:10px;margin-left:10px;font-weight:bold;font-size:larger;">Layer attributes scheme:</div>
  
  <div class="table_small_padding">
  <table>
    <tr>
      <th>attribute</th>
      <th>data type</th>
      <th>description</th>
    </tr>
    <tr>
      <td>FEATURECLA</td>
      <td><code>String</code></td>
      <td>Populated places classification</td>
    </tr>
    <tr>
      <td>NAME</td>
      <td><code>String</code></td>
      <td>Name of the populated place</td>
    </tr>
    <tr>
      <td>WORLDCITY</td>
      <td><code>Integer</code></td>
      <td>Whether the place is classified as a World city, <br><code>0=no</code>, <code>1=yes</code></td>
    </tr>
    <tr>
      <td>MEGACITY</td>
      <td><code>Integer</code></td>
      <td>Whether the place is classified as a Mega city, <br><code>0=no</code>, <code>1=yes</code></td>
    </tr>
    <tr>
      <td>SOV0NAME</td>
      <td><code>String</code></td>
      <td>Name of the sovereign country</td>
    </tr>
    <tr>
      <td>ADM0NAME</td>
      <td><code>String</code></td>
      <td>Name of the admin country</td>
    </tr>
    <tr>
      <td>ADM1NAME	</td>
      <td><code>String</code></td>
      <td>Name of the First-level administrative devision in a country</td>
    </tr>
    <tr>
      <td>LATITUDE</td>
      <td><code>Double</code></td>
      <td>Latitude</td>
    </tr>
    <tr>
      <td>LONGITUDE</td>
      <td><code>Double</code></td>
      <td>Longitude</td>
    </tr>
    <tr>
      <td>POP_MAX</td>
      <td><code>Double</code></td>
      <td>Estimate of inhabitants of the place <b>with</b> urban agglomeration</td>
    </tr>
    <tr>
      <td>POP_MIN</td>
      <td><code>Double</code></td>
      <td>Estimate of inhabitants of the place <b>without</b> urban agglomeration</td>
    </tr>
    <tr>
      <td>TIMEZONE</td>
      <td><code>String</code></td>
      <td>Name of the timezone</td>
    </tr>
  </table>
  </div>
</details>

<hr class="level-1">

### Spatial queries

Spatial Query is a method of selecting/filtering elements of one layer based on their relative position with elements of another layer. The function uses as input the __`layer of selected elements`__, the __`layer for overlay analysis`__ a the __`relationship for overlay analysis`__.

<!-- ![](https://geo.fsv.cvut.cz/data/cehak/155SGEA/img_01.svg){ .off-glb .no-filter }
![](https://geo.fsv.cvut.cz/data/cehak/155SGEA/img_02.svg){ .off-glb .no-filter }
{: .process_container style="flex-wrap:wrap; row-gap: 10px;"} -->

![](https://geo.fsv.cvut.cz/data/cehak/155SGEA/img_01.svg){ .no-filter }
![](https://geo.fsv.cvut.cz/data/cehak/155SGEA/img_02.svg){ .no-filter }
{: .process_container}

<div class="table_headerless table_small_padding table_centered centered_tab_labels" markdown> <!-- trik: vlastnosti tabulky pro vsechny podrizene -->

=== "Select POINTS..."

    === "...using POINTS"

        ![](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/GUID-1ECFFABC-3608-4BB4-86A8-FD6FA0F16C13-web.gif){ style="filter:none !important;" }
        {: align=center}

        <table style="width:unset;">
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

=== "Select LINES..."


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
        
</div>

<!-- <figcaption markdown>zdroj: [Select By Location graphic examples](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/select-by-location-graphical-examples.htm)</figcaption> -->


[:material-open-in-new: Select features by location](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/select-features-by-location.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
[:material-open-in-new: Select Layer By Location (Data Management)](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/select-layer-by-location.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
[:material-open-in-new: Select By Location graphic examples](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/select-by-location-graphical-examples.htm){ .md-button .md-button--primary .button_smaller target="\_blank"}
{: align=center style="display:flex; justify-content:center; align-items:center; column-gap:20px; row-gap:10px; flex-wrap:wrap;"}

<br><br><br><br><br><br>

<!-- ## Zadání domácího úkolu k semestrální práci -->


