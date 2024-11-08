---
icon: material/numeric-7-box
title: Practical 7
---

# Geoprocessing tools for raster data

“A DEM is a raster representation of a continuous surface, usually referencing the surface of the earth. The accuracy of this data is determined primarily by the resolution (the distance between sample points). Other factors affecting accuracy are data type (integer or floating point) and the actual sampling of the surface when creating the original DEM.” (pro.arcgis.com)

“The CORINE Land Cover is provided for 1990, 2000, 2006, 2012, and 2018. This vector-based dataset includes 44 land cover and land use classes. The time-series also includes a land change layer, highlighting changes in land cover and land-use.” (land.copernicus.eu)

__Resources:__
{: align=center }

[<span>pro.arcgis.com</span><br>Exploring Digital Elevation Models](https://pro.arcgis.com/en/pro-app/latest/tool-reference/spatial-analyst/exploring-digital-elevation-models.htm){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>land.copernicus.eu</span><br>CORINE Land Cover](https://land.copernicus.eu/pan-european/corine-land-cover){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>land.copernicus.eu</span><br>CORINE Land Cover Guide](https://land.copernicus.eu/user-corner/technical-library/corine-land-cover-nomenclature-guidelines/html){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
{: .button_array}

## Assignment: Indicate areas of avalanche risk
The aim of this training is to provide experience with real-world GIS tasks. Your knowledge and skills acquired from previous lessons will be used when processing the task.
Your mission will be to evaluate which slopes are prone to avalanches and possible threats to the surroundings. You are going to monitor the situation within one selected Czech national parc.
An essential part, without which the work cannot be done, is the acquisition of data from publicly available sources and the subsequent modification of the data in the GIS environment so that you can perform future analysis with them. At the beginning, you will receive a package of input data containing, in particular, a digital elevation model. Based on the DEM, it will be your task to process and evaluate which slopes are prone to avalanche danger. To evaluate an avalanche slope, you need to know slope inclination, elevation, wind speed, and land cover.

Criteria indicating a dangerous hillside with avalanche hazard potencial:

•	Area in the highest third of assigned national parc

•	Slope > 30°

•	CLC land cover code = 2.X.X or 3.X.X (except for 3.1.1, 3.1.2, and 3.1.3)

•	Peaks in windier half of assigned national parc

Input [Data Package](/docs/assets/cviceni7/AvalancheRisk.gdb.zip) includes:

•	Digital elevation model (DEM)

•	Wind speed measurement

•	Corine Land Cover (CLC)

•	Czechia protected land areas


**1.** Exploring Input Data

First of all, it’s always essential to start with exploring input data, understand the data types or browse the attribute tables for instance.

•	Czech DEM is a raster which stores values of height above sea level.

•	Czech protected land areas is a polygon feature layer containing polygons of national parks, etc.

•	Wind speed measurement is a point feature layer of measurement units in Czechia with average measured wind speed.

•	Corine Land Cover is a classified raster including many land cover and land use classes.

**2.** Get Your Input Data Ready

•	Set Křovák projection (EPSG: 5514)

•	Use definition query to display assigned Czech national parc. Picture below is displaying Krkonoše national parc using definition query; DEM in the background.

![](../assets/cviceni7/Obrázek1){ .no-filter .off-glb}
{: align=center}
 
•	Use Extract by Mask tool to clip raster by assigned national parc polygon.


