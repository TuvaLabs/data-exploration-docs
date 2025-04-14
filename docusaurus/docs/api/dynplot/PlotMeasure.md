---
sidebar_position: 7 # Position after iconStyler
title: PlotMeasure
---

# PlotMeasure Class/Concept

(*Path likely `src/lib/dynplot/plotMeasure.js` or related to plot overlays/annotations*)

This class or concept likely relates to the functionality for displaying **statistical measures or annotations directly on the plot area**.

## Overview

Often, users want to see calculated statistics overlaid on the visualization (e.g., a line showing the mean, shaded areas for standard deviation, counts displayed on bars). `PlotMeasure` might be the component or system responsible for managing and rendering these statistical overlays.

-   **Functionality:**
    -   Provides options for users to toggle the display of various statistical measures (Mean, Median, Standard Deviation, Box Plot elements, Counts, Percentages, etc.) on the current plot.
    -   Calculates the necessary statistics (likely using [`AttributeStats`](../dynDataset/AttributeStats.md) from the relevant [`Attribute`](../dynDataset/Attribute.md)).
    -   Determines the correct position and visual representation for the measure on the plot (e.g., coordinates for a mean line, position for a count label).
    -   Renders the visual representation of the measure onto the plot area managed by [`PlotView`](./PlotView.md).
-   **User Interface:** Controls for toggling these measures might appear in the [`ToolbarComponent`](../components/ToolbarComponent.md) or a dedicated plot settings panel ([`PlotSettingComponent`](../components/PlotSettingComponent.md)).
-   **Context Dependent:** The available measures and how they are calculated/displayed depend heavily on the current plot type ([`PlotElement`](./plotElement/PlotElement.md)) and the attributes assigned.

## Key Methods/Responsibilities (Conceptual)

-   `showMeasure(measureType, attributeId)`: Enables the display of a specific measure.
-   `hideMeasure(measureType)`: Disables the display of a measure.
-   `calculatePosition(measureType, stats, scale)`: Determines where on the plot the measure should be drawn.
-   `render(measureType, position)`: Draws the visual element for the measure (e.g., line, text, shaded area).
-   `update()`: Recalculates and redraws measures when data or plot configuration changes.

## Usage

-   Allows users to add quantitative summaries directly onto the visual representation of the data.
-   Enhances plot interpretation by highlighting key statistical features.
-   Likely works as an overlay system managed by or interacting closely with **[`PlotView`](./PlotView.md)** and the active **[`PlotElement`](./plotElement/PlotElement.md)**.

## Dependencies

-   Interacts with **[`PlotView`](./PlotView.md)** for rendering space and coordinate systems.
-   Relies on statistics calculated by **[`AttributeStats`](../dynDataset/AttributeStats.md)** for the relevant **[`Attribute`](../dynDataset/Attribute.md)(s)**.
-   Configuration might be controlled via **[`ToolbarComponent`](../components/ToolbarComponent.md)** or **[`PlotSettingComponent`](../components/PlotSettingComponent.md)**.
-   Specific calculations depend on the active **[`PlotElement`](./plotElement/PlotElement.md)**. 