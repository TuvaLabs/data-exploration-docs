---
sidebar_position: 2 # Position second within utils
title: axisUtil
---

# axisUtil

(*Path likely `src/lib/dynplot/axisUtil.js` or similar*)

This module likely contains utility functions specifically focused on calculations and logic related to plot axes, used primarily by [`AxisView`](../AxisView.md) and [`PlotElement`](../plotElement/PlotElement.md) subclasses.

## Overview

`axisUtil` centralizes reusable logic for tasks like determining tick values, formatting labels, and handling different axis types (numeric, categorical, date, etc.).

-   **Functionality:** Provides helper functions for:
    -   **Tick Generation:** Calculating "nice" tick values and positions based on a data domain and scale type (e.g., linear, log). Might leverage libraries like d3-scale or implement custom logic.
    -   **Label Formatting:** Formatting numerical, date, or categorical values into human-readable strings suitable for axis labels, potentially considering [`Attribute`](../../dynDataset/Attribute.md) formatting settings.
    -   **Scale Domain Calculation:** Helpers for determining appropriate axis domains (min/max) based on data ranges and desired padding.
    -   **Categorical Axis Logic:** Helpers for managing discrete category positions and labels.

## Key Functions (Conceptual Examples)

-   `generateTicks(domain, scaleType, desiredTickCount)`: Returns an array of tick values.
-   `formatTickValue(value, attributeFormat, scaleType)`: Formats a tick value into a string.
-   `calculateNiceDomain(dataMin, dataMax, scaleType)`: Calculates a padded domain suitable for axis display.
-   `getCategoryPositions(categories, range)`: Determines screen positions for categorical labels.

## Usage

-   Functions are imported and used heavily by:
    -   [`AxisView`](../AxisView.md): For calculating tick positions and formatting labels.
    -   [`PlotElement`](../plotElement/PlotElement.md) subclasses: For calculating axis domains (`calcAxis`, `calcPlotSpecificRange`) and potentially formatting values used in calculations.

## Dependencies

-   May depend on **[`Attribute`](../../dynDataset/Attribute.md)** formatting properties.
-   May utilize external libraries like **d3-scale**, **d3-format**, **d3-time-format** for complex scaling, formatting, and tick generation. 