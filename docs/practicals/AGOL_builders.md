---
icon: material/numeric-10-box
title: Practical 10
---

# ArcGIS Online
In a typical web GIS workflow, individual components build on each other:

**data → web layer → web map → application**

- **Data** are the source geographic and attribute information.
- A **web layer** makes the geographic data available through ArcGIS Online and can be reused in multiple maps and applications.
- A **web map** combines one or more web layers with their symbology, pop-ups, filters and other map settings.
- A **web application** uses a web map or web layers and adds a user interface and tools designed for a particular purpose.

![](../assets/cviceni1/AGOL_workflow.svg){ .no-filter width=800px}
{align=center}

???+ note-fg-color "Why separate data, maps and applications?"
    One dataset can be reused in several web maps, and one web map can be used in several applications. Changes to a shared data source can therefore propagate to multiple outputs without creating unnecessary copies of the data.

## ArcGIS Online content

Items stored in ArcGIS Online can represent different parts of a web GIS project. During this practical, we will mainly work with:

- **Hosted Feature Layers** – vector data hosted in ArcGIS Online,
- **Hosted Feature Layer Views** – alternative interfaces to an existing Hosted Feature Layer,
- **Web Maps** – map compositions combining layers, symbology and map configuration,
- **Applications** – user-facing interfaces built on top of web maps and web layers.

The aim of this practical is to prepare and publish datasets so that they can be **managed efficiently and reused in subsequent web maps and applications**.

???+ note-fg-color "Browser-based workflow"
    This practical uses a fully browser-based workflow and does not require ArcGIS Pro. ArcGIS Online is, however, a proprietary cloud GIS platform and publishing hosted layers requires an organisational account with appropriate privileges.

## Preparing NOAA event data

We will use three datasets from the [__NOAA Natural Hazards database__](https://www.ngdc.noaa.gov/hazel/view/hazards/){.color_def .underlined_dotted .external_link_icon target="_blank"}:

- **Earthquake Events**
- **Volcano Events**
- **Tsunami Events**

[Earthquake Events :material-earth:](https://www.ngdc.noaa.gov/hazel/view/hazards/earthquake/event-data/){ .md-button .md-button--primary .button_smaller }
[Volcano Events :material-volcano:](https://www.ngdc.noaa.gov/hazel/view/hazards/volcano/event-search/){ .md-button .md-button--primary .button_smaller }
[Tsunami Events :material-waves:](https://www.ngdc.noaa.gov/hazel/view/hazards/tsunami/event-search/){ .md-button .md-button--primary .button_smaller }
{: .button_array style="justify-content:flex-start;"}

Open each search interface, leave the search filters empty, run the search and download the resulting dataset as a tab-separated text file (`.tsv`).

### Import the TSV files into Excel

Do **not** open the downloaded TSV files by double-clicking or drag-and-drop. Instead:

1. Open Excel and select **Data → From Text/CSV**.
2. Select the downloaded `.tsv` file.
3. Check that the delimiter is **Tab** and the encoding is **UTF-8**.
4. Use **Transform Data** and review the detected field types.
5. Remove the first data row containing the export search parameters.
6. Remove the empty `Search Parameters` column.
7. Keep missing values empty – **do not replace them with zeros**.
8. Export the cleaned table as **CSV UTF-8**.

???+ warning "Check automatic data conversion"
    Spreadsheet software may automatically interpret decimal values such as `7.3` as dates. Always import the TSV file using **Data → From Text/CSV** and verify the detected data types before loading the table.

???+ warning "Missing value ≠ zero"
    An empty value means that the information is unknown or unavailable. A value of `0` means that the phenomenon was measured and its value was zero. Replacing missing values with zeros would therefore change the meaning of the data.

Use simple filenames, for example:

```text
Earthquake_Events.csv
Volcano_Events.csv
Tsunami_Events.csv
```

## Publishing data to ArcGIS Online

ArcGIS Online can publish spatial data directly from common file formats without using desktop GIS software. We will publish the three cleaned CSV files as point Hosted Feature Layers using their latitude and longitude attributes.

Sign in to [__ArcGIS Online__](https://www.arcgis.com/){.color_def .underlined_dotted .external_link_icon target="_blank"} using your organisational account.

Create a folder named `Practical_01` in **Content → My content** and publish all three CSV files as separate Hosted Feature Layers.

For each dataset:

1. Click **New item → Your device** and select the corresponding CSV file.
2. Choose **Add file and create a hosted layer or table**.
3. Review the detected fields and their data types.
4. For location information, select **Latitude and longitude**.
5. Check that the appropriate latitude and longitude fields are used.
6. Review numeric fields such as year, magnitude, VEI, casualties and damage.
7. Add an appropriate title and tags.
8. Save the item into the `Practical_01` folder.

Use the following titles:

```text
Earthquake Events
Volcano Events
Tsunami Events
```

???+ note-fg-color "CSV field types"
    CSV files do not store an explicit field schema. ArcGIS Online therefore estimates field types from the data. Always verify the detected types before publishing, especially for sparse numeric attributes containing many empty values.

### What has been created?

After publishing all three datasets, inspect **My content**. For each uploaded CSV, ArcGIS Online creates a source file item and a Hosted Feature Layer.

Open the Hosted Feature Layer item and inspect:

- **Overview** – item description, tags, credits and sharing,
- **Data** – attribute table and fields,
- **Visualization** – default representation,
- **Settings** – editing, export and other layer capabilities.

<hr/>

# ArcGIS Vector Tile Style Editor

A **basemap** provides geographic context for thematic information. In web cartography, the basemap should support the thematic layers rather than compete with them visually.

ArcGIS Vector Tile Style Editor (VTSE) allows you to create a custom style based on an existing vector basemap. The underlying vector tiles remain the same, while colours, labels and other visual properties can be customised.

[Vector Tile Style Editor :material-palette:](https://vtse.arcgis.com/){ .md-button .md-button--primary .button_smaller }
{: .button_array style="justify-content:flex-start;"}

## Create a custom basemap

Create a custom vector basemap suitable for displaying global natural-hazard events.

Your basemap should:

- provide sufficient geographic context at global and regional scales,
- remain visually subordinate to the thematic event layers,
- use restrained colours,
- keep labels readable but unobtrusive,
- avoid unnecessary visual detail,
- maintain sufficient contrast with all three event layers.

Use **Quick Edit** for broad visual changes and the detailed layer editor when individual feature classes or labels need further refinement.

Save the resulting style to your ArcGIS Online content.

???+ question "Cartographic decision"
    Which basemap elements are essential for interpreting the spatial distribution of natural hazards, and which can be visually suppressed or removed?

<hr/>

# Web Map

## Create a Web Map

Open **Map Viewer** and create a new map containing:

- your custom VTSE basemap,
- `Earthquake Events – App`,
- `Volcano Events – App`,
- `Tsunami Events – App`.

### Configure the thematic layers

Design the three event layers so that they are clearly distinguishable but visually coherent.

Consider using quantitative attributes where appropriate, for example:

- earthquake magnitude,
- volcanic explosivity index (`VEI`),
- a quantitative tsunami attribute such as intensity or maximum run-up.

Configure meaningful **pop-ups** for all three layers. Show only useful attributes and use understandable aliases and number formatting.

???+ note-fg-color "Map before app"
    Configure symbology, pop-ups and the initial map extent in the **Web Map** rather than treating the application builder as the primary place for cartographic design. The Web Map will be reused by multiple applications.

Save the map as:

```text
NOAA Natural Hazard Events
```
<hr/>

# ArcGIS Instant App

We will use an **ArcGIS Instant Apps – Slider** application to explore how the three types of events are distributed through time.

[ArcGIS Instant Apps :material-application:](https://www.arcgis.com/apps/instantgallery/index.html){ .md-button .md-button--primary .button_smaller }
[Slider documentation :material-tune-variant:](https://doc.arcgis.com/en/instant-apps/latest/create-apps/slider.htm){ .md-button .md-button--primary .button_smaller }
{: .button_array style="justify-content:flex-start;"}

## Configure the Slider app

1. Open the `NOAA Natural Hazard Events` Web Map.
2. Create an application using **Instant Apps**.
3. Select the **Slider** template.
4. Configure a **numeric slider** using the numeric year attribute.
5. Apply the slider to all three event layers.
6. Configure the slider so that users can interactively explore changes in the distribution of events through time.
7. Enable only interface elements that support the purpose of the application, such as the legend, layer list or pop-ups.
8. Review the title, description and sharing settings.
9. Publish the application.

Use a title such as:

```text
Natural Hazard Events Through Time
```

???+ note-fg-color "Numeric slider vs. time slider"
    The Slider template can animate data using a **numeric field in one or more layers**. Using the numeric year attribute avoids the need to construct complete date values for historical records where month or day may be unknown.

<hr/>

# ArcGIS StoryMap

The Instant App provides an **exploratory view** of the full dataset. We will now complement it with a **curated narrative** highlighting selected major events.

[ArcGIS StoryMaps :material-book-open-page-variant:](https://storymaps.arcgis.com/){ .md-button .md-button--primary .button_smaller }
{: .button_array style="justify-content:flex-start;"}

Create a StoryMap that combines a short narrative with selected event locations and the interactive Instant App.

## Map Tours

Prepare a short Map Tour, e.g.:

- **Top 5 Earthquake Events**
- **Top 5 Tsunami Events**
- **Top 5 Volcano Events**

Instructions:

1. Choose a meaningful quantitative criterion for selecting the five events.
2. State the criterion clearly in the StoryMap.
3. For each event, include:
   - event name or location,
   - year,
   - the quantitative value used for ranking,
   - a short explanatory text,
   - an appropriate image where available.

???+ question "What does Top 5 mean?"
    A ranking is meaningful only when the criterion is explicit. The most powerful earthquake, the deadliest earthquake and the most damaging earthquake are not necessarily the same event. Choose a criterion that can be justified from the available attributes.

## Embed the Instant App

Below the curated Map Tours, add a short transition explaining that the selected events represent only a small part of the complete dataset.

Embed the published **Natural Hazard Events Through Time** Instant App so that readers can explore the full data interactively.

???+ note-fg-color "Narrative + exploration"
    The StoryMap and Instant App serve different purposes. The Map Tours provide a **curated narrative**, while the embedded Instant App provides an **exploratory interface** to the complete dataset.

## Output

At the end of the practical, you should have the following ArcGIS Online items:

1. a custom **vector basemap style** created in VTSE,
2. a **Web Map** containing the three NOAA event layers,
3. a **Slider Instant App** filtering the three event layers by year,
4. a **StoryMap** containing *Top 5* Map Tour and the embedded Instant App.

!!! abstract "Final workflow"
    **NOAA application Views → custom VTSE basemap → Web Map → Slider Instant App → StoryMap**

    The same Web Map and data will be reused in the next practical when creating an **Experience Builder application** and an **ArcGIS Dashboard**.
