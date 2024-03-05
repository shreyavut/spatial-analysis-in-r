# Spatial Analysis in R - NICAR 2024 🗺️

Shreya Vuttaluru, Tampa Bay Times  
Ryan Little, The Baltimore Banner

This GitHub repository accompanies a class on spatial analysis in R. We'll cover basic spatial functions for transforming data and explore tools for exploratory mapping, spatial joins, buffering, calculating spatial distances between points and spatial indexing.

We'll be using the `sf` package for geospatial functions. This package has many of the same functions available in geospatial software like ArcGIS, QGIS and PostGIS.

Some advantages of using `sf` for spatial analysis:

- Easy to integrate with other data analysis and cleaning steps
- Reproduce your scripts
- Fairly easy visualization
- Faster processing time for large datasets
- Free! 💰

Clone this repository locally to start!

## Packages for Spatial Work in R:
- **[sf](https://r-spatial.github.io/sf/)** is a relatively intuitive R package with functions for spatial analysis that integrates well with other data analysis and cleaning steps.
- **[raster](https://rspatial.org/raster/pkg/1-introduction.html)** provides functions for reading, writing, processing, and analyzing gridded spatial data, such as satellite imagery, digital elevation models (DEMs), and climate data.
- **[mapview](https://r-spatial.github.io/mapview/)** is a library built off of the leaflet API for creating interactive web maps. Consider using **[leaflet](https://learn.r-journalism.com/en/mapping/leaflet_maps/leaflet/)** instead for more customizable maps.
- **[tidycensus](https://walker-data.com/tidycensus/articles/spatial-data.html)** and **[tigris](https://rdrr.io/cran/tigris/man/tracts.html)** provide spatial data for census geographies across the U.S.


## Basic Types of Spatial Data:
- **Vector Data**: 
  - Represents geographic features like points, lines, and polygons.
    - Example: Points representing cities or landmarks, linear features like roads, rivers, or boundaries.
- **Raster Data**:
  - Represents geographic features as a grid of cells or pixels, where each cell has a value representing a specific attribute.
    - Example: Satellite imagery, digital elevation models (DEMs), land cover classifications.

## Common Spatial Filetypes:
- When filing records requests, it might be helpful to include one or more of these filetypes. You can also ask for polygon, multipolygon, or latitude/longitude fields.
- **ESRI Shapefile (.shp)**: 
  - Standard format for geographic data, holding both shape geometry and attribute information.
- **KML (.kml)**: 
  - Google Earth's language for displaying geographic data, featuring points, lines, and polygons.
- **Compressed KML (.kmz)**: 
  - Compact version of KML, convenient for sharing as a single compressed file.
- **ESRI Geodatabase (.gdb)**: 
  - ESRI's comprehensive spatial data management system, storing various data types within a structured folder.
- **R Data Set (.rds)**: 
  - File format in R for storing spatial data objects, facilitating analysis and manipulation within the R environment.
- **GeoJSON (.geojson)**: 
  - Lightweight format for encoding geographic data structures in a human-readable text format, widely used for web mapping and interoperability purposes.

## Types of Spatial Joins:
- Most of these kinds of joins can be passed as an argument in `st_join`.
- **Point-in-Polygon**: 
  - Assigns attributes from polygons to points that fall within them. Implemented with `st_join` using `join = st_within`.
- **Polygon-on-Polygon**:
  - Assigns attributes from one polygon layer to another based on their spatial intersection, or whether one polygon falls inside another. Implemented with `st_join` using `join = st_intersects`.
- **Intersect**:
  - Computes the intersection between geometries, returning shared portions of intersecting geometries as a new `sf` object using `st_intersection`.
- **Union**:
  - Combines geometries from multiple layers into a single `sf` object, preserving all features and their attributes using `st_union`.
- **Difference**:
  - Computes the geometric difference between two `sf` objects and removes overlapping portions based on their intersection with `st_difference`.
- **Buffer**:
  - Creates buffer zones around spatial features by generating new geometries at a specified distance from the original features using `st_buffer`.
- **Nearest Neighbor**:
  - Determines the nearest feature in one layer to each feature in another layer, achieved using spatial indexing and distance calculations, not directly supported by `st_join`.

Check out the documentation for **[st_join](https://r-spatial.github.io/sf/reference/st_join.html)**  for more.

## Coordinate Reference Systems (CRS):
- Choosing the right CRS is important for accurately representing spatial data on maps.
- There are two main types of CRS: geographic and projected.
- **Geographic CRS** (e.g., CRS 4326/WGS84):
  - Uses latitude and longitude coordinates, like a grid laid over a globe.
- **Projected CRS** (e.g., CRS 5070/NAD83/Conus Albers):
  - Flattens the Earth's surface onto a map, helping with calculating in distance, area, and direction. Stick with a projected system if you plan to do any math.
  - When performing joins, ensure your CRS match each other. Pick one and stick with it.
  - Popular CRS include 4326 and 5070 for any US-based spatial analysis you might do, but research the most appropriate system for your region!

**Other Resources for Understanding CRS:**
- [Earthlab introduction (with R code)](https://www.earthdatascience.org/courses/use-data-open-source-python/intro-vector-data-python/spatial-data-vector-shapefiles/)
- [Overview from USCB](https://www.census.gov/programs-surveys/geography/guidance/geo-areas/national-geospatial-data-standards.html)

Here's this documentation in [Google Docs](https://docs.google.com/document/d/1pilPhRDHUpVOgeCBC6X0y8-9vC7yl5SYmuEfEytSYy8/edit?usp=sharing).
