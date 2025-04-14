---
sidebar_position: 2 # Position after PlotView
title: AxisView
---

# `AxisView` Class/Component

(*Path might be `src/lib/dynplot/axisView.js` or similar*)

This component is responsible for rendering a single axis (horizontal or vertical) within a plot area, including its line, tick marks, labels, and title.

## Overview

`AxisView` works in conjunction with [`PlotView`](./PlotView.md) and the active [`PlotElement`](./plotElement/PlotElement.md) to display axes correctly configured for the current plot type and assigned attributes.

-   **Functionality:** Renders the visual representation of a data axis based on calculated scale, range, and attribute type.
-   **Types Handled:** Needs to support different types of axes:
    -   **Numeric:** Linear scales, potentially logarithmic scales.
    -   **Categorical:** Discrete labels for distinct categories.
    -   **Frequency/Percentage/Proportion:** Numeric scales representing counts or relative values (often for Histogram or Bar Chart y-axes).
    -   **Time/Date:** Scales appropriate for date/time data.
-   **Configuration:** Receives its configuration (data range, scale type, tick format, axis label/title, orientation - horizontal/vertical) primarily from the [`PlotElement`](./plotElement/PlotElement.md) which calculates these based on the assigned [`Attribute`](../dynDataset/Attribute.md) and plot type.

## Key Responsibilities & Methods

-   **Scale Calculation:** While the core range might be set by `PlotElement`, `AxisView` might use a scaling library (like d3-scale) to map data values to pixel positions.
-   **Tick Generation:** Calculates the positions and values for tick marks along the axis based on the scale.
-   **Label Formatting:** Formats the tick labels appropriately (e.g., number formatting, date formatting, category names).
-   **Rendering:** Draws the axis line, tick marks, and labels (using SVG, Canvas, or HTML elements).
-   **Title Display:** Renders the axis title, usually derived from the [`Attribute`](../dynDataset/Attribute.md) name or explicitly set.
-   **Updating:** Must efficiently update its rendering when the data, plot type, or axis configuration changes (e.g., zooming, panning, attribute change).

## Usage

-   Instances of `AxisView` (typically one for X and one for Y) are likely created and managed by [`PlotView`](./PlotView.md).
-   [`PlotElement`](./plotElement/PlotElement.md) subclasses call methods on `AxisView` instances (or provide configuration) during their `calcAxis` or similar phases to set up the scale, range, and labels.

## Dependencies

-   Works closely with **[`PlotView`](./PlotView.md)** (its container).
-   Receives configuration from **[`PlotElement`](./plotElement/PlotElement.md)** subclasses.
-   Displays information derived from **[`Attribute`](../dynDataset/Attribute.md)** metadata (name, type, categories).
-   May utilize a scaling library (e.g., **d3-scale**).
-   Interacts with the rendering system (SVG/Canvas/HTML). 