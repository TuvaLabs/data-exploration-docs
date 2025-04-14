---
sidebar_position: 6.22 # Position nested under AttributeEditComponent
title: DataTypeComponent
---

# DataTypeComponent

(*Path likely `src/components/dataTypeComponent.js` or similar*)

This is a sub-component rendered within [`AttributeEditComponent`](./AttributeEditComponent.md) that allows the user to view and change the **data type** assigned to the selected attribute.

## Overview

`DataTypeComponent` typically presents a dropdown menu or radio buttons listing the available data types. Changing the data type fundamentally alters how the application interprets and visualizes the attribute's data and often changes the available options within the parent [`AttributeEditComponent`](./AttributeEditComponent.md).

-   **Functionality:** Displays the current data type and provides controls (e.g., a dropdown) to select a new type.
-   **Impact:** Changing the type might:
    -   Enable or disable other editing sub-components (e.g., `RangeFilterComponent` is only relevant for numerical types, `CategoricalColorEditor` only for categorical).
    -   Affect default visualization choices.
    -   Trigger data re-processing or validation if applicable.
-   **Data Binding:** The selection control is bound to the temporary state managed by the parent [`AttributeEditComponent`](./AttributeEditComponent.md) during the editing session.

## Supported Data Types (Examples)

The specific data types available may vary, but common types include:

-   **Numerical:** Standard numeric values (integers or decimals).
-   **Categorical:** Distinct text or numeric values representing groups or categories.
-   **Text:** Free-form string data.
-   **Date/Time:** Values representing dates and/or times.
-   **Numerical Interval:** Represents a range or interval (e.g., for binned data).
-   *(Others might exist, e.g., Boolean, Geographic Coordinates, Image URL)*

## Key Props (Conceptual)

-   `currentDataType`: The data type of the attribute being edited.
-   `availableTypes`: An array of strings representing the selectable data types.
-   `onDataTypeChange`: A callback function (provided by `AttributeEditComponent`) to update the selected data type in the parent's state.

## Rendering

-   Renders a label indicating the purpose (e.g., "Data Type").
-   Renders a selection control (e.g., `<select>`) populated with `availableTypes`.
-   Sets the initial value of the control to `currentDataType`.
-   Attaches the `onDataTypeChange` handler to the selection control.
-   May conditionally render other components (like [`NumericalIntervalComponent`](./NumericalIntervalComponent.md)) if a specific type (e.g., Numerical Interval) is selected.

## Usage

-   Rendered as part of the layout within [`AttributeEditComponent`](./AttributeEditComponent.md).
-   Allows users to correct misidentified data types or intentionally change how data is treated (e.g., treating numerical codes as categories).

## Dependencies

-   Contained within and controlled by **[`AttributeEditComponent`](./AttributeEditComponent.md)**.
-   Modifies a core property of an **[`Attribute`](../dynDataset/Attribute.md)**.
-   The selected type influences the visibility/behavior of other sibling sub-components within `AttributeEditComponent`. 