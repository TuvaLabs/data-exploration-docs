---
sidebar_position: 6 # Position after PlotShaper
title: iconStyler
---

# iconStyler Utility/Class

(*Path likely `src/lib/dynplot/iconStyler.js` or similar*)

This utility or class is responsible for determining the visual style (color, shape, size) of individual icons or markers used in plots, particularly dot plots ([`DotPlotElement`](./plotElement/DotPlotElement.md)) and scatter plots ([`ScatterPlotElement`](./plotElement/ScatterPlotElement.md)).

## Overview

When rendering plots with individual points, the style of each point often encodes information from the data (e.g., color based on a legend attribute). `iconStyler` likely encapsulates the logic for applying these styling rules.

-   **Functionality:** Takes information about a specific data case and the current plot configuration (assigned attributes, color maps) and returns the appropriate style properties for that case's icon/marker.
-   **Styling Properties Determined:**
    -   `fill`: Fill color (often determined by the legend [`Attribute`](../dynDataset/Attribute.md) and its `colorMap`).
    -   `stroke`: Outline color.
    -   `size`: Size of the icon (could be fixed or mapped to another attribute).
    -   `shape`: Shape of the icon (e.g., circle, square, triangle - potentially mapped to an attribute).
    -   `opacity`: Transparency.
-   **Context Awareness:** Needs access to the current legend attribute, its color map, potentially attributes assigned to size or shape roles, and the specific data values for the case being styled.

## Key Methods (Conceptual)

-   `getStyle(caseData, plotConfig)`: The main method that takes case data and plot configuration details (legend attribute, color map, size attribute, etc.) and returns an object with style properties (fill, stroke, size, shape).
-   `getColor(value, colorMap)`: Helper to determine fill color based on a value and color map.
-   `getSize(value, sizeScale)`: Helper to determine size.
-   `getShape(value, shapeMap)`: Helper to determine shape.

## Usage

-   Used internally by **[`PlotElement`](./plotElement/PlotElement.md)** subclasses that render individual points (e.g., `DotPlotElement`, `ScatterPlotElement`, `DotPlotBase`).
-   Called within the rendering loop for each data point to determine how it should look.

## Dependencies

-   Relies on **[`Attribute`](../dynDataset/Attribute.md)** metadata and `colorMap`.
-   Uses data values from individual cases.
-   May interact with color utility functions (`Dyn.colorUtil`) or scaling libraries (like d3-scale).
-   Provides styling information used by the rendering logic within **[`PlotElement`](./plotElement/PlotElement.md)** subclasses. 