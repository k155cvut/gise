---
icon: material/numeric-5-box
title: Practical 5
---
# Georeferencing
Raster data is obtained from many sources, such as satellite images, aerial cameras, and scanned maps. Unlike modern satellite images and aerial cameras that tend to have relatively accurate location information and might need only slight adjustments to line up all your GIS data, scanned maps and historical data usually do not contain any spatial reference information. In these cases you need to use the process of georeferencing. 

Georeferencing is the process of assigning real-world geographic coordinates to a raster image or a scanned map, enabling it to be accurately placed within a spatial reference system. This process involves matching identifiable points on the image with corresponding locations on a reference dataset, such as a satellite image or a vector map. Georeferencing is essential in cartography and GIS, as it allows historical maps, aerial photographs, or other spatial data to be integrated with modern geographic information for analysis, visualization, and decision-making.


<figure markdown>
  ![Georeferencing an old map](../assets/Georeferencing/GeoreferencingMap.png "Georeferencing an old map"){ width=600px }
  <figcaption>Georeferencing an old map</figcaption>
</figure>


__Resources:__
{: align=center }

[<span>pro.arcgis.com</span><br>Overview of georeferencing](https://pro.arcgis.com/en/pro-app/latest/help/data/imagery/overview-of-georeferencing.htm){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>pro.arcgis.com</span><br>Understanding Raster Georeferencing](https://www.esri.com/about/newsroom/arcuser/understanding-raster-georeferencing/){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>pro.arcgis.com</span><br>Georeferencing tools](https://pro.arcgis.com/en/pro-app/latest/help/data/imagery/georeferencing-tools.htm){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>learn.arcgis.com/</span><br>Georeference historical imagery in ArcGIS Pro](https://learn.arcgis.com/en/projects/georeference-imagery-in-arcgis-pro/){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
{: .button_array}

<hr class="level-1">


## Assignment 03
!!! abstract "Urban development of the city"
    **TASK:**

    Make a map showing the urban development of chosen city (your hometown, the capital of your country, ...). Derived the extent of built-up areas from old maps (try to show at least three time periods including this year). Try to quantify the change (in relative and absolute numbers).

    <br>
    In technical report answer following questions:
    
    - How has the extent of built-up area changed during the whole time period (relatively and absolutely)?


    <br>
    **DATA SOURCES:**
    
      [:material-map: Plan of Prague (1920–1930)](../assets/cviceni4/Prague_Plan_1920-1930_detail.jpg){ .md-button .md-button--primary .button_smaller }
      {: .button_array style="justify-content:flex-start;"}
    
    <br>
    **SUBMISSION FORM:**

    - technical report + 1 map in PDF format (submit by 23/03, send to <a href="mailto:petra.justova@fsv.cvut.cz">petra.justova@fsv.cvut.cz</a>)
    
    <div class="annotate" markdown>
    <br>
    **INSTRUCTIONS:**
    
    **Step 1:** **Find a map**
    
    - Search the browser or digital map collections to find the old map of your chosen city <br>
    *(If you find an already georeferenced map that is provided as a [WMS/WMTS]("A Web Map Service (WMS) or Web Map Tile Service (WMTS) are standard protocols for serving geospatial data as images (e.g., PNG, JPEG) over the web. It allows clients to request maps and map layers from a server and display them on a map viewer or client application."), connect it to ArcGIS Pro __(1)__{title="How to add WMS/WMTS service to ArcGIS Pro"}. and proceed to step 3)*

    [OldMapsOnline](https://www.oldmapsonline.org/){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
    [David Rumsey Map Collection](https://www.davidrumsey.com/){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
    {: .button_array}


    - If you want to use another (older) plan of Prague, you can use [:material-map: Jüttner's plan of Prague (1816)](https://gs-pub.praha.eu/arcgis/rest/services/arch/mapove_podklady_archiv/MapServer/1){ .md-button .md-button--primary .button_smaller }
    <br>
    *(Jüttner's plan of Prague (1816) is already georeferenced and provided via [ArcGIS REST service]("ArcGIS REST Service is a web service (such as WMS or WMTS) that allows users to access and interact with geographic data and GIS functionalities over the internet using RESTful APIs. It enables querying, visualization, and analysis of spatial data from ArcGIS Server in applications and web maps."), just copy the URL and add the map to ArcGIS Pro __(2)__{title="How to add data from path"}, and proceed to step 3)*
        
    <br>
    **Step 2:** **Georeference the map**

    - Add the old map to your *Map project*.
    - Set the projection of *Map* properly (Properties-Coordinate Systems)
    - Activate the *Georeference* tool (*Imagery* tab).
    - Zoom in to the area of interest (area covered by the old map). Save the map display to *Bookmarks* (*Map* tab).
    - On the *Georeference* tab choose *Fit to Display* to reposition and place the image within the current map display. You can use *Move/Scale/Rotate* tool to refine the approximate placement of the image for better identification of control points for georeferencing in next step.
    - On the *Georeference* tab, click *Add Control Points*. Now try to find at least 4 identical points (control points) on the image *(source)* and the reference map *(target)*. These points should be spread out throughout the image to obtain the best possible registration.
    - After collecting all points, on the *Georeference* tab, click *Save*.

        <br>
    **Step 3:** **Vectorization**

    - Create new feature class *(Catalog-Databases-New-Feature Class)*. Choose the feature geometry, add fields for attributes you want to record *(“year”)* and choose the right coordinate system.
    - Vectorize the extent of built-up area for all georeferenced maps (*Edit-Features-Create Feature*). For each polygon, i.e. an old map, enter the value for *“year”* attribute.
    - Symbolize the layer properly to show the urban expansion of your city *(Symbology-Graduated Colors)*. Overlay the layers on a reference map that reflects the current extent of built-up area *(Map-Layer-Basemap)*.
    - Finish the layout: insert *Map Title*, *Scale*, *Legend* and *Credits*. Feel free to make it nice! You can see an inspiration for your output below. <br>
    - Export *Layout* in PDF Format

    </div>

    1.  ![](../assets/cviceni4/ServerConnection.png){ .no-filter width=700px} Add WMS/WMTS service to ArcGIS Pro
    2.  ![](../assets/cviceni4/AddDataFromPath.png){ .no-filter width=700px} Add data from path to ArcGIS Pro

    <br>
    ![](../assets/cviceni4/PragueMap.png){ width=600px }
    {: align=center}


    

    