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

__Resources:__
{: align=center }

[<span>pro.arcgis.com</span><br>GCS vs. PCS](https://www.esri.com/arcgis-blog/products/arcgis-pro/mapping/gcs_vs_pcs/){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>pro.arcgis.com</span><br>Coordinate systems](https://www.esri.com/arcgis-blog/products/arcgis-pro/mapping/coordinate-systems-difference/){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>learn.arcgis.com</span><br>Understand projections](https://learn.arcgis.com/en/projects/choose-the-right-projection/#understand-projections){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
{: .button_array}

!!! note-grey "Note"

    *Projection on the fly* is what ArcGIS does to **resolve conflicts** when your data is in a different coordinate system than your map. It does this so the data can draw in the correct place on the map. *Projection on the fly* ensures that the data draws in the map’s coordinate system, even though it is still stored in other coordinate systems. ArcGIS will **always** apply *projection on the fly* when it’s needed. It can’t draw the data on your map otherwise.

__Exercices:__
{: align=center }

[<span>learn.arcgis.com</span><br>Fix data when it appears on a wrong place](https://learn.arcgis.com/en/projects/fix-data-when-it-appears-in-the-wrong-place/){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
[<span>learn.arcgis.com</span><br>Choose the right projection](https://learn.arcgis.com/en/projects/choose-the-right-projection/){ .md-button .md-button--primary .server_name .external_link_icon_small target="_blank"}
{: .button_array}