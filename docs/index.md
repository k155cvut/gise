# Course characteristics

The practices in GIS 1 will introduce you to the basics of geographic information systems (GIS).

You will learn:

- **process** and **analyze** spatial (geographic, map) data
- understand the difference between **vector** and **raster** data
- **filter** data using attribute and spatial queries
- apply basic **spatial functions** (geoprocessing tools)
- **create** and **edit** data
- create models for **automated processing** (_ModelBuilder_ tool)
- **share** data via the web (_ArcGIS Online_, web mapping applications)

Esri ArcGIS Pro software will generally be used during the course.

Principles of geographic information systems, time and space in GIS, spatial representation options, spatial analysis, data quality analysis, GIS technical tools.

## Literature

1. Bolstad, P. (2005) GIS Fundamentals: A First Text on Geographic Information Systems. 2nd Edition, Eider Press, White Bear Lake, Minnesota.
2. De Smith, M.J., Goodchild, M.F. and Longley, P.A. (2015) Geospatial Analysis A Comprehensive Guide to Principles, Techniques, and Software Tools.
3. P. A. Burrough, Rachael McDonnell (1998) Principles of Geographical Information Systems. Oxford University Press.

## Lectures

Lecturers: prof. Ing. Jiří Cajthaml, Ph.D. & Ing. Tomáš Janata, Ph.D.

<!-- <div class="container" style="">
  <div class="list_item" style="background-color:inherit;padding:10px;border-radius:10px;border:2px solid #ddd;">
    <div class="date" style="display:inline-block;text-align:center;color:var(--md-primary-fg-color);width:2.5rem;">
      <div class="month" style="font-size:.6rem;line-height:1.3;">leden</div>
      <div class="day" style="font-size:1.5rem;font-weight:bold;line-height:1;">28</div>
    </div>
    <div class="time_place" style="background-color:blue;display:inline-block">
      <div clas="time">10:00 - 12:00</div>
      <div class="place">C-212, FSv ČVUT</div>
    </div>
    <div class="title_teacher" style="background-color:blue;display:inline-block">
      <div class="title">Lecture Title</div>
      <div class="teacher">Lecturer</div>
    </div>
  </div>
</div> -->

## Courses schedule

<style>
  .connected{margin:0 !important;border-top:none !important; border-bottom:none !important;border-radius:0 !important;box-shadow:none !important;}
  .connected.first{border-radius: .1rem .1rem 0 0 !important; border-top:   .05rem solid var(--md-primary-fg-color) !important;}
  .connected.last {border-radius: 0 0 .1rem .1rem !important; border-bottom:.05rem solid var(--md-primary-fg-color) !important;}

  .connected.table.first{border-radius: .5rem .5rem 0 0 !important; border-top:   .05rem solid var(--md-primary-fg-color) !important;}
  .connected.table.last {border-radius: 0 0 .5rem .5rem !important; border-bottom:.05rem solid var(--md-primary-fg-color) !important;}
  details.connected.table summary:first-child::before{content:none !important;}
  details.connected.table summary:first-child::after{top:22.8px;background-color:var(--md-primary-fg-color);} /*verical alignment*/
  details.connected.table summary{padding-left:0;background-color:unset;}
  summary:hover{background-color:#0094851a !important;}
  details[open] summary{background-color:#0094851a !important;}
  details[open]{border-bottom:.05rem solid var(--md-primary-fg-color) !important;}

  div.event_container{border:.05rem solid var(--md-primary-fg-color); border-radius:.5rem;/*background-color:red;*/overflow: hidden;}
  div.event_container details.details_event_item{border:none;}
  div.event_container details.details_event_item summary{padding:10px; white-space:nowrap;}
  div.event_container details.details_event_item summary .date{display:inline-block;vertical-align:middle;text-align:center;border-right:1px solid var(--md-typeset-table-color); padding-right:calc(1.25em + 2px); padding-left:10px;color:var(--md-primary-fg-color); width:80px;}
                                                 summary .date .month{font-size:.6rem;line-height:1.3;}
                                                 summary .date .day  {font-size:1.5rem;font-weight:bold;line-height:1;}
  div.event_container details.details_event_item summary .time_loc{display:inline-block; vertical-align:middle; font-weight:normal; margin: 0px 40px 0px 20px;}
                                                 /* summary .time_loc .time    {white-space:nowrap;} */
                                                 /* summary .time_loc .location{white-space:nowrap;} */
                                                 summary .marker.map_pin   {display:inline-block; height:1em; width:1em; vertical-align: -6%; margin-right:5px; color:#999;}
                                                 summary .marker.clock_time{display:inline-block; height:1em; width:1em; vertical-align:-10%; margin-right:5px; color:#999;}
  div.event_container details.details_event_item summary .title_staff{display:inline-block; vertical-align:middle; font-weight:normal;}
                                                 summary img{width:1em !important; height:1em !important; object-fit:cover; border-radius:50%; vertical-align:-9%; margin-right:5px;}
  /*DESIGN INSPIRATION: https://cdn.dribbble.com/userupload/6968464/file/original-35752bb8755c7231346ed73826e77597.png*/
</style>

<div class="event_container">
  <details class="details_event_item connected table">
    <summary>
      <div class="date">
        <div class="month">October</div>
        <div class="day">5</div>
      </div>
      <div class="time_loc">
        <div class="time">
          <span class="marker map_pin"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>map-marker</title><path d="M12,11.5A2.5,2.5 0 0,1 9.5,9A2.5,2.5 0 0,1 12,6.5A2.5,2.5 0 0,1 14.5,9A2.5,2.5 0 0,1 12,11.5M12,2A7,7 0 0,0 5,9C5,14.25 12,22 12,22C12,22 19,14.25 19,9A7,7 0 0,0 12,2Z" /></svg></span>
          14:00</div>
        <div class="location">
          <span class="marker clock_time"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>clock-time-eight</title><path d="M12 2C6.5 2 2 6.5 2 12C2 17.5 6.5 22 12 22C17.5 22 22 17.5 22 12S17.5 2 12 2M7.7 15.5L7 14.2L11 11.9V7H12.5V12.8L7.7 15.5Z" /></svg></span>
          B973</div>
      </div>
      <div class="title_staff">
        <div class="title">Practice 1</div>
        <div class="staff">Marek Hoffmann, Jozef Münzberger, Vojtěch Cehák</div>
      </div>
    </summary>
    <p>Course introduction, ArcGIS Pro basics </p>
  </details>

  <details class="details_event_item connected table">
    <summary>
      <div class="date">
        <div class="month">October</div>
        <div class="day">12</div>
      </div>
      <div class="time_loc">
        <div class="time">
          <span class="marker map_pin"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>map-marker</title><path d="M12,11.5A2.5,2.5 0 0,1 9.5,9A2.5,2.5 0 0,1 12,6.5A2.5,2.5 0 0,1 14.5,9A2.5,2.5 0 0,1 12,11.5M12,2A7,7 0 0,0 5,9C5,14.25 12,22 12,22C12,22 19,14.25 19,9A7,7 0 0,0 12,2Z" /></svg></span>
          14:00</div>
        <div class="location">
          <span class="marker clock_time"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>clock-time-eight</title><path d="M12 2C6.5 2 2 6.5 2 12C2 17.5 6.5 22 12 22C17.5 22 22 17.5 22 12S17.5 2 12 2M7.7 15.5L7 14.2L11 11.9V7H12.5V12.8L7.7 15.5Z" /></svg></span>
          B973</div>
      </div>
      <div class="title_staff">
        <div class="title">Practice 2</div>
        <div class="staff">Marek Hoffmann, Jozef Münzberger, Vojtěch Cehák</div>
      </div>
    </summary>
    <p>Coordinate systems, geodatabase, shapefile, reference scale </p>
  </details>

  <details class="details_event_item connected table">
    <summary>
      <div class="date">
        <div class="month">October</div>
        <div class="day">19</div>
      </div>
      <div class="time_loc">
        <div class="time">
          <span class="marker map_pin"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>map-marker</title><path d="M12,11.5A2.5,2.5 0 0,1 9.5,9A2.5,2.5 0 0,1 12,6.5A2.5,2.5 0 0,1 14.5,9A2.5,2.5 0 0,1 12,11.5M12,2A7,7 0 0,0 5,9C5,14.25 12,22 12,22C12,22 19,14.25 19,9A7,7 0 0,0 12,2Z" /></svg></span>
          14:00</div>
        <div class="location">
          <span class="marker clock_time"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>clock-time-eight</title><path d="M12 2C6.5 2 2 6.5 2 12C2 17.5 6.5 22 12 22C17.5 22 22 17.5 22 12S17.5 2 12 2M7.7 15.5L7 14.2L11 11.9V7H12.5V12.8L7.7 15.5Z" /></svg></span>
          B973</div>
      </div>
      <div class="title_staff">
        <div class="title">Practice 3</div>
        <div class="staff">Marek Hoffmann, Jozef Münzberger, Vojtěch Cehák</div>
      </div>
    </summary>
    <p>Vector data (Feature Classes), selections, attribute query, location query	</p>
  </details>

  <details class="details_event_item connected table">
    <summary>
      <div class="date">
        <div class="month">October</div>
        <div class="day">26</div>
      </div>
      <div class="time_loc">
        <div class="time">
          <span class="marker map_pin"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>map-marker</title><path d="M12,11.5A2.5,2.5 0 0,1 9.5,9A2.5,2.5 0 0,1 12,6.5A2.5,2.5 0 0,1 14.5,9A2.5,2.5 0 0,1 12,11.5M12,2A7,7 0 0,0 5,9C5,14.25 12,22 12,22C12,22 19,14.25 19,9A7,7 0 0,0 12,2Z" /></svg></span>
          14:00</div>
        <div class="location">
          <span class="marker clock_time"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>clock-time-eight</title><path d="M12 2C6.5 2 2 6.5 2 12C2 17.5 6.5 22 12 22C17.5 22 22 17.5 22 12S17.5 2 12 2M7.7 15.5L7 14.2L11 11.9V7H12.5V12.8L7.7 15.5Z" /></svg></span>
          B973</div>
      </div>
      <div class="title_staff">
        <div class="title">Practice 4</div>
        <div class="staff">Marek Hoffmann, Jozef Münzberger, Vojtěch Cehák</div>
      </div>
    </summary>
    <p>Attribute table, join, spatial join, calculate field, calculate geometry</p>
  </details>

  <details class="details_event_item connected table">
    <summary>
      <div class="date">
        <div class="month">November</div>
        <div class="day">2</div>
      </div>
      <div class="time_loc">
        <div class="time">
          <span class="marker map_pin"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>map-marker</title><path d="M12,11.5A2.5,2.5 0 0,1 9.5,9A2.5,2.5 0 0,1 12,6.5A2.5,2.5 0 0,1 14.5,9A2.5,2.5 0 0,1 12,11.5M12,2A7,7 0 0,0 5,9C5,14.25 12,22 12,22C12,22 19,14.25 19,9A7,7 0 0,0 12,2Z" /></svg></span>
          14:00</div>
        <div class="location">
          <span class="marker clock_time"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>clock-time-eight</title><path d="M12 2C6.5 2 2 6.5 2 12C2 17.5 6.5 22 12 22C17.5 22 22 17.5 22 12S17.5 2 12 2M7.7 15.5L7 14.2L11 11.9V7H12.5V12.8L7.7 15.5Z" /></svg></span>
          B973</div>
      </div>
      <div class="title_staff">
        <div class="title">Practice 5</div>
        <div class="staff">Marek Hoffmann, Jozef Münzberger, Vojtěch Cehák</div>
      </div>
    </summary>
    <p>Creating vector data, editing tools (constraints, snapping, absolute location,
fixed angle/distance, move, rotate, scale, split, merge, copy geometry between layers) </p>
  </details>

  <details class="details_event_item connected table">
    <summary>
      <div class="date">
        <div class="month">November</div>
        <div class="day">9</div>
      </div>
      <div class="time_loc">
        <div class="time">
          <span class="marker map_pin"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>map-marker</title><path d="M12,11.5A2.5,2.5 0 0,1 9.5,9A2.5,2.5 0 0,1 12,6.5A2.5,2.5 0 0,1 14.5,9A2.5,2.5 0 0,1 12,11.5M12,2A7,7 0 0,0 5,9C5,14.25 12,22 12,22C12,22 19,14.25 19,9A7,7 0 0,0 12,2Z" /></svg></span>
          14:00</div>
        <div class="location">
          <span class="marker clock_time"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>clock-time-eight</title><path d="M12 2C6.5 2 2 6.5 2 12C2 17.5 6.5 22 12 22C17.5 22 22 17.5 22 12S17.5 2 12 2M7.7 15.5L7 14.2L11 11.9V7H12.5V12.8L7.7 15.5Z" /></svg></span>
          B973</div>
      </div>
      <div class="title_staff">
        <div class="title">Practice 6</div>
        <div class="staff">Marek Hoffmann, Jozef Münzberger, Vojtěch Cehák</div>
      </div>
    </summary>
    <p>Geoprocessing tools (Buffer, Clip, Union, Intersect, Project),
specific use case (finding the best location for a new city bus stop)</p>
  </details>

  <details class="details_event_item connected table">
    <summary>
      <div class="date">
        <div class="month">November</div>
        <div class="day">16</div>
      </div>
      <div class="time_loc">
        <div class="time">
          <span class="marker map_pin"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>map-marker</title><path d="M12,11.5A2.5,2.5 0 0,1 9.5,9A2.5,2.5 0 0,1 12,6.5A2.5,2.5 0 0,1 14.5,9A2.5,2.5 0 0,1 12,11.5M12,2A7,7 0 0,0 5,9C5,14.25 12,22 12,22C12,22 19,14.25 19,9A7,7 0 0,0 12,2Z" /></svg></span>
          14:00</div>
        <div class="location">
          <span class="marker clock_time"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>clock-time-eight</title><path d="M12 2C6.5 2 2 6.5 2 12C2 17.5 6.5 22 12 22C17.5 22 22 17.5 22 12S17.5 2 12 2M7.7 15.5L7 14.2L11 11.9V7H12.5V12.8L7.7 15.5Z" /></svg></span>
          B973</div>
      </div>
      <div class="title_staff">
        <div class="title">Practice 7</div>
        <div class="staff">Marek Hoffmann, Jozef Münzberger, Vojtěch Cehák</div>
      </div>
    </summary>
    <p>Data resource overview, web data services, geoportals</p>
  </details>

  <details class="details_event_item connected table">
    <summary>
      <div class="date">
        <div class="month">November</div>
        <div class="day">23</div>
      </div>
      <div class="time_loc">
        <div class="time">
          <span class="marker map_pin"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>map-marker</title><path d="M12,11.5A2.5,2.5 0 0,1 9.5,9A2.5,2.5 0 0,1 12,6.5A2.5,2.5 0 0,1 14.5,9A2.5,2.5 0 0,1 12,11.5M12,2A7,7 0 0,0 5,9C5,14.25 12,22 12,22C12,22 19,14.25 19,9A7,7 0 0,0 12,2Z" /></svg></span>
          14:00</div>
        <div class="location">
          <span class="marker clock_time"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>clock-time-eight</title><path d="M12 2C6.5 2 2 6.5 2 12C2 17.5 6.5 22 12 22C17.5 22 22 17.5 22 12S17.5 2 12 2M7.7 15.5L7 14.2L11 11.9V7H12.5V12.8L7.7 15.5Z" /></svg></span>
          B973</div>
      </div>
      <div class="title_staff">
        <div class="title">Practice 8</div>
        <div class="staff">Marek Hoffmann, Jozef Münzberger, Vojtěch Cehák</div>
      </div>
    </summary>
    <p>Raster data, raster parameters (extent, px size, px depth, bands, pyramids, spatial reference),
basic symbology, terrain representation in GIS</p>
  </details>

  <details class="details_event_item connected table">
    <summary>
      <div class="date">
        <div class="month">November</div>
        <div class="day">30</div>
      </div>
      <div class="time_loc">
        <div class="time">
          <span class="marker map_pin"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>map-marker</title><path d="M12,11.5A2.5,2.5 0 0,1 9.5,9A2.5,2.5 0 0,1 12,6.5A2.5,2.5 0 0,1 14.5,9A2.5,2.5 0 0,1 12,11.5M12,2A7,7 0 0,0 5,9C5,14.25 12,22 12,22C12,22 19,14.25 19,9A7,7 0 0,0 12,2Z" /></svg></span>
          14:00</div>
        <div class="location">
          <span class="marker clock_time"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>clock-time-eight</title><path d="M12 2C6.5 2 2 6.5 2 12C2 17.5 6.5 22 12 22C17.5 22 22 17.5 22 12S17.5 2 12 2M7.7 15.5L7 14.2L11 11.9V7H12.5V12.8L7.7 15.5Z" /></svg></span>
          B973</div>
      </div>
      <div class="title_staff">
        <div class="title">Practice 9</div>
        <div class="staff">Marek Hoffmann, Jozef Münzberger, Vojtěch Cehák</div>
      </div>
    </summary>
    <p>Geoprocessing tools for raster data (Slope, Aspect, Reclassify, Raster Calculator)	</p>
  </details>

  <details class="details_event_item connected table">
    <summary>
      <div class="date">
        <div class="month">December</div>
        <div class="day">7</div>
      </div>
      <div class="time_loc">
        <div class="time">
          <span class="marker map_pin"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>map-marker</title><path d="M12,11.5A2.5,2.5 0 0,1 9.5,9A2.5,2.5 0 0,1 12,6.5A2.5,2.5 0 0,1 14.5,9A2.5,2.5 0 0,1 12,11.5M12,2A7,7 0 0,0 5,9C5,14.25 12,22 12,22C12,22 19,14.25 19,9A7,7 0 0,0 12,2Z" /></svg></span>
          14:00</div>
        <div class="location">
          <span class="marker clock_time"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>clock-time-eight</title><path d="M12 2C6.5 2 2 6.5 2 12C2 17.5 6.5 22 12 22C17.5 22 22 17.5 22 12S17.5 2 12 2M7.7 15.5L7 14.2L11 11.9V7H12.5V12.8L7.7 15.5Z" /></svg></span>
          B973</div>
      </div>
      <div class="title_staff">
        <div class="title">Practice 10</div>
        <div class="staff">Marek Hoffmann, Jozef Münzberger, Vojtěch Cehák</div>
      </div>
    </summary>
    <p>Raster/vector conversion, subsequent conversion GP tools</p>
  </details>

  <details class="details_event_item connected table">
    <summary>
      <div class="date">
        <div class="month">December</div>
        <div class="day">14</div>
      </div>
      <div class="time_loc">
        <div class="time">
          <span class="marker map_pin"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>map-marker</title><path d="M12,11.5A2.5,2.5 0 0,1 9.5,9A2.5,2.5 0 0,1 12,6.5A2.5,2.5 0 0,1 14.5,9A2.5,2.5 0 0,1 12,11.5M12,2A7,7 0 0,0 5,9C5,14.25 12,22 12,22C12,22 19,14.25 19,9A7,7 0 0,0 12,2Z" /></svg></span>
          14:00</div>
        <div class="location">
          <span class="marker clock_time"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>clock-time-eight</title><path d="M12 2C6.5 2 2 6.5 2 12C2 17.5 6.5 22 12 22C17.5 22 22 17.5 22 12S17.5 2 12 2M7.7 15.5L7 14.2L11 11.9V7H12.5V12.8L7.7 15.5Z" /></svg></span>
          B973</div>
      </div>
      <div class="title_staff">
        <div class="title">Practice 11</div>
        <div class="staff">Marek Hoffmann, Jozef Münzberger, Vojtěch Cehák</div>
      </div>
    </summary>
    <p>ArcGIS Online, sharing data from ArcGIS Pro</p>
  </details>

  <details class="details_event_item connected table">
    <summary>
      <div class="date">
        <div class="month">December</div>
        <div class="day">21</div>
      </div>
      <div class="time_loc">
        <div class="time">
          <span class="marker map_pin"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>map-marker</title><path d="M12,11.5A2.5,2.5 0 0,1 9.5,9A2.5,2.5 0 0,1 12,6.5A2.5,2.5 0 0,1 14.5,9A2.5,2.5 0 0,1 12,11.5M12,2A7,7 0 0,0 5,9C5,14.25 12,22 12,22C12,22 19,14.25 19,9A7,7 0 0,0 12,2Z" /></svg></span>
          14:00</div>
        <div class="location">
          <span class="marker clock_time"><svg fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>clock-time-eight</title><path d="M12 2C6.5 2 2 6.5 2 12C2 17.5 6.5 22 12 22C17.5 22 22 17.5 22 12S17.5 2 12 2M7.7 15.5L7 14.2L11 11.9V7H12.5V12.8L7.7 15.5Z" /></svg></span>
          B973</div>
      </div>
      <div class="title_staff">
        <div class="title">Practice 12</div>
        <div class="staff">Marek Hoffmann, Jozef Münzberger, Vojtěch Cehák</div>
      </div>
    </summary>
    <p>Assessment Project Presentation	</p>
  </details>
</div>

<div style="margin:6cm">&nbsp;</div>
