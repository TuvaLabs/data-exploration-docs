---
sidebar_position: 4
title: SummaryViewComponent
---

# `<SummaryViewComponent />`

This component renders the "Summary View" panel within the [`<TuvaDataTools />`](../containers/TuvaDataTools.md) widget. Its purpose is to display calculated statistical measures and analysis derived from the current plot configuration in one or more dynamically generated HTML tables.

## Overview

The `<SummaryViewComponent />` listens for updates to the plot's statistical measures and performs the following:

-   Receives detailed measure data (likely via the `plot:measuresUpdated` mediator event from the `Dyn` object).
-   Analyzes this data using an internal helper class (`MeasureSetAnalysis`) to determine the optimal structure for presenting the information in tables. This includes deciding which data dimensions (attributes, categories, measure types) belong in table rows, columns, or titles.
-   Dynamically renders the HTML `<table>` structure based on the analysis and the received measure data.
-   Displays various statistical outputs, such as counts, percentages (cell, row, column), sums, means, medians, standard deviations, etc., depending on the plot configuration and measures added via the toolbar.
-   Handles user interactions like clicking or hovering over table cells/rows, often linking these interactions back to selections in the main plot view via the mediator.
-   Provides controls for adjusting the numeric precision of the displayed values.
-   Listens for selection events from other parts of the tool to highlight corresponding cells or rows in the summary table(s).

## Props

| Prop       | Type     | Default     | Description                                                                                           |
|------------|----------|-------------|-------------------------------------------------------------------------------------------------------|
| `Dyn`      | `object` | `undefined` | The core internal `Dyn` object containing the dataset, plot state, mediator, and utilities. Required. |
| `mode`     | `string` | `"explore"` | The operational mode (e.g., "explore", "edit", "jr"). (Likely passed down, usage may be limited).  |
| `language` | `string` | `"en"`      | The current language code for localization.                                                          |

## Data Source and Rendering

The component doesn't typically receive measure data directly via props. Instead, it subscribes to an internal event (likely `plot:measuresUpdated` on `Dyn.mediator`). When new measure data is available:

1.  The data is analyzed to determine table layout (rows, columns, headers).
2.  The component re-renders, dynamically building the necessary `<table>`, `<thead>`, `<tbody>`, `<tr>`, `<th>`, and `<td>` elements using React.
3.  The content of the cells is populated with the calculated measure values, formatted according to the current precision setting.

## Features

-   **Dynamic Table Structure:** The layout adapts based on the attributes on the plot axes, the presence of a legend attribute, and the specific statistical measures being displayed.
-   **Variety of Measures:** Can display counts, sums, percentages, means, medians, standard deviations, IQR, variance, and potentially results from statistical models.
-   **Linked Highlighting:** Selections made in the plot view or case table can highlight corresponding rows or cells in the summary view, and vice-versa.
-   **Precision Control:** Users can increase or decrease the number of decimal places shown for numeric values.
-   **Formula Display:** May use `MathQuilElement` or `Mathjax` to render mathematical formulas or symbols correctly within table cells or headers.

## Usage Example

The `<SummaryViewComponent />` is rendered conditionally within the bottom panel of the [`<TuvaDataTools />`](../containers/TuvaDataTools.md) container, typically when the user selects the "Summary" tab or view option.

```jsx
// Inside TuvaDataTools.jsx render method (simplified):

renderBottomPanel() {
  switch (this.state.activeTableView) {
    case Constants.SUMMARY_VIEW:
      return (
        <SummaryViewComponent
          Dyn={this.Dyn}
          mode={this.props.mode}
          language={this.props.language}
        />
      );
    case Constants.TABLE_VIEW:
      return <CaseTableComponent /* ...props... */ />;
    // ... other cases ...
    default:
      return null;
  }
}

render() {
  // ... other setup ...
  return (
    <div className="tuva-data-tool">
      {/* ... ToolbarComponent ... */}
      <SplitPane /* ... options ... */ >
        <div> {/* Top Pane */} </div>
        <div> {/* Bottom Pane */} 
          {/* ... CaseCardComponent ... */}
          {this.renderBottomPanel()}
        </div>
      </SplitPane>
    </div>
  );
}
```

## Dependencies

-   Critically dependent on the **`Dyn` object** for data (via mediator) and interaction logic.
-   May depend on `MathQuilElement` or `Mathjax` for rendering formulas.
-   Uses helper components like `<ToolTip />`. 