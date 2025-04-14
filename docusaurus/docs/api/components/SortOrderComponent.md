---
sidebar_position: 6.26 # Position nested under AttributeEditComponent
title: SortOrderComponent
---

# SortOrderComponent

(*Path likely `src/components/sortOrderComponent.js` or similar*)

This is a sub-component rendered within [`AttributeEditComponent`](./AttributeEditComponent.md) that allows the user to specify the **sort order** for an attribute's values or categories, primarily affecting how they are displayed on plot axes.

## Overview

`SortOrderComponent` provides options to control the sequence in which categories (for categorical attributes) or potentially numerical bins are arranged on an axis (e.g., the categorical axis of a Bar Chart or Box Plot).

-   **Functionality:** Presents options for sorting, such as:
    -   Default/Data Order.
    -   Alphabetical (A-Z).
    -   Reverse Alphabetical (Z-A).
    -   Custom (Potentially allowing manual drag-and-drop reordering for categorical attributes).
    -   Numerical Order (Ascending/Descending) - if applicable to categorical attributes with numerical meaning or for bin ordering.
-   **Impact:** Changes the order of labels and corresponding visual elements (bars, boxes) along an axis managed by [`AxisView`](../dynplot/AxisView.md).
-   **Data Binding:** The selected sort order is bound to the temporary state managed by the parent [`AttributeEditComponent`](./AttributeEditComponent.md).

## Key Props (Conceptual)

-   `currentSortOrder`: The currently selected sort order setting.
-   `availableSortOptions`: An array of possible sort options.
-   `onSortOrderChange`: A callback function (provided by `AttributeEditComponent`) to update the selected sort order in the parent's state.

## Rendering

-   Renders a label (e.g., "Sort Order").
-   Provides selection controls (e.g., dropdown, radio buttons) listing the `availableSortOptions`.
-   Sets the initial selection based on `currentSortOrder`.
-   Attaches the `onSortOrderChange` handler.

## Usage

-   Rendered within [`AttributeEditComponent`](./AttributeEditComponent.md), likely applicable to both categorical and potentially some numerical representations (like binned data).
-   Allows users to customize the presentation order on axes for better readability or specific analytical comparisons.

## Dependencies

-   Contained within and controlled by **[`AttributeEditComponent`](./AttributeEditComponent.md)**.
-   Modifies sorting properties associated with an **[`Attribute`](../dynDataset/Attribute.md)**.
-   The chosen setting affects rendering handled by **[`AxisView`](../dynplot/AxisView.md)** and potentially the layout calculations within **[`PlotElement`](../dynplot/plotElement/PlotElement.md)** subclasses. 