---
sidebar_position: 13.3 # Position after OutlierBoxPlotElement
title: BoxAndDotPlotElement
---

# `BoxAndDotPlotElement` Class

(`src/lib/dynplot/plotElement/boxPlotElement.js` / `dotPlotBase.js` - *Note: Actual file paths might differ*)

This class implements a **Box and Dot Plot**, a hybrid visualization that combines the summary statistics of a Box Plot with the display of individual data points (like a Dot Plot).

## Overview

`BoxAndDotPlotElement` likely extends the base [`BoxPlotElement`](./BoxPlotElement.md) and potentially incorporates logic or rendering capabilities from [`DotPlotBase`](./DotPlotBase.md) or its subclasses.

-   **Functionality:** Shows both the overall distribution summary (box, median, whiskers) and the location of each individual data point within each category.
-   **Data Representation:** Renders:
    -   The standard box plot elements (box, median, whiskers) as per [`StandardBoxPlotElement`](./StandardBoxPlotElement.md).
    -   Individual **dots** representing each data case, plotted along the numeric axis within their respective category. Outliers identified by the box plot logic are also shown as dots.
    -   May employ **jittering** (slight random displacement) on the categorical axis to prevent dots with the same numeric value from overlapping completely.
-   **Calculation:** Uses the summary statistics calculation from [`BoxPlotElement`](./BoxPlotElement.md) for the box component and requires access to individual case values for plotting the dots.
-   **Axes:** Uses a **numeric** axis and a **categorical** axis.

## Key Properties & Methods

-   Inherits properties and methods from [`BoxPlotElement`](./BoxPlotElement.md) and [`PlotElement`](./PlotElement.md).
-   May inherit or use methods from [`DotPlotBase`](./DotPlotBase.md) for dot placement and jittering.
-   `constructor()`: Sets flags indicating it's a combined plot.
-   `calcPosition()`: Computes coordinates for the box plot elements *and* determines the position (including potential jitter) for each individual data point dot within its category.
-   Defines its own `kDefaultTitle` (e.g., "Box and Dot Plot") and `kUndoAction`.

## Usage

-   Created by `PlotShaper` when the user selects a "Box and Dot Plot" (or similar) option from the [`<ToolbarComponent />`](../../components/ToolbarComponent.md) and assigns numeric and categorical [`Attributes`](../../dynDataset/Attribute.md).
-   Useful for seeing the summary statistics while also visualizing the density, gaps, and individual values within the distribution.

## Dependencies

-   Extends **[`BoxPlotElement`](./BoxPlotElement.md)**.
-   Potentially related to or uses logic from **[`DotPlotBase`](./DotPlotBase.md)**.
-   Relies on summary statistics calculation from the base box plot class.
-   Needs access to individual case data for dot plotting.
-   Depends on **[`Attribute`](../../dynDataset/Attribute.md)** definitions.
-   Interaction with `PlotShaper` and [`<ToolbarComponent />`](../../components/ToolbarComponent.md).
-   Interaction with rendering components and axis components (`AxisView`). 