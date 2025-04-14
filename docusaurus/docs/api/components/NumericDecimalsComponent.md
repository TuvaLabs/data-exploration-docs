---
sidebar_position: 6.27 # Position nested under AttributeEditComponent
title: NumericDecimalsComponent
---

# NumericDecimalsComponent

(*Path likely `src/components/numericDecimalsComponent.js` or similar*)

This is a sub-component rendered within [`AttributeEditComponent`](./AttributeEditComponent.md), specifically when editing **numerical** attributes. It provides controls for specifying the number of **decimal places** used when displaying values of this attribute.

## Overview

`NumericDecimalsComponent` allows users to control the precision of displayed numerical values, affecting labels on axes, tooltips, and potentially the case card display.

-   **Functionality:** Presents a control (e.g., a number input, dropdown) to select the desired number of decimal places (e.g., 0, 1, 2, 3, ...).
-   **Impact:** Changes how numerical values for this attribute are formatted and displayed throughout the application.
-   **Data Binding:** The selected number of decimal places is bound to the temporary state managed by the parent [`AttributeEditComponent`](./AttributeEditComponent.md).

## Key Props (Conceptual)

-   `currentDecimalPlaces`: The currently configured number of decimal places.
-   `onDecimalPlacesChange`: A callback function (provided by `AttributeEditComponent`) to update the selected value in the parent's state.

## Rendering

-   Renders a label (e.g., "Decimal Places").
-   Provides a number input or dropdown control to set the value.
-   Initializes the control with `currentDecimalPlaces`.
-   Attaches the `onDecimalPlacesChange` handler.

## Usage

-   Rendered conditionally within [`AttributeEditComponent`](./AttributeEditComponent.md) when the attribute type is Numerical.
-   Allows users to adjust display precision for clarity or based on the nature of the data.

## Dependencies

-   Contained within and controlled by **[`AttributeEditComponent`](./AttributeEditComponent.md)**.
-   Modifies formatting properties associated with a numerical **[`Attribute`](../dynDataset/Attribute.md)**.
-   Affects display formatting potentially used by **[`AxisView`](../dynplot/AxisView.md)**, tooltips within **[`PlotView`](../dynplot/PlotView.md)**, and **[`CaseCardComponent`](./CaseCardComponent.md)**. 