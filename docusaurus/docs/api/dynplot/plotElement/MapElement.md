---
sidebar_position: 14 # Adjust position relative to other PlotElement types
title: MapElement
---

# `MapElement` Class

(`src/lib/dynplot/plotElement/mapElement.js` - *Note: Actual file path might differ*)

This class implements a **Map** view for displaying geographically referenced data.

## Overview

`MapElement` likely extends the base [`PlotElement`](./PlotElement.md) but has fundamentally different requirements than standard Cartesian plots.

-   **Functionality:** Visualizes data points or aggregated data overlaid on a geographical map (e.g., world map, country map, state map).
-   **Data Representation:** Can represent data in various ways:
    -   **Points/Markers:** Showing individual case locations based on latitude/longitude [`Attributes`](../../dynDataset/Attribute.md).
    -   **Chloropleth:** Shading geographical regions (countries, states, counties) based on an aggregated value (e.g., count, sum, mean) for cases within that region. Requires attributes linking cases to regions.
    -   **Heatmap:** Showing density of points.
-   **Configuration:** Requires specific configuration for:
    -   **Map Layers/Tiles:** Base map imagery (e.g., OpenStreetMap, Mapbox).
    -   **Projection:** How the 3D globe is represented in 2D.
    -   **Attribute Mapping:** Defining which attributes provide location data (lat/lon, region name) and which control visual properties like color or size.
    -   **Region Boundaries:** May need access to GeoJSON or similar boundary data for chloropleth maps.
-   **Axes:** Does not use standard X/Y axes. Relies on geographic coordinate systems.

## Key Properties & Methods

-   Inherits core properties and methods from [`PlotElement`](./PlotElement.md) where applicable.
-   `constructor()`: Sets flags specific to map views.
-   Methods for loading map tiles and boundary data.
-   `calcPosition()` / `updateMapView()`: Calculates positions of markers or determines region shading based on data and attribute mappings. This involves converting geographic coordinates to screen coordinates based on the current map view (zoom, center).
-   Methods for handling map interactions like zooming, panning, and potentially clicking/hovering on map features to show details (linking to [`<CaseCardComponent />`](../../components/CaseCardComponent.md)?).
-   Defines its own `kDefaultTitle` (e.g., "Map") and `kUndoAction`.

## Usage

-   Created by `PlotShaper` when the user selects "Map" from the [`<ToolbarComponent />`](../../components/ToolbarComponent.md) and assigns appropriate geographic and potentially numeric/categorical attributes.
-   Used to explore spatial patterns and relationships in the data.

## Dependencies

-   Extends **[`PlotElement`](./PlotElement.md)**.
-   Requires specific **[`Attribute`](../../dynDataset/Attribute.md)** types for geographic data (latitude, longitude, region identifiers).
-   May depend heavily on an **external mapping library** (e.g., Leaflet, Mapbox GL JS, OpenLayers) integrated within the component.
-   Interaction with `PlotShaper` and [`<ToolbarComponent />`](../../components/ToolbarComponent.md) for creation.
-   May require access to **GeoJSON** or other boundary files. 