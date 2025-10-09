---
icon: material/numeric-4-box
title: Practical 4
---

# Creating vector data, Editing tools, Calculate Field & Geometry

Lecturer: <!-- Cvičící:  -->![](https://geomatics.fsv.cvut.cz/wp-content/uploads/2022/01/03-edit_export@0.3x.jpg){: .off-glb .no-filter style="height: 1.5em; vertical-align: -.4em; clip-path: circle();"} 
[__Vojtěch Cehák__](mailto:vojtech.cehak@fsv.cvut.cz)

## Data

[:material-download: Geodatabase :material-database:](https://geo.fsv.cvut.cz/courses/155GISE/Practical04/Practical04.gdb.zip){ .md-button .md-button--primary .button_smaller }
[:material-download: Layer File :material-layers:](https://geo.fsv.cvut.cz/courses/155GISE/Practical04/Orthophoto_Czechia.lyrx){ .md-button .md-button--primary .button_smaller }
{: .button_array style="justify-content:flex-start;"}

<hr class="level-1">

## Workflow

### Inspect the Data

__Download the data__ and __add them to a new map__ in :simple-arcgis: ArcGIS Pro.

Scan the data visually – __inspect the attributes and their values__

Layers in the Geodatabase:

<div id="id_01" class="table_no_cell_padding table_no_cell_min_width centered_tab_labels" markdown>
|Layer Name|Geometry Type|Note|
|:--------:|:-----------:|:--:|
|AOI|:material-vector-polygon: polygon|Area of interest|
|Buildings|:material-vector-polygon: polygon|Building Footprints|
|Buildings_REPORTED_ERRORS|:material-vector-polygon: polygon|Errors of the data reported by other users|
|PublicTransportationStops|:material-vector-point: point|Public Transportation Stops|
|Streets|:material-vector-line: line|Street Network|
</div>

---

### Data Preparation

The layer _:material-vector-point: PublicTransportationStops_{.outlined} contains too many records. __Limit the records to the area of interest only__, use a `spatial query` to do so.

---

### Creating additional data

#### 1. PUBLIC TRANSPORTATION STOPS

Using the OpenStreetMap basemap, __find 5 missing bus stops near the faculty__ and __add the missing geometry to the correct layer__ ( _:material-vector-point: PublicTransportationStops_{.outlined} )

__Add 4 additional bus stops by inserting coordinates__ (see below)
<div id="id_01" class="table_no_cell_padding table_no_cell_min_width centered_tab_labels" markdown>
|X|Y|
|-|-|
|1601729,8432|6464830,9824|
|1601748,3756|6464803,9781|
|1602125,1092|6463800,7206|
|1602504,0565|6463309,2208|
</div>

#### 2. STREETS

__Add pedestrian streets in front of the faculty__, try tools such as Parallel, Perpendicular, Direction, Distance, Absolute XYZ, Reverse Direction

#### 3. BUILDINGS

__Add missing buildings in the university campus area__, try tools such as Parallel, Perpendicular, Distance, Square and Finish, use snapping

---

### Editing data

__Inspect the possibilities of the Select Tool__ (select by drawing different shapes, add features to selection, remove features from selection, where to get the number of selected features)

__Find incorrectly placed buildings and delete them__. Use the aerial map layer hidden in the Layer File downloaded previously.

__Use editing tools to edit buildings with incorrect geometry__, try tools such as Move, Rotate, Edit Vertices, Split, Merge.

Use the layer _:material-vector-polygon: Buildings_REPORTED_ERRORS_{.outlined} as a guide.

---

### Field Calculator




<hr class="level-1">