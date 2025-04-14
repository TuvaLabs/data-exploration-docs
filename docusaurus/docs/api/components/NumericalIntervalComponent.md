---
sidebar_position: 6.29 # Position nested under AttributeEditComponent
title: NumericalIntervalComponent
---

# NumericalIntervalComponent

(*Path likely `src/components/numericalIntervalComponent.js` or similar*)

This is a sub-component rendered within [`AttributeEditComponent`](./AttributeEditComponent.md), specifically when the attribute's data type is set to **Numerical Interval** via the [`DataTypeComponent`](./DataTypeComponent.md).

## Overview

When data represents intervals or ranges (e.g., age groups like 10-19, 20-29), this component provides the necessary controls to define how these intervals are managed or displayed.

-   **Functionality:** Offers controls specific to interval data, which might include:
    -   Defining interval boundaries (if not inherent in the data).
    -   Setting display formatting for intervals (e.g., "10-19", "[10, 20)").
    -   Potentially options for how intervals are treated in calculations or visualizations.
-   **Data Binding:** Options are bound to the temporary state managed by the parent [`AttributeEditComponent`](./AttributeEditComponent.md).

## Key Props (Conceptual)

-   `currentIntervalSettings`: An object holding the current settings related to interval definition and formatting.
-   `onSettingsChange`: A callback function (provided by `AttributeEditComponent`) to update the interval settings in the parent's state.

## Rendering

-   Renders labels and controls specific to defining and formatting numerical intervals.
-   Initializes controls based on `currentIntervalSettings`.
-   Attaches handlers to update the settings via `onSettingsChange`.

## Usage

-   Rendered conditionally within [`AttributeEditComponent`](./AttributeEditComponent.md) only when the data type is set to "Numerical Interval".
-   Allows customization of how interval data is handled and presented.

## Dependencies

-   Contained within and controlled by **[`AttributeEditComponent`](./AttributeEditComponent.md)**.
-   Visibility is often controlled by **[`DataTypeComponent`](./DataTypeComponent.md)**.
-   Modifies properties associated with a Numerical Interval **[`Attribute`](../dynDataset/Attribute.md)**. 