---
sidebar_position: 5 # Position after AttributeFormula
title: CaseFilter
---

# CaseFilter Class

(*Path likely `src/lib/dynDataset/caseFilter.js` or similar*)

This helper class is responsible for managing the definition and application of filters to the dataset, determining which cases are considered "active".

## Overview

Filtering allows users to focus on specific subsets of the data based on criteria applied to one or more attributes. The `CaseFilter` class likely encapsulates the state of these filters and the logic to determine which cases satisfy them.

-   **Functionality:**
    -   **Stores Filter Definitions:** Maintains a collection of active filter criteria (e.g., "Age > 30", "Gender == 'Female'", "Date between X and Y").
    -   **Applies Filters:** Takes the full set of cases and returns the subset (e.g., an array of indices) that matches *all* active filter criteria.
    -   **Manages Filter Updates:** Provides methods to add, remove, or modify individual filter criteria.
-   **Integration:** An instance of `CaseFilter` is likely held and managed by the main [`DataSet`](./DataSet.md) class.

## Filter Definition (Conceptual)

Filter criteria might be represented as objects, potentially including:

-   `attributeId`: The ID of the attribute being filtered.
-   `operator`: The comparison operator (e.g., `>`, `<`, `==`, `!=`, `in`, `between`).
-   `value`: The value(s) to compare against.
-   `type`: Indication of filter type (e.g., numerical range, categorical selection).

## Key Properties (Conceptual)

-   `activeFilters`: An array or map storing the current filter definitions.
-   `filteredIndices`: The cached array of indices for cases passing the current filters.

## Key Methods (Conceptual)

-   `addFilter(filterDefinition)`: Adds a new filter criterion.
-   `removeFilter(attributeId)`: Removes the filter associated with a specific attribute.
-   `updateFilter(filterDefinition)`: Modifies an existing filter.
-   `clearFilters()`: Removes all active filters.
-   `getFilteredIndices(allCases)`: Calculates and returns the indices of cases passing the current filters.
-   `hasFilters()`: Returns true if any filters are active.

## Usage

-   An instance is likely created and managed by **[`DataSet`](./DataSet.md)**.
-   Filters might be added or modified based on user interactions, such as:
    -   Adjusting ranges in [`RangeFilterComponent`](../components/RangeFilterComponent.md).
    -   Selecting categories in a plot legend ([`LegendComponent`](../components/LegendComponent.md)) or axis.
    -   Dedicated filtering UI elements.
-   The `filteredIndices` are used by `DataSet` to determine the `activeCaseIndices` (potentially in combination with sampling).

## Dependencies

-   Managed by **[`DataSet`](./DataSet.md)**.
-   Operates on case data and **[`Attribute`](./Attribute.md)** values.
-   Requires logic to evaluate different filter types and operators against case data. 