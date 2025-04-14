---
sidebar_position: 4.2 # Adjust as needed
title: LineAndCategoryElement (Line Chart by Category)
---

# `LineAndCategoryElement` Class

(`src/lib/dynplot/plotElement/dotPlotElement.js`)

This class implements a Line Chart where the data is split into multiple distinct lines based on the categories of a legend attribute.

## Overview

`LineAndCategoryElement` extends the [`LineGraphElement`](./LineGraphElement.md) base class.

-   **Functionality:** It uses the inherited logic from [`LineGraphElement`](./LineGraphElement.md) for positioning points and the base line drawing, but adds specific logic within `calcAdornments` (or methods called by it) to:
    -   Group the data points based on the categories of the currently selected legend attribute (`Dyn.dataSet.getSelectedAttribute()`). See [`Attribute`](../../dynDataset/Attribute.md).
    -   Draw a separate line segment path for each category.
    -   Apply different styling (usually color) to each line based on the category's assigned color (from the legend attribute's `colorMap` or derived colors).
-   **Use Case:** Visualizing trends of a numeric variable (Y-axis) against another variable (X-axis), broken down by different groups defined by a third (legend) categorical attribute.
-   **Configuration:** Sets its specific `primaryType` (`kControlsLineAndCategoryGraph`) and `replaceType` (`kControlsShape`).
-   Defines its own `kDefaultTitle` and `kUndoAction`.

## Usage

An instance is created by `PlotShaper` when the user selects "Line Chart by Category" (or similar) from the [`<ToolbarComponent />`](../../components/ToolbarComponent.md). It requires attributes on the X and Y axes and relies on a categorical attribute being selected for the legend (either dropped on the legend drop zone or selected via the [`<CaseCardComponent />`](../../components/CaseCardComponent.md)).

## Dependencies

-   Extends **[`LineGraphElement`](./LineGraphElement.md)**.
-   Relies heavily on the selected **legend attribute** in [`Dyn.dataSet`](../../dynDataset/DataSet.md) to group data and style lines. 