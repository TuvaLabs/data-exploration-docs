---
sidebar_position: 3
title: CaseTableComponent
---

# `<CaseTableComponent />`

This component is responsible for rendering the main data grid within the [`<TuvaDataTools />`](../containers/TuvaDataTools.md) widget. It utilizes the `Handsontable` library to provide an interactive table display of the dataset.

## Overview

The `<CaseTableComponent />` displays cases (rows) and attributes (columns). Its key features include:

-   **Data Display:** Renders the dataset provided via the `Dyn` object.
-   **Two Modes:** Operates in:
    -   **View Mode (Read-Only):** Shows formatted data values. Column headers typically include the attribute name and a color key/legend. Data might be filtered based on selections elsewhere.
    -   **Edit Mode:** Allows direct editing of cell values. Usually displays raw, unformatted numbers. Adds blank rows and columns to facilitate data entry. Column headers are simplified (often just color keys), and attribute names are displayed in the first row of the table body.
-   **`Handsontable` Integration:** Leverages `Handsontable` for core grid features like scrolling, cell selection, rendering, and editing.
-   **Dynamic Configuration:** Adjusts `Handsontable` settings (columns, data, headers, read-only status) based on the current mode (`editingTable` state) and attribute properties (`getColumnFlags`).
-   **Interaction:** Listens to mediator events from `Dyn` to update its state (e.g., switch between view/edit mode, highlight selected rows) and potentially emits events based on table interactions.

## Props

| Prop             | Type       | Default     | Description                                                                                                         |
|------------------|------------|-------------|---------------------------------------------------------------------------------------------------------------------|
| `Dyn`            | `object`   | `undefined` | The core internal `Dyn` object containing the dataset, plot state, mediator, and utilities. Required.                |
| `isActive`       | `boolean`  | `undefined` | Indicates if the table view itself is the currently active bottom panel view. Affects updates.                     |
| `editable`       | `boolean`  | `false`     | Controls whether the table should be initialized in or allowed to switch to edit mode.                             |
| `onTableDataSave`| `function` | `undefined` | (Optional) Callback function triggered, likely when data is saved during edit mode (if save is handled internally). |
| `fullTableView`  | `boolean`  | `false`     | Controls whether the table should expand to take up more vertical space.                                         |
| `mode`           | `string`   | `"explore"` | The operational mode (e.g., "explore", "edit", "jr"), which can influence edit mode behavior.                   |
| `language`       | `string`   | `"en"`      | The current language code for localization (usage within this component might be limited).                          |

## State Management

Key internal state includes:

-   `editingTable`: Boolean, determines if the table is in view or edit mode.
-   `rows`: The array of data currently displayed in the table.
-   `columnAttributeNames`: Array of attribute names corresponding to table columns.
-   `columnHTMLHeaders`: Array of HTML strings used for `Handsontable` column headers.
-   `columns`: Array of configuration objects passed to `Handsontable` for each column (defining type, read-only status, formatting, etc.).
-   `isSampleMode`: Boolean, indicates if the table is displaying sampled data (edit mode is disabled in sample mode).

## Key Methods

-   `setBaseTable()`: Core method that reconstructs the table's data (`rows`) and configuration (`columns`, `columnHTMLHeaders`) based on the current `editingTable` state and the data in `Dyn.dataSet` (See [`DataSet`](../dynDataset/DataSet.md)).
-   `initEditMode()`: Initializes the edit mode based on the `editable` prop and dataset state.
-   `prepareEditMode()`: Sets initial cell focus when entering edit mode.
-   `getDirtyRawData()`: Returns the current data from the table when in edit mode (used for saving changes).
-   `setSelectedRowIds()`: Responds to mediator events to highlight rows corresponding to selected cases.

## Interaction and Data Flow

-   **Reads Data:** Fetches data primarily from `Dyn.dataSet` (See [`DataSet`](../dynDataset/DataSet.md)).
-   **Updates via Mediator:** Subscribes to events like `records:randomSamplesUpdated`, `elemPlayContainer:editModeOn`/`Off`, and `records:setCasesSelected` to update its internal state (mode, row highlighting).
-   **Updates Data (Edit Mode):** When edited, changes are held within the `Handsontable` instance. The `getDirtyRawData` method is likely used by a parent component or save mechanism to retrieve the modified data and update `Dyn.dataSet`.

## Usage Example

The `<CaseTableComponent />` is rendered conditionally within the bottom panel of the [`<TuvaDataTools />`](../containers/TuvaDataTools.md) container.

```jsx
// Inside TuvaDataTools.jsx render method (simplified):

renderBottomPanel() {
  switch (this.state.activeTableView) {
    case Constants.TABLE_VIEW:
      return (
        <CaseTableComponent
          Dyn={this.Dyn}
          isActive={true} // When this view is active
          editable={/*... based on config or mode ...*/}
          fullTableView={this.state.fullTableView}
          mode={this.props.mode}
          language={this.props.language}
          onTableDataSave={/*... handler ...*/}
        />
      );
    case Constants.SUMMARY_VIEW:
      return <SummaryViewComponent /* ...props... */ />;
    // ... other cases ...
    default:
      return null;
  }
}
```

## Dependencies

-   Critically dependent on the **`Dyn` object** for data access and event handling.
-   Relies heavily on the **`Handsontable`** library (via the `react-handsontable` wrapper) for the grid implementation. 