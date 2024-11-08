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
**1.** Exploring Input Data

First of all, it’s always essential to start with exploring input data, understand the data types or browse the attribute tables for instance.

•	Czech DEM is a raster which stores values of height above sea level.

•	Czech protected land areas is a polygon feature layer containing polygons of national parks, etc.

•	Wind speed measurement is a point feature layer of measurement units in Czechia with average measured wind speed.

•	Corine Land Cover is a classified raster including many land cover and land use classes.


