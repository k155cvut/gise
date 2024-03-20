---
icon: material/numeric-3-box
title: Practical 3
---

# Coordinate systems

## Basic terms

### Geographic vs. Projected coordinate system

<div class="grid_container">
  <div class="grid_item" style="flex:1 1 300px;">
    <strong>Geographic coordinate system</strong>
    <hr style="margin:10px 0 !important;">
    <p>Defines <strong>where</strong> the data is located on the model of Earth’s surface.</p>
    <p>A GCS is <strong>round</strong>, and so records locations in angular units (usually degrees).</p>
  </div>
  <div class="grid_item" style="flex:1 1 300px;">
    <strong>Projected coordinate system</strong>
    <hr style="margin:10px 0 !important;">
    <p>Tells the data <strong>how</strong> to draw on a flat surface, like on a paper map or a computer screen.</p>
    <p>A PCS is <strong>flat</strong>, so it records locations in linear units (usually meters).</p>
  </div>
</div>

![](../assets/cviceni2/CS.png){ .no-filter .off-glb}
{: align=center}

**Resources:**
{: align=center }

[<span>pro.arcgis.com</span><br>GCS vs. PCS](https://www.esri.com/arcgis-blog/products/arcgis-pro/mapping/gcs_vs_pcs/){ .md-button .md-button--primary .server_name .external_link_icon_small target="\_blank"}
[<span>pro.arcgis.com</span><br>Coordinate systems](https://www.esri.com/arcgis-blog/products/arcgis-pro/mapping/coordinate-systems-difference/){ .md-button .md-button--primary .server_name .external_link_icon_small target="\_blank"}
[<span>learn.arcgis.com</span><br>Understand projections](https://learn.arcgis.com/en/projects/choose-the-right-projection/#understand-projections){ .md-button .md-button--primary .server_name .external_link_icon_small target="\_blank"}
{: .button_array}

!!! note-grey "Note"

    *Projection on the fly* is what ArcGIS does to **resolve conflicts** when your data is in a different coordinate system than your map. It does this so the data can draw in the correct place on the map. *Projection on the fly* ensures that the data draws in the map’s coordinate system, even though it is still stored in other coordinate systems. ArcGIS will **always** apply *projection on the fly* when it’s needed. It can’t draw the data on your map otherwise.

**Exercices:**
{: align=center }

[<span>learn.arcgis.com</span><br>Fix data when it appears on a wrong place](https://learn.arcgis.com/en/projects/fix-data-when-it-appears-in-the-wrong-place/){ .md-button .md-button--primary .server_name .external_link_icon_small target="\_blank"}
[<span>learn.arcgis.com</span><br>Choose the right projection](https://learn.arcgis.com/en/projects/choose-the-right-projection/){ .md-button .md-button--primary .server_name .external_link_icon_small target="\_blank"}
{: .button_array}

## Explore the impact of projection with interactive apps

### Web Mercator distortion

The Web Mercator projection, an adapted version of the Mercator projection, has become the default map projection for web mapping. Unlike its predecessor, it employs a spherical formula consistently across all scales. Major online map providers, such as Google Maps, CARTO, Mapbox, OpenStreetMap, Esri, and others, widely employ this projection.

The primary advantage of the Mercator projection, and consequently the Web Mercator, is its preservation of direction, providing users with the valuable knowledge that north is consistently oriented upwards. Despite even distortion throughout most areas, as one moves away from the equator, distortion intensifies, causing significant stretching toward the poles. Consequently, the Web Mercator projection is unsuitable for polar displays. Due to these apparent distortions, it is not recommended for spatial analysis or area calculations.

<iframe style="filter:none !important;margin-top:.6rem;" width="100%" height="500" frameborder="0" allowfullscreen src="https://www.thetruesize.com/#?borders=1~!MTU2ODg0MjU.NDY3MTc3NQ*MzEyNTI5MDA(NjIzOTIyOA~!CONTIGUOUS_US*MTAwMjQwNzU.MjUwMjM1MTc(MTc1)MQ~!IN*NTI2NDA1MQ.Nzg2MzQyMQ)MA~!CN*OTkyMTY5Nw.NzMxNDcwNQ(MjI1)Mg"></iframe>

<iframe style="filter:none !important;margin-top:.6rem;" width="100%" height="500" frameborder="0" allowfullscreen src="https://developers.arcgis.com/javascript/latest/sample-code/client-projection/live/"></iframe>
