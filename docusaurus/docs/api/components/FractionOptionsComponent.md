---
sidebar_position: 6.28 # Position nested under AttributeEditComponent
title: FractionOptionsComponent
---

# FractionOptionsComponent

(*Path likely `src/components/fractionOptionsComponent.js` or similar*)

This is a sub-component potentially rendered within [`AttributeEditComponent`](./AttributeEditComponent.md), likely when editing **numerical** attributes that are intended to be displayed as **fractions**.

## Overview

For certain numerical data, displaying values as fractions (e.g., 1/2, 3/4) might be more intuitive than decimals (0.5, 0.75). This component provides options to control this fractional representation.

-   **Functionality:** Offers settings related to fraction display, such as:
    -   Toggling between decimal and fraction display.
    -   Setting a maximum denominator.
    -   Choosing simplification rules (e.g., always show simplest form).
-   **Impact:** Changes how numerical values for this attribute are formatted and displayed, assuming the underlying system supports fractional rendering.
-   **Data Binding:** Selected options are bound to the temporary state managed by the parent [`AttributeEditComponent`](./AttributeEditComponent.md).

## Key Props (Conceptual)

-   `currentFractionSettings`: An object holding the current settings (e.g., `displayAsFraction: true`, `maxDenominator: 100`).
-   `onSettingsChange`: A callback function (provided by `AttributeEditComponent`) to update the fraction settings in the parent's state.

## Rendering

-   Renders labels and controls (e.g., checkboxes, number inputs) corresponding to the available fraction display options.
-   Initializes controls based on `currentFractionSettings`.
-   Attaches handlers to update the settings via `onSettingsChange`.

## Usage

-   Rendered conditionally within [`AttributeEditComponent`](./AttributeEditComponent.md) when the attribute type is Numerical and fractional display is relevant/supported.
-   Allows users to format numerical data specifically as fractions.

## Dependencies

-   Contained within and controlled by **[`AttributeEditComponent`](./AttributeEditComponent.md)**.
-   Modifies formatting properties associated with a numerical **[`Attribute`](../dynDataset/Attribute.md)**.
-   Relies on downstream components (like **[`AxisView`](../dynplot/AxisView.md)**, tooltips, **[`CaseCardComponent`](./CaseCardComponent.md)**) to support and implement fractional rendering based on these settings. 