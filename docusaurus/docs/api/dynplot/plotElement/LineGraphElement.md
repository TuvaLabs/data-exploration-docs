---
sidebar_position: 4 # Adjust as needed
title: LineGraphElement (Base for Line Charts)
---

# `LineGraphElement` Class

(`src/lib/dynplot/plotElement/dotPlotElement.js`)

This class serves as an intermediate base class for Line Graph visualizations. It extends [`DotPlotBase`](./DotPlotBase.md) because it relies on the logic for positioning individual data points (nodes), but it adds the crucial functionality of drawing lines connecting these points.

## Role and Purpose

`LineGraphElement` bridges the gap between positioning individual points ([`DotPlotBase`](./DotPlotBase.md)) and drawing connecting lines:

-   **Inherits Point Positioning:** Uses the `calcPosition` logic from [`DotPlotBase`](./DotPlotBase.md) to determine where the nodes (points) of the line graph should be located based on X and Y axes, including handling stacking if relevant (though less common for line graphs).
-   **Adds Line Drawing:** Implements the `calcAdornments` method. This method is responsible for:
    -   Retrieving the calculated point positions.
    -   Sorting the points appropriately for line connection (e.g., by X-axis value).
    -   Generating the SVG path strings for the line segments.
    -   Handling gaps in the line where data is missing or filtered.
    -   Drawing the lines using `PlotAdornments`.
    -   Potentially handling coloring or styling of different lines if multiple lines are present (logic might be further specialized in subclasses).
-   **Tooltip Handling:** Manages tooltips specifically for the line segments themselves.

## Core Concepts

-   **Points + Lines:** Combines the concept of individual data points (managed by [`DotPlotBase`](./DotPlotBase.md)) with connecting line segments (managed by `LineGraphElement`'s `calcAdornments`).
-   **Sorting for Connection:** Points usually need to be sorted based on the independent axis variable before lines can be drawn correctly.
-   **Handling Gaps:** Logic is required to detect missing data points and avoid drawing lines across gaps.

## Key Properties

-   Inherits properties from [`DotPlotBase`](./DotPlotBase.md).
-   May define properties related to line styling (though styling might also be managed globally or by subclasses).

## Key Methods

-   **`calcAdornments()`:** The core override. This method calculates and draws the line segments connecting the points whose positions were determined by the inherited `calcPosition`.
-   Inherits `calcPosition`, `calcMissingValueCases`, etc., from [`DotPlotBase`](./DotPlotBase.md).

## Subclassing

Concrete line graph types extend `LineGraphElement`:

-   [`LineGraphSingleElement`](./LineGraphSingleElement.md): For simple line graphs with one line.
-   [`LineAndCategoryElement`](./LineAndCategoryElement.md): For line graphs where data is split into multiple lines based on a categorical legend attribute.

Subclasses might refine the sorting, line styling, or tooltip behavior.

## Dependencies

-   Extends **[`DotPlotBase`](./DotPlotBase.md)**.
-   Relies on **`PlotAdornments`** (via `this.plotShaper.adornments`) to draw the actual SVG line paths.
-   Uses **`AxisView`** instances for coordinate mapping.
-   Uses **[`Dyn.dataSet`](../../dynDataset/DataSet.md)** to access data values. 