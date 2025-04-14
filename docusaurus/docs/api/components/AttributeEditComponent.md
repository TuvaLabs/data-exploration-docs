---
sidebar_position: 6.2 # Position after AttributeListComponent
title: AttributeEditComponent
---

# AttributeEditComponent

(*Path likely `src/components/attributeEditComponent.js` or similar*)

This component provides the main user interface (likely a modal or a dedicated view within [`CaseCardComponent`](./CaseCardComponent.md)) for editing the properties of a selected [`Attribute`](../dynDataset/Attribute.md).

## Overview

When a user clicks the edit icon for an attribute in the [`AttributeListComponent`](./AttributeListComponent.md), the `AttributeEditComponent` is displayed. It acts as a container, presenting various specific editing controls, often by utilizing several specialized sub-components.

-   **Functionality:** Orchestrates the display of different editing options based on the type and properties of the attribute being edited.
-   **Data Source:** Receives the specific [`Attribute`](../dynDataset/Attribute.md) object to be edited as a prop.
-   **Saving/Canceling:** Provides mechanisms (e.g., Save/Apply and Cancel/Close buttons) to commit or discard the changes made.

## Contained Sub-components & Features

`AttributeEditComponent` typically renders and manages several sub-components to provide focused functionality:

-   **`NameDescEditComponent`:** Allows editing the attribute's name and description.
-   **`DataTypeComponent`:** Allows changing the attribute's data type (e.g., from numerical to categorical, text, date, numerical interval). May conditionally render other components based on the selected type.
-   **`RangeFilterComponent`:** (For numerical attributes) Allows setting or adjusting the minimum and maximum range, potentially applying filters.
-   **`NumericalColorPickerComponent`:** (For numerical attributes) Allows selecting the color or gradient used for the attribute's scale.
-   **`CategoricalColorEditor`:** (For categorical attributes) Allows viewing and modifying the colors assigned to each specific category (This might be part of `DataTypeComponent` or a separate component).
-   **`SortOrderComponent`:** Allows setting the sort order for attribute values/categories (e.g., alphabetical, reverse), which can affect axis display.
-   **`NumericDecimalsComponent`:** (For numerical attributes) Allows specifying the number of decimal places for display.
-   **`FractionOptionsComponent`:** (For numerical attributes, possibly when represented as fractions) Provides options for fraction display.
-   **`NumericalIntervalComponent`:** (For numerical interval data type) Provides controls specific to defining intervals.
-   **`MissingValueComponent`:** Displays information about missing values (e.g., count) and potentially allows selection of cases with missing values.
-   **`DeleteAttributeComponent`:** Provides the option to delete the attribute, likely only enabled for user-created custom attributes.

## Usage

-   Launched or displayed by [`CaseCardComponent`](./CaseCardComponent.md) when an attribute edit is requested.
-   Presents a focused interface for modifying a single attribute's configuration.
-   Handles the overall state management for the editing session and coordinates updates via callbacks or state management (`Dyn`).

## Dependencies

-   Triggered by **[`CaseCardComponent`](./CaseCardComponent.md)** / **[`AttributeListComponent`](./AttributeListComponent.md)**.
-   Operates on an **[`Attribute`](../dynDataset/Attribute.md)** object.
-   Contains and coordinates multiple sub-components (listed above).
-   Interacts with application state (`Dyn`) to save changes. 