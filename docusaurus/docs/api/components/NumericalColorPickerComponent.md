---
sidebar_position: 6.24 # Position nested under AttributeEditComponent
title: NumericalColorPickerComponent
---

# NumericalColorPickerComponent

(*Path likely `src/components/numericalColorPickerComponent.js` or similar*)

This is a sub-component rendered within [`AttributeEditComponent`](./AttributeEditComponent.md), specifically when editing **numerical** attributes. It provides an interface for selecting the color or gradient used to represent the attribute's values visually.

## Overview

Numerical attributes are often mapped to a color scale (either a single hue with varying intensity or a multi-color gradient) in visualizations. This component allows the user to customize that color mapping.

-   **Functionality:** Displays the current color/gradient selection and allows the user to choose a new one. This might involve:
    -   Selecting a single base color (for sequential scales).
    -   Choosing from predefined gradient options (e.g., Viridis, Plasma, Coolwarm).
    -   Potentially defining custom gradient stops and colors.
-   **Data Binding:** The selection is bound to the temporary state managed by the parent [`AttributeEditComponent`](./AttributeEditComponent.md).

## Key Props (Conceptual)

-   `currentColorScale`: Information about the currently selected color or gradient (e.g., scale name, base color).
-   `availableScales`: A list of predefined scales/gradients the user can choose from.
-   `onColorScaleChange`: A callback function (provided by `AttributeEditComponent`) to update the selected color scale in the parent's state.

## Rendering

-   Displays the current color selection (e.g., a swatch or preview of the gradient).
-   Provides controls to select a new color/gradient (e.g., color input, dropdown list of scales, interactive gradient editor).
-   Attaches the `onColorScaleChange` handler to the controls.

## Usage

-   Rendered conditionally within [`AttributeEditComponent`](./AttributeEditComponent.md) when the attribute type is Numerical.
-   Allows users to customize the visual encoding of numerical data using color.

## Dependencies

-   Contained within and controlled by **[`AttributeEditComponent`](./AttributeEditComponent.md)**.
-   Modifies color mapping properties associated with a numerical **[`Attribute`](../dynDataset/Attribute.md)**.
-   May use a color manipulation or charting library (e.g., D3, Chroma.js) for scale generation or previews. 