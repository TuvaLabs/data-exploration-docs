---
sidebar_position: 6.30 # Position nested under AttributeEditComponent
title: MissingValueComponent
---

# MissingValueComponent

(*Path likely `src/components/missingValueComponent.js` or similar*)

This is a sub-component rendered within [`AttributeEditComponent`](./AttributeEditComponent.md). It displays information about missing values (cases where the attribute has no value) and may provide functionality to select these cases.

## Overview

Understanding the prevalence of missing data is important for analysis. This component provides visibility into missing values for the attribute currently being edited.

-   **Functionality:**
    -   Calculates and displays the count or percentage of cases that have a missing value for this specific attribute.
    -   May provide an interactive element (e.g., a button or link like "Select Missing Cases") that triggers the selection of these specific cases in other views like the [`PlotView`](../dynplot/PlotView.md) or [`CaseTableComponent`](./CaseTableComponent.md).
-   **Data Source:** Needs access to the attribute's data or pre-calculated missing value statistics.

## Key Props (Conceptual)

-   `attribute`: The [`Attribute`](../dynDataset/Attribute.md) object being edited.
-   `missingValueCount` / `missingValuePercent`: The calculated count or percentage of missing values.
-   `onSelectMissingCases`: A callback function (potentially passed up from `AttributeEditComponent`) to trigger the selection logic in the main application state (`Dyn`).

## Rendering

-   Displays text indicating the number or percentage of missing values (e.g., "Missing: 15 cases (10%)").
-   Renders a button or link to trigger the selection of missing cases, attaching the `onSelectMissingCases` handler.

## Usage

-   Rendered within [`AttributeEditComponent`](./AttributeEditComponent.md), providing quick insight into data completeness for the attribute.
-   Allows users to easily isolate and examine cases with missing values for a specific attribute.

## Dependencies

-   Contained within **[`AttributeEditComponent`](./AttributeEditComponent.md)**.
-   Operates on data related to an **[`Attribute`](../dynDataset/Attribute.md)**.
-   Callback may interact with application state (`Dyn`) or directly with selection mechanisms in **[`PlotView`](../dynplot/PlotView.md)** / **[`CaseTableComponent`](./CaseTableComponent.md)**. 