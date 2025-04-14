---
sidebar_position: 5 # Adjust position relative to other components
title: LegendComponent
---

# LegendComponent

(*Path likely `src/components/legendComponent.js` or similar*)

This component renders the legend for the current plot, explaining the mapping between visual elements (colors, shapes, sizes) and the data categories or ranges they represent.

## Overview

The `<LegendComponent />` typically appears alongside the main plot area (rendered by [`<PlotView />`](../dynplot/PlotView.md)) when a legend attribute is active.

-   **Functionality:** Displays a list of legend items, each showing a visual swatch (e.g., a colored square, line segment, or symbol) and the corresponding category name or value range from the legend [`Attribute`](../dynDataset/Attribute.md).
-   **Data Source:** Gets its information from the currently active legend [`Attribute`](../dynDataset/Attribute.md) (often stored in `Dyn.legendAttribute` or similar state) and the specific [`PlotElement`](../dynplot/plotElement/PlotElement.md) being displayed, which determines *how* the legend attribute is used (e.g., for color, size).
-   **Interactivity:** May support interactivity, such as:
    -   Highlighting corresponding plot elements on hover.
    -   Filtering or selecting data by clicking on legend items.
-   **Types Handled:** Needs to adapt to different attribute types used for legends:
    -   **Categorical:** Displays distinct swatches and labels for each category.
    -   **Numeric (for color/size):** May display a continuous gradient or discrete steps with corresponding numeric values.

## Key Props (Conceptual)

-   `legendAttribute`: The [`Attribute`](../dynDataset/Attribute.md) object being used for the legend.
-   `plotElement`: The active [`PlotElement`](../dynplot/plotElement/PlotElement.md) instance, providing context on how the legend is used (e.g., color mapping, symbol mapping).
-   `colorMap` / `scale`: Information mapping attribute values/categories to visual properties (e.g., a D3 scale object).

## Rendering

-   Iterates through the categories or representative values of the `legendAttribute`.
-   For each item, renders a visual swatch (using SVG or styled HTML elements) matching the plot's visual encoding.
-   Renders the corresponding category name or value.
-   Arranges items, potentially handling scrolling if the list is long.

## Usage

-   Typically included as part of the main application layout, often within or adjacent to the [`<PlotView />`](../dynplot/PlotView.md).
-   Its visibility is often controlled based on whether a legend attribute is selected in the UI (e.g., via the [`<ToolbarComponent />`](./ToolbarComponent.md)).
-   Essential for plots like stacked/stretched bars ([`<StretchedBarElement />`](../dynplot/plotElement/StretchedBarElement.md)), multi-line charts ([`<LineAndCategoryElement />`](../dynplot/plotElement/LineAndCategoryElement.md)), or scatter plots colored by category ([`ScatterPlotElement`](../dynplot/plotElement/ScatterPlotElement.md)).

## Dependencies

-   Relies on **[`Attribute`](../dynDataset/Attribute.md)** data (categories, type, values).
-   Depends on the active **[`PlotElement`](../dynplot/plotElement/PlotElement.md)** for context and visual mapping details.
-   Often interacts with **[`PlotView`](../dynplot/PlotView.md)** or a shared state management system (`Dyn`).
-   May use utility functions for color generation or scaling. 