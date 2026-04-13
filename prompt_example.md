## Prompt Example


You are a Frontend Developer specializing in Geospatial Web Apps.
Create HTML code using the [Map Library: e.g., OpenLayers 9] library to display a vector tile map.
STEP 1: INFRASTRUCTURE & SOURCE

Map Library: OpenLayers v9.2.4 (via CDN).

Base Tile Path: ${window.location.origin}/datasets/${dataset}/mvt/{z}/{x}/{y}.mvt

Use OSM as base map. Make sure the base map is seamless integrated in the visualization: const base = new ol.layer.Tile({
  source: new ol.source.OSM()
});

Default Dataset: TIGER2018_COUNTY

Target Container ID: map

Initial Viewport: Center: [-98.5, 39.5] | Zoom: 3.

STEP 2: DATA SCHEMA (MVT METADATA)

Source Layer Name: (Generic/Not specified in code, but uses standard MVT format).

Fields/Attributes: * geometry: The shapes (Polygons/Points) included in the MVT tiles.
 STATEFP
(string)
 COUNTYFP
(string)
 COUNTYNS
(string)
 GEOID
(string)
 NAME
(string)
 NAMELSAD
(string)
 LSAD
(string)
 CLASSFP
(string)
 MTFCC
(string)
 CSAFP
(string)
 CBSAFP
(string)
 METDIVFP
(string)
 FUNCSTAT
(string)
 ALAND
(integer)
 AWATER
(integer)
 INTPTLAT
(string)
 INTPTLON
(Note: No specific property filtering is used, just global styling for all features.)

STEP 3: VISUALIZATION & UI GOALS (Natural Language)

UI Layout: Create a fullscreen map. In the top-left, place a floating white info panel (rgba(255,255,255,0.96)) with rounded corners and a shadow.

Display Info: The panel must show a title ("Starlet map example"), the active dataset name, the full calculated Tile URL in a <code> block, and a status message.

Styling Logic: * Polygons: Dark blue stroke (rgba(8, 48, 107, 0.95), width 1.2) and a color fills at random for different regions

Points: Orange circles (rgba(217, 95, 14, 0.9)) with a white 1px border.

Dynamics: Use URLSearchParams to grab a dataset key from the URL. If missing, use the default.

STEP 4: SYSTEM INSTRUCTIONS

Include the OpenLayers CSS in the <head> and JS at the end of the <body>.

Implement event listeners on the vector source:

On tileloadstart: Update status to "Loading vector tiles…".

On tileloadend: Update status to "Vector tiles loaded.".

On tileloaderror: Display an error message mentioning the Flask console.

Ensure the code uses ol.proj.fromLonLat for the initial view center.   
