---
sidebar_position: 2 # Position after Attribute
title: DataSet
---

# DataSet Class

(*Path likely `src/lib/dynDataset/dataSet.js` or similar*)

This class is the central hub for managing the entire dataset within the application. It holds the collection of all [`Attribute`](./Attribute.md) instances and the actual case data, providing an API for accessing and manipulating this data.

## Overview

The `DataSet` class is responsible for the overall state and structure of the data being explored.

-   **Data Holding:**
    -   Maintains the list/map of all [`Attribute`](./Attribute.md) objects.
    -   Stores the primary data table, often as an array of case objects or potentially columnar storage.
-   **Initialization:** Handles the loading and parsing of the initial dataset (e.g., from a file or API), creating the necessary [`Attribute`](./Attribute.md) instances and populating the case data.
-   **Attribute Management:** Provides methods for:
    -   Accessing individual `Attribute` objects (by ID or name).
    -   Adding new attributes (e.g., calculated attributes created via [`NewAttributeComponent`](../components/NewAttributeComponent.md)).
    -   Removing attributes (e.g., custom attributes deleted via [`DeleteAttributeComponent`](../components/DeleteAttributeComponent.md)).
    -   Modifying attribute properties (delegating changes to the `Attribute` instance but managing the overall update flow).
-   **Case Management:** Provides methods for:
    -   Accessing individual cases or subsets of cases.
    -   Potentially adding or removing cases (if supported).
-   **Filtering & Selection:** Manages the application of filters and maintains the set of currently selected cases. It likely provides methods to:
    -   Get the indices or data for currently active/filtered cases.
    -   Get the indices or data for currently selected cases.
    -   Update the selection state based on user interactions.
-   **Sampling:** Manages the application of data sampling (configured via [`RandomSampleComponent`](../components/RandomSampleComponent.md)), determining the active subset of cases.
-   **Notifications:** Emits events or uses callbacks to notify other parts of the application (like [`PlotView`](../dynplot/PlotView.md) or UI components) when data or attributes change.

## Key Properties (Conceptual)

-   `attributes`: A Map or Array storing all `Attribute` instances.
-   `cases`: An Array storing the raw data for all cases (e.g., array of objects).
-   `activeCaseIndices`: An array of indices representing the cases currently active after filtering and sampling.
-   `selectedCaseIndices`: An array of indices representing the currently selected cases.

## Key Methods (Conceptual)

-   `loadData(source)`: Loads data from a given source.
-   `getAttribute(id)`: Retrieves an `Attribute` by its ID.
-   `addAttribute(attributeDefinition)`: Adds a new attribute.
-   `removeAttribute(id)`: Removes an attribute.
-   `updateAttribute(id, changes)`: Updates properties of an attribute.
-   `getCases(indices)`: Retrieves case data for specified indices.
-   `getActiveCases()`: Retrieves data for currently active cases.
-   `getSelectedCases()`: Retrieves data for selected cases.
-   `setSelectedCases(indices)`: Updates the set of selected cases.
-   `applySample(settings)`: Applies sampling to determine `activeCaseIndices`.
-   `clearSample()`: Removes the sample filter.
-   `applyFilter(filterDefinition)`: Applies filters to determine `activeCaseIndices`.
-   `clearFilters()`: Removes filters.
-   `on(eventName, callback)`: Method to subscribe to data change notifications.

## Usage

-   A single `DataSet` instance likely exists within the main application state (`Dyn`).
-   Serves as the source of truth for data accessed by all visualization ([`PlotView`](../dynplot/PlotView.md), [`PlotElement`](../dynplot/plotElement/PlotElement.md)) and UI ([`CaseCardComponent`](../components/CaseCardComponent.md), [`CaseTableComponent`](../components/CaseTableComponent.md), etc.) components.
-   Coordinates data updates originating from user interactions or calculations.

## Dependencies

-   Manages a collection of **[`Attribute`](./Attribute.md)** instances.
-   May use helper utilities for data parsing, filtering, sampling, and statistical calculations (potentially within `Dyn.dataUtil`).
-   Provides data to essentially all other major components of the application. 