---
sidebar_position: 11 # Adjust position relative to other BarElement subclasses
title: StretchedBarElement (Stretched Bar Chart / Percent Bar Chart)
---

# `StretchedBarElement` Class

(`src/lib/dynplot/plotElement/barElement.js`)

This class implements a **Stretched Bar Chart**, also known as a **Percent Bar Chart**. In this type of chart, each primary bar (representing a category or bin) is scaled to represent 100%, and the segments within each bar show the *proportion* or *percentage* of cases belonging to different sub-categories defined by a legend attribute.

## Overview

`StretchedBarElement` extends the base [`BarElement`](./BarElement.md) class, likely sharing much logic with [`FreqBarElement`](./FreqBarElement.md) but with specific modifications for percentage scaling.

-   **Functionality:** Visualizes the relative proportions of sub-categories within each main category.
-   **Data Representation:** All bars have the same length (representing 100%). The segments within each bar are proportionally sized based on the count of cases for each legend category within the main bar's category.
-   **Configuration:**
    -   Sets the `barsStretched` flag to `true` in its constructor.
    -   Inherently requires a **legend attribute** to define the sub-category segments.
    -   Likely sets `isFreq` to `true` as the proportions are based on frequency counts.
-   **Axes:** Requires a categorical axis (or binned numeric) to define the main bars and a numeric axis scaled from 0 to 1 (or 0% to 100%) to represent the proportions.

## Key Properties & Methods

-   Inherits most properties and methods from [`BarElement`](./BarElement.md).
-   Sets `barsStretched = true`.
-   Requires a legend attribute defined in `Dyn.legendAttribute`.
-   Overrides `calcPlotSpecificRange()` to force the numeric axis range to 0-1 (or similar for percentage).
-   Overrides `calcPosition()`: This method will contain the core logic for stretching. It uses the counts per sub-category (calculated by `BarSums`) within each main category, calculates the total count for the main category, and then determines the start and end positions of each segment as a proportion of the total bar length (100%).
-   Defines its own `kDefaultTitle` (e.g., "percent bar chart") and `kUndoAction`.

## Usage

-   Created by `PlotShaper` when the user selects an option like "Stretched Bar Chart" or "Percent Bar Chart" from the [`<ToolbarComponent />`](../../components/ToolbarComponent.md), typically requiring both a primary categorical/binned attribute and a legend attribute.
-   Used to compare the relative proportions of sub-categories across different main categories, answering questions like "What percentage of each group falls into these sub-categories?".

## Helper Class: `BarSums`

-   Relies on `BarSums` to calculate the raw counts for each sub-category (defined by the legend attribute) within each main category (defined by the primary axis attribute). `BarSums` likely stores these counts in a way that `calcPosition` can easily access them (e.g., nested arrays or maps).

## Dependencies

-   Extends **[`BarElement`](./BarElement.md)** (and related to **[`FreqBarElement`](./FreqBarElement.md)**).
-   Uses **`BarSums`** helper class for frequency counts per sub-category.
-   Requires **[`Attribute`](../Attribute.md)** definitions for the primary axis and the legend.
-   Interaction with `PlotShaper` and [`<ToolbarComponent />`](../../components/ToolbarComponent.md) for creation. 