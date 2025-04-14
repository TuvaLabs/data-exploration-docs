---
sidebar_position: 1 # Position first within dynDataset
title: Attribute
---

# Attribute Class/Object

(*Path likely `src/lib/dynDataset/attribute.js` or similar*)

This class (or object structure) represents a single **attribute** (also known as a column, feature, or variable) within the dataset. It holds not only the data values but also metadata and configuration settings that define how the attribute is interpreted, displayed, and used throughout the application.

## Overview

An `Attribute` instance encapsulates everything known about a specific column of data.

-   **Core Role:** Represents a single dimension of the dataset (e.g., 'Age', 'Gender', 'Sales', 'Date').
-   **Metadata:** Stores essential information about the attribute, such as:
    -   `id`: A unique identifier.
    -   `name`: The human-readable name (editable via [`AttributeEditComponent`](../components/AttributeEditComponent.md)).
    -   `description`: A longer description (editable).
    -   `type`: The assigned data type (e.g., 'numerical', 'categorical', 'date', managed by [`DataTypeComponent`](../components/DataTypeComponent.md)).
    -   `isUserCreated`: Flag indicating if it's an original attribute or one created via formula ([`NewAttributeComponent`](../components/NewAttributeComponent.md)).
    -   `formula`: The formula string, if it's a calculated attribute.
-   **Configuration:** Holds settings controlling its behavior and appearance:
    -   `colorMap`: Mapping of values/categories to colors (managed by [`NumericalColorPickerComponent`](../components/NumericalColorPickerComponent.md) / [`CategoricalColorEditor`](../components/CategoricalColorEditor.md)).
    -   `sortOrder`: The sort order for display (managed by [`SortOrderComponent`](../components/SortOrderComponent.md)).
    -   `range`: Min/max range settings (managed by [`RangeFilterComponent`](../components/RangeFilterComponent.md)).
    -   `displayPrecision`: Number of decimal places for numerical display (managed by [`NumericDecimalsComponent`](../components/NumericDecimalsComponent.md)).
    -   `fractionSettings`: Options for fractional display (managed by [`FractionOptionsComponent`](../components/FractionOptionsComponent.md)).
    -   Other type-specific settings (e.g., interval definitions).
-   **Values:** While the `Attribute` object primarily holds metadata, it's logically associated with the actual data values for all cases in the dataset (often accessed via the main dataset structure).

## Key Properties (Conceptual Example)

```javascript
{
  id: 'att123',
  name: 'Age',
  description: 'Age of the participant in years.',
  type: 'numerical',
  isUserCreated: false,
  formula: null,
  colorMap: { type: 'sequential', baseColor: '#4682B4' }, // Example
  sortOrder: 'ascending',
  range: { min: 18, max: 65 },
  displayPrecision: 0,
  // ... other properties
}
```

## Usage

-   `Attribute` objects are fundamental building blocks used throughout the system.
-   Listed and managed visually via [`CaseCardComponent`](../components/CaseCardComponent.md) and its sub-components.
-   Assigned to axes or legends in [`PlotView`](../dynplot/PlotView.md) via drag-and-drop or the [`ToolbarComponent`](../components/ToolbarComponent.md).
-   Used by [`PlotElement`](../dynplot/plotElement/PlotElement.md) subclasses to determine plot type, scales, positions, and visual encoding.
-   Used by [`AxisView`](../dynplot/AxisView.md) to render correct labels and scales.
-   Displayed in the [`CaseTableComponent`](../components/CaseTableComponent.md).

## Dependencies

-   Central part of the **`dynDataset`** core.
-   Interacts heavily with UI components in `api/components/` for display and editing.
-   Crucial input for components in `api/dynplot/` for visualization configuration.
-   Associated with the main **DataSet** structure that holds the actual case values. 