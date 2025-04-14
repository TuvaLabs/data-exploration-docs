---
sidebar_position: 6.23 # Position nested under AttributeEditComponent
title: RangeFilterComponent
---

# RangeFilterComponent

(*Path likely `src/components/rangeFilterComponent.js` or similar*)

This is a sub-component rendered within [`AttributeEditComponent`](./AttributeEditComponent.md), specifically when editing **numerical** attributes. It provides controls to view and adjust the minimum and maximum values considered for the attribute, potentially acting as a filter.

## Overview

`RangeFilterComponent` allows users to fine-tune the effective range of a numerical attribute, which can impact filtering, axis scales, and color mapping.

-   **Functionality:** Displays the current minimum and maximum values of the attribute's range and provides input fields (e.g., number inputs, sliders) to modify these values.
-   **Filtering:** Adjusting the range here might directly filter the data used in visualizations or analyses, excluding cases outside the specified min/max.
-   **Scope:** The range might represent the actual data range, the range used for axis scaling, or a user-defined filter range.
-   **Data Binding:** Input controls are bound to the temporary state managed by the parent [`AttributeEditComponent`](./AttributeEditComponent.md).

## Key Props (Conceptual)

-   `currentMin`: The current minimum value of the range.
-   `currentMax`: The current maximum value of the range.
-   `dataMin`: The actual minimum value present in the dataset for this attribute (read-only display).
-   `dataMax`: The actual maximum value present in the dataset for this attribute (read-only display).
-   `onMinChange`: Callback to update the minimum range value in the parent state.
-   `onMaxChange`: Callback to update the maximum range value in the parent state.

## Rendering

-   Displays labels like "Minimum" and "Maximum".
-   Renders input controls (number fields, possibly sliders) initialized with `currentMin` and `currentMax`.
-   May display the actual data min/max for reference.
-   Attaches the `onMinChange` and `onMaxChange` handlers.

## Usage

-   Rendered conditionally within [`AttributeEditComponent`](./AttributeEditComponent.md) when the attribute type is Numerical.
-   Allows users to constrain the effective range of a numerical attribute for analysis or visualization purposes.

## Dependencies

-   Contained within and controlled by **[`AttributeEditComponent`](./AttributeEditComponent.md)**.
-   Operates on range properties associated with a numerical **[`Attribute`](../dynDataset/Attribute.md)**. 