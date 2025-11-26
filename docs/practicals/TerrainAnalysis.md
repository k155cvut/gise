---
icon: material/numeric-7-box
title: Practical 7
---

# Terrain analysis, map algebra

## Basic terms

<div class="grid_container">
  <div class="grid_item" style="flex:1 1 300px;">
    <strong>Terrain Analysis</strong>
    <hr style="margin:5px 0 !important;">
    <p> <strong>Terrain analysis</strong>  refers to a set of GIS techniques used to describe and interpret the shape of the Earth’s surface. By deriving information such as slope, aspect or curvature from a digital elevation model, terrain analysis helps us understand how topography influences natural processes, accessibility, visibility and spatial patterns in the landscape.</p>
  </div>
  <br>
  <div class="grid_item" style="flex:1 1 300px;">
    <strong>Map algebra</strong>
    <hr style="margin:5px 0 !important;">
    <p> <strong>Map algebra</strong> is a framework for performing cell-by-cell operations on raster data. It allows users to combine multiple raster layers using mathematical expressions, logical conditions or statistical functions. Through map algebra, it becomes possible to model environmental suitability, classify risk zones or derive new thematic layers from existing datasets.</p>
  </div>
  <br>
  <div class="grid_item" style="flex:1 1 300px;">
    <strong>Interpolation</strong>
    <hr style="margin:5px 0 !important;">
    <p> <strong>Interpolation</strong> is a method used to estimate unknown values at unsampled locations based on measurements taken at known points. In GIS, interpolation creates continuous surfaces — such as elevation, temperature or pollution concentration — from discrete observations. This helps reveal spatial gradients and provides input for further spatial analyses.</p>
  </div>
</div>
<br>

**Learn more:**
{: align=center }

[<span>pro.arcgis.com</span><br>How Surface Parameters works](https://pro.arcgis.com/en/pro-app/latest/tool-reference/3d-analyst/how-surface-parameters-works.htm){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>pro.arcgis.com</span><br>Introduction to map algebra](https://pro.arcgis.com/en/pro-app/3.4/help/analysis/spatial-analyst/mapalgebra/what-is-map-algebra.htm){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>pro.arcgis.com</span><br>Understanding interpolation analysis](https://pro.arcgis.com/en/pro-app/latest/tool-reference/spatial-analyst/understanding-interpolation-analysis.htm){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>pro.arcgis.com</span><br>An introduction to interpolation methods](https://pro.arcgis.com/en/pro-app/latest/help/analysis/geostatistical-analyst/an-introduction-to-interpolation-methods.htm){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>pro.arcgis.com</span><br>Comparing interpolation methods](https://pro.arcgis.com/en/pro-app/latest/tool-reference/spatial-analyst/comparing-interpolation-methods.htm){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
{: .button_array}

## Assignment 05
!!! abstract "Areas of avalanche risk in the Krkonoše National Park"
    **TASK:**

    Based on the analysis of provided data, make a map showing the areas of avalanche risk in [the Krkonoše National Park](https://en.wikipedia.org/wiki/Krkono%C5%A1e_National_Park){target="_blank"}.

    Areas of the avalanche risk are defined according to the following criteria:

    1. elevation
    
        - the highest third of the national pak

    2. slope/inclination
    
        - more than 30°

    3. land cover
    
        - land cover code = 2.X.X or 3.X.X (except for 3.1.1, 3.1.2, and 3.1.3)

    4. wind speed
    
        - windier half of the national park


    <br>
    In technical report answer following questions:
    
    - What proportion of the Krkonoše National Park (in %) lies within the zone most at risk of avalanches?
    - What proportion of the Krkonoše National Park (in %) lies outside the avalanche-risk zone (i.e. the sum of all criteria is 0)?


    <br>
    **DATA SOURCES:**

    - [Digital elevation model (DEM)](https://pro.arcgis.com/en/pro-app/latest/tool-reference/spatial-analyst/exploring-digital-elevation-models.htm){target="_blank"}

    - Wind speed measurement

    - [Corine Land Cover (CLC)](https://land.copernicus.eu/pan-european/corine-land-cover){target="_blank"}

    - Czechia protected land areas

        
      [:material-download: Data for avalanche risk map :material-layers:](../assets/TerrainAnalysis/AvalancheRisk.gdb.zip){ .md-button .md-button--primary .button_smaller }
        {: .button_array style="justify-content:flex-start;"}

         
    **SUBMISSION FORM:**

    - technical report + map in PDF format (submit by 07/12, send to <a href="mailto:petra.justova@fsv.cvut.cz">petra.justova@fsv.cvut.cz</a>)

    [:material-download: Technical report template :material-layers:](../assets/cviceni2/technical_report.doc){ .md-button .md-button--primary .button_smaller }
      {: .button_array style="justify-content:flex-start;"}
    

    **INSTRUCTIONS:**

    **1. Explore input data**

    - First of all, it’s always essential to start with exploring input data, understand the data types or browse the attribute tables for instance.
            
        - ``DMR`` is a raster which stores values of height above sea level for the area of Czechia.

        - ``CzechProtected`` is a polygon feature layer containing polygons of parts of the Krkonoše National Park.

        - ``windSpeed`` is a point feature layer of measurement units in Czechia with average measured wind speed.

        - ``CORINE`` is a classified raster including many land cover and land use classes.

    **2. Data Preparation**

    - Clip both rasters to the extent of Krkonoše National Park *(Extract by Mask)*

    **3. Terrain Analysis**

    - In the following step, a set of spatial analysis tools together with subsequent reclassification will be processed to calculate and classify elevation and slope (steepness). Later on, you will deal with reclassification of Corine Land Cover raster and finally, suitable interpolation method will be used to help you process wind speed data.

    - Use Slope function to calculate the steepness. Use extracted raster by your national park as an input raster. The output should be similar to following picture.

        ![](../assets/cviceni7/Obrázek2.png){ .no-filter .off-glb}
        {: align=center}
        
    - Use Reclassify tool to change the values in slope raster. Basically, you’re interested in two categories: 0°–30° and 30°–90° so you can define new values: 0 and 1. Zero stands for “doesn’t meet the criteria”.

        ![](../assets/cviceni7/Obrázek3.png){ .no-filter .off-glb}
        {: align=center}
        
    - Similarly you need to reclassify your extracted DEM to decide, which values are within the highest third of national park. In Krkonoše national park, the highest third is indicated by violet color (see the picture below).

        ![](../assets/cviceni7/Obrázek4.png){ .no-filter .off-glb}
        {: align=center}
        
    - By this time, you should have two reclassified raster layers (elevation and slope). Now it’s time to do the same with CORINE Land Cover data. Such raster reclassification might look a little bit sophisticated since you have to discover and use the land cover codes in the attribute table. The criteria in the assignment are clear enough so it is going to be an easy job anyway. For more detail on the land cover classification see [CLC illustrated nomenclature guidelines](https://land.copernicus.eu/content/corine-land-cover-nomenclature-guidelines/docs/pdf/CLC2018_Nomenclature_illustrated_guide_20190510.pdf){target="_blank"}

    - If you were successful to reclassify three raster layers, you can move to wind speed feature layer. You’ve processed only raster data so far. Since you need to use raster calculator in the very ending, your final outputs have to be raster layers, so it is necessary to “transform” a point layer using some math into a raster (continuous surface).

        !!! note-grey "Note"

            “Interpolation predicts values for cells in a raster from a limited number of sample data points. It can be used to predict unknown values for any geographic point data, such as elevation, rainfall, chemical concentrations, and noise levels.” (pro.arcgis.com)


    - Using some of the links above, you can compare interpolation methods and choose the best one (or at least suitable) for point data. For this purpose, Inverse distance weighing (IDW) looks promising. Fill speed attribute as a Z field value and don’t forget to define an Output cell size (should be consistent for all your raster layers).

    - The output should be calculated for entire Czech Republic and clipped by national park polygon subsequently (if you first clip than interpolate, your result won’t be accurate)

    - Afterwards, the last reclassification is ahead: you have to detect a windier part of assigned national park

    **4. Combine the criteria and find out the result!** 

    - Now is time for the best part of solution: combining the reclassified raster layers and finding out risky areas. All you need is to use Raster Calclulator and compile an appropriate algebraic expression. Your raster layers include only values of 0 and 1. As it’s mentioned above, zero is against the criteria. The final question is, how to construct four values as an algebra expression so the resulting raster layer would consist of values 0 and 1 again and zero would stand for “safe” slopes? Zero will represent for example an area in windier part & lower half of national park or area in the highest third of national park & having land cover code 1.2.1.

        ![](../assets/cviceni7/Obrázek5.png){ .no-filter .off-glb}
        {: align=center}

    - Avalanche risk in national park Krkonoše is red-colored in the picture below. It is possible to make the final raster semi-transparent and set Czech orthophoto as a background map to better illustrate the result for instance.

        ![](../assets/cviceni7/Obrázek6.png){ .no-filter .off-glb}
        {: align=center}

    - Another approach could be represented by symbolizing different levels of avalanche risk, which can be reached if you change the expression in raster calculator. Instead of multiplying the values of four raster layers, you can simply sum them up. Output will consist of 5 different values: 0, 1, 2, 3, or 4. Change raster symbology afterwards to indicate increasing avalanche risk according to the that values.


    **5. Visualize the results**

    - Set the symbolization of all different levels of avalanche risk properly. 
    - In *New Layout* (A4 Landscape) insert the Map Title, Scale and Credits.
    - Export *Layout* in PDF Format


 
