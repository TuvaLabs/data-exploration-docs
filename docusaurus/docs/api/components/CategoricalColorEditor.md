---
sidebar_position: 6.25 # Position nested under AttributeEditComponent
title: CategoricalColorEditor
---

# CategoricalColorEditor

(*Path likely `src/components/categoricalColorEditor.js` or similar*)

This is a sub-component rendered within [`AttributeEditComponent`](./AttributeEditComponent.md), specifically when editing **categorical** attributes. It displays the distinct categories of the attribute and allows the user to modify the color assigned to each category.

## Overview

Categorical attributes typically use a unique color for each distinct category in visualizations. This component provides the interface to manage these category-color mappings.

-   **Functionality:**
    -   Lists all unique categories found in the attribute's data.
    -   Displays the current color assigned to each category (often via a color swatch).
    -   Provides a mechanism (e.g., clicking a swatch opens a color picker) to change the color for individual categories.
    -   May offer options to apply predefined color palettes.
-   **Data Binding:** Changes are typically managed within the temporary state of the parent [`AttributeEditComponent`](./AttributeEditComponent.md) until saved.

## Key Props (Conceptual)

-   `categories`: An array or map containing the unique categories and their currently assigned colors.
-   `onColorChange`: A callback function (provided by `AttributeEditComponent`) that takes the category and the new color to update the parent state.

## Rendering

-   Iterates through the `categories` prop.
-   For each category, renders:
    -   The category name (label).
    -   A color swatch displaying the current color.
    -   An interactive element (e.g., the swatch itself) that triggers a color picker or selection mechanism when clicked.
-   The color picker allows selecting a new color, which then calls `onColorChange`.

## Usage

-   Rendered conditionally within [`AttributeEditComponent`](./AttributeEditComponent.md) when the attribute type is Categorical.
-   Provides fine-grained control over the visual appearance of different categories in plots.

## Dependencies

-   Contained within and controlled by **[`AttributeEditComponent`](./AttributeEditComponent.md)**.
-   Operates on the category list and color mappings of a categorical **[`Attribute`](../dynDataset/Attribute.md)**.
-   Likely uses a **Color Picker** component for selecting new colors. 