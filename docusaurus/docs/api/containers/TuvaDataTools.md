---
sidebar_position: 1
title: TuvaDataTools
---

# TuvaDataTools Component

(*Path likely `src/containers/tuvaDataTools.js` or `src/index.js`*)

This is the top-level container component that encapsulates the entire Tuva Data Exploration widget. It orchestrates the main sub-components and manages the overall application state and data flow.

## Overview

`TuvaDataTools` acts as the primary wrapper when embedding the data exploration tools into a larger application. It initializes the core data structures and renders the main UI sections.

-   **Functionality:**
    -   **Initialization:** Creates and manages the core `Dyn` object (or equivalent state management structure), including initializing the [`DataSet`](../dynDataset/DataSet.md) with provided data.
    -   **Layout:** Renders the main structural layout of the tool, often using resizable panes (like `SplitPane`) to arrange the different views.
    -   **Component Orchestration:** Renders and passes necessary props (like the `Dyn` object or specific data/callbacks) to the major sub-components:
        -   [`ToolbarComponent`](../components/ToolbarComponent.md): For plot type selection, undo/redo, etc.
        -   [`PlotView`](../dynplot/PlotView.md): For the main data visualization area.
        -   [`CaseCardComponent`](../components/CaseCardComponent.md): For attribute listing, editing, and other panel views.
        -   [`CaseTableComponent`](../components/CaseTableComponent.md): For the tabular data view.
        -   [`SummaryView`](../components/SummaryView.md): For displaying summaries (potentially rendered conditionally or within `CaseCardComponent`).
        -   [`LegendComponent`](../components/LegendComponent.md): Displayed when a legend attribute is active.
    -   **State Management:** Serves as the root for application state, handling communication between components (often via the `Dyn` object acting as a mediator or state container).
-   **Embedding:** Designed to be embedded in other web pages or applications, receiving initial data and configuration via props.

## Key Props (Conceptual)

-   `initialData`: The raw dataset provided upon initialization.
-   `metadata`: Initial metadata for attributes.
-   `config`: Configuration options for the widget's behavior or appearance.
-   `language`: Language setting for UI text.
-   `mode`: Potential operating mode affecting available features.

## Core Internal State (Conceptual)

-   `Dyn`: The central object holding references to the `DataSet`, potentially the `mediator`, utility functions, and current application state (selected attributes, plot types, etc.).

## Rendering

-   Sets up the main container div.
-   Instantiates the `Dyn` object and `DataSet`.
-   Renders the `ToolbarComponent`.
-   Renders the main layout (e.g., `SplitPane`) containing:
    -   The `PlotView` (and related elements like `AxisView`).
    -   A panel containing the `CaseCardComponent`.
    -   Another panel potentially containing `CaseTableComponent` or `SummaryView`.
-   Conditionally renders `LegendComponent`.

## Usage

-   The primary component used by developers integrating the Tuva tools into their application.
-   Instantiated with initial data and configuration.

## Dependencies

-   Manages the central **`Dyn`** state object.
-   Initializes and holds the **[`DataSet`](../dynDataset/DataSet.md)**.
-   Renders and coordinates major UI and plotting components:
    -   **[`ToolbarComponent`](../components/ToolbarComponent.md)**
    -   **[`PlotView`](../dynplot/PlotView.md)**
    -   **[`CaseCardComponent`](../components/CaseCardComponent.md)**
    -   **[`CaseTableComponent`](../components/CaseTableComponent.md)**
    -   **[`SummaryView`](../components/SummaryView.md)**
    -   **[`LegendComponent`](../components/LegendComponent.md)**
-   May utilize layout components like `SplitPane`.

## Usage Example

```jsx
import React from 'react';
import TuvaDataTools from '@tuvalabs/data-exploration/src/containers/TuvaDataTools';

// Assuming data is loaded and structured appropriately
const columnNames = ['Case', 'AttributeA', 'AttributeB'];
const columnIds = ['id', 'attributea-attrib0', 'attributeb-attrib1'];
const rowData = [[1, 10, 'X'], [2, 20, 'Y'], [3, 15, 'X']];
const metaData = {
  fields: [
    { id: 'id', name: 'Case', type: 'numeric', ... },
    { id: 'attributea-attrib0', name: 'AttributeA', type: 'numeric', ... },
    { id: 'attributeb-attrib1', name: 'AttributeB', type: 'categorical', ... }
  ]
};

// Optional initial plot state or configuration
const initialPlotState = { /* ... plot configuration ... */ };
const config = { /* ... tool configuration ... */ };

function MyDataApp() {

  const handleUserAction = (action) => {
    console.log('User Action:', action);
    // Track user actions if needed
  };

  return (
    <TuvaDataTools
      columnNames={columnNames}
      columnIds={columnIds}
      rowData={rowData}
      metaData={metaData}
      initialPlotState={initialPlotState} // Optional
      config={config} // Optional
      onUserAction={handleUserAction} // Optional callback
      theme="light" // Optional: "light" or "dark"
      mode="explore" // Optional: e.g., "explore", "edit", "jr"
      language="en" // Optional: e.g., "en", "es", "fr"
    />
  );
}

export default MyDataApp;

```

## Props

| Prop               | Type       | Default        | Description                                                                                                                               |
|--------------------|------------|----------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `columnNames`      | `string[]` | `[]`           | An array of display names for each data column (including the initial "Case" column).                                                     |
| `columnIds`        | `string[]` | `[]`           | An array of unique IDs for each data column (including "id" for the Case column). Used internally to reference attributes.                |
| `rowData`          | `any[][]`  | `[]`           | A 2D array representing the dataset rows. Each inner array corresponds to a case, including the initial case number.                      |
| `metaData`         | `object`   | `{ fields: [] }` | An object describing the attributes. Primarily uses the `fields` array, where each object defines an attribute's `id`, `name`, `type`, etc. |
| `initialPlotState` | `object`   | `{}`           | An optional object defining the initial configuration of the plot (axes, plot type, displayed attributes, etc.).                         |
| `config`           | `object`   | `{}`           | An optional object for general tool configuration (e.g., feature flags, UI settings).                                                  |
| `onUserAction`     | `function` | `undefined`    | An optional callback function that is triggered on various user interactions within the tool. Receives an action descriptor object.      |
| `theme`            | `string`   | `"light"`      | Sets the visual theme ("light" or "dark").                                                                                              |
| `mode`             | `string`   | `"explore"`    | Sets the operational mode of the tool (e.g., "explore", "edit", "jr"). This can affect available features and UI elements.             |
| `language`         | `string`   | `"en"`         | Sets the display language. Requires corresponding locale data to be available.                                                         |

## Initialization & Data Handling

The component uses the `columnNames`, `columnIds`, `rowData`, and `metaData` props to initialize the internal dataset managed by the `Dyn` object. If `initialPlotState` is provided, it configures the plot accordingly; otherwise, it likely defaults to a standard initial view.

## Core Internal Object: `Dyn`

Much of the component's functionality relies on an internal `Dyn` object created via `initDyn()`. This object encapsulates:

-   **`Dyn.dataSet`**: Manages the loaded data, attributes, cases, filtering, and sampling. See [`DataSet`](../dynDataset/DataSet.md).
-   **`Dyn.plotView`**: Controls the rendering and interaction logic of the main plot area (using RaphaelJS). See [`PlotView`](../dynplot/PlotView.md).
-   **`Dyn.mediator`**: An event bus for communication between different parts of the tool.
-   Utility functions (`Dyn.dataUtil`, `Dyn.mathUtil`, `Dyn.colorUtil`, etc.).
-   State related to the plot configuration.

Understanding the structure and methods of the `Dyn` object (particularly `Dyn.dataSet` and `Dyn.plotView`) is key to understanding the tool's deeper mechanics, although direct interaction is often managed through the React components and the `onUserAction` callback.

## Layout

The UI is typically split vertically:

1.  **Top Section:** Contains the [`<ToolbarComponent />`](../components/ToolbarComponent.md) and the main plot view (`Dyn.plotView`).
2.  **Bottom Section:** A resizable panel (`react-split-pane`) containing the [`<CaseCardComponent />`](../components/CaseCardComponent.md) and one of the data views ([`<CaseTableComponent />`](../components/CaseTableComponent.md), [`<SummaryViewComponent />`](../components/SummaryViewComponent.md), or `SampleStatsComponent`).

## Interactivity

-   User actions in the [`<ToolbarComponent />`](../components/ToolbarComponent.md) trigger changes in the plot state or data.
-   Interactions with the plot view (e.g., selecting points, dragging) are handled by `Dyn.plotView` and often broadcast via the mediator.
-   Selections in the [`<CaseTableComponent />`](../components/CaseTableComponent.md) or [`<SummaryViewComponent />`](../components/SummaryViewComponent.md) can highlight corresponding elements in the plot, and vice-versa, coordinated via the mediator.
-   Keyboard shortcuts provide quick access to common actions. 