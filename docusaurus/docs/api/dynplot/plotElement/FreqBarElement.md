---
sidebar_position: 7 # Adjust position relative to other BarElement subclasses
title: FreqBarElement (Bar Chart of Frequencies)
---

# `FreqBarElement` Class

(`src/lib/dynplot/plotElement/barElement.js`)

This class implements a **Bar Chart of Frequencies**, one of the most common types of bar charts. Each bar represents the **count** (frequency) of cases within a specific category or bin.

## Overview

`FreqBarElement` extends the base [`BarElement`](./BarElement.md) class.

-   **Functionality:** Visualizes the distribution of a categorical variable or a binned numeric variable.
-   **Data Representation:** The length (or height) of each bar corresponds to the number of data points (cases) falling into that bar's category or bin.
-   **Configuration:** Sets the `isFreq` flag to `true` in its constructor, signaling to the base [`BarElement`](./BarElement.md) logic that bar lengths should be based on frequency counts.
-   **Axes:** Typically uses a categorical axis (or a binned numeric axis) to define the bars and a numeric axis to represent the frequency counts.

## Key Properties & Methods

-   Inherits most properties and methods from [`BarElement`](./BarElement.md).
-   Sets `isFreq = true`.
-   Overrides `replaces()` to specify which plot types it can replace.
-   Defines its own `kDefaultTitle` (e.g., "bar chart of counts") and `kUndoAction`.

## Usage

-   Created by `PlotShaper` when the user selects the standard "Bar Chart" option from the [`<ToolbarComponent />`](../../components/ToolbarComponent.md) (often the default bar chart type).
-   Used to answer questions like "How many cases are there in each category?" or "What is the distribution of values within these bins?".

## Helper Class: `BarSums`

-   Crucially relies on the `BarSums` helper class (defined within the same file) to calculate the frequencies for each bar. `BarSums` iterates through the data (`iCases`), determines the category or bin for each case based on the axis configuration (`valueAxisRole`, `cellAxisRole`), and accumulates the counts (`sumArray`, `weightArray`).

## Dependencies

-   Extends **[`BarElement`](./BarElement.md)**.
-   Uses **`BarSums`** helper class for frequency calculation.
-   Depends on [`Attribute`](../Attribute.md) definitions for axis roles.
-   Interaction with `PlotShaper` and [`<ToolbarComponent />`](../../components/ToolbarComponent.md) for creation. 