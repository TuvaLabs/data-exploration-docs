---
sidebar_position: 1 # Position first within utils
title: plotUtil
---

# plotUtil

(*Path likely `src/lib/dynplot/plotUtil.js` or similar*)

This module likely contains various utility functions shared across different plotting components and classes within the `dynplot` system, particularly those related to general plot layout, coordinate calculations, or common rendering tasks.

## Overview

`plotUtil` serves as a collection of reusable helper functions to avoid code duplication and centralize common plotting logic that doesn't belong to a specific class like `PlotView` or `PlotElement`.

-   **Functionality:** Provides helper functions for tasks such as:
    -   Calculating plot dimensions based on container size and margins.
    -   Mapping data coordinates to screen (pixel) coordinates (potentially simple linear mapping helpers).
    -   Geometric calculations (e.g., distance between points, checking if a point is within a rectangle).
    -   Common SVG or Canvas drawing helpers (e.g., creating path strings).
    -   Debouncing or throttling functions for handling frequent events like resizing.

## Key Functions (Conceptual Examples)

-   `calculatePlotArea(containerWidth, containerHeight, margins)`: Returns dimensions for the main plot region.
-   `mapDataToScreen(value, dataDomain, screenRange)`: Basic linear scaling.
-   `isPointInRect(point, rect)`: Collision detection.
-   `debounce(func, delay)`: Event handling utility.

## Usage

-   Functions from `plotUtil` are imported and used by various classes like:
    -   [`PlotView`](../PlotView.md): For layout calculations.
    -   [`PlotElement`](../plotElement/PlotElement.md) subclasses: For position calculations or rendering helpers.
    -   [`AxisView`](../AxisView.md): Potentially for coordinate mapping.

## Dependencies

-   Generally contains standalone functions.
-   May rely on basic geometry or math concepts. 