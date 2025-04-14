---
sidebar_position: 6.1 # Position after CaseCardComponent
title: AttributeListComponent
---

# AttributeListComponent

(*Path likely `src/components/attributeListComponent.js` or similar*)

This component is a crucial sub-component of [`CaseCardComponent`](./CaseCardComponent.md). It is responsible for rendering the interactive list of all attributes in the dataset.

## Overview

`AttributeListComponent` displays each attribute along with its value for the currently selected case(s) and provides visual cues like color mappings.

-   **Functionality:** Iterates through the list of available [`Attribute`](../dynDataset/Attribute.md) objects and renders a row or item for each one.
-   **Row Content:** Each attribute row typically displays:
    -   The attribute name.
    -   The attribute value(s) for the currently selected case(s).
    -   A visual representation of the attribute's color mapping (swatches for categorical, gradient/single color for numerical).
    -   An icon or button to trigger attribute editing (likely handled by the parent `CaseCardComponent`).
-   **Interactivity:**
    -   May support drag-and-drop functionality to allow users to assign attributes to plot axes (interacting with [`PlotView`](../dynplot/PlotView.md) drop zones).
    -   Clicking the edit icon signals the parent [`CaseCardComponent`](./CaseCardComponent.md) to open the appropriate editing interface.
-   **Data Source:** Receives the list of all attributes and the data for the selected case(s) as props, likely passed down from [`CaseCardComponent`](./CaseCardComponent.md).

## Key Props (Conceptual)

-   `attributes`: An array or map of all available [`Attribute`](../dynDataset/Attribute.md) objects.
-   `selectedCases`: An array containing the data objects for the currently selected case(s).
-   `onEditAttribute`: A callback function (passed from `CaseCardComponent`) to handle requests to edit an attribute.
-   `onDragAttributeStart`: A callback function to handle the start of a drag operation for assigning attributes to axes.

## Rendering

-   Maps over the `attributes` prop.
-   For each attribute, renders a component (e.g., `AttributeListItem`) responsible for displaying the name, value (retrieved from `selectedCases`), color map, and edit button.
-   Implements drag-and-drop handlers if applicable.

## Usage

-   Rendered directly within [`CaseCardComponent`](./CaseCardComponent.md) as its primary view.
-   Provides the visual list that users interact with to understand attribute values and initiate configuration.

## Dependencies

-   Contained within **[`CaseCardComponent`](./CaseCardComponent.md)**.
-   Uses **[`Attribute`](../dynDataset/Attribute.md)** metadata and configuration.
-   Displays data from **selected cases**.
-   May interact with drag-and-drop libraries or browser APIs. 