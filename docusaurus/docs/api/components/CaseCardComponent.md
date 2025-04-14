---
sidebar_position: 6 # Adjust position relative to other components
title: CaseCardComponent
---

# CaseCardComponent

(*Path likely `src/components/caseCardComponent.js` or similar*)

This component serves as the primary interface for viewing and interacting with data attributes, displaying their values for the currently selected case(s) and providing access to attribute configuration.

## Overview

The `CaseCardComponent` typically resides in a side panel (e.g., the right margin) and displays a list of all attributes available in the dataset.

-   **Functionality:** Renders an interactive list/table of attributes.
    -   For each attribute, it shows:
        -   Attribute Name.
        -   Attribute Value(s) corresponding to the currently selected case(s).
        -   Visual Color Mapping: A representation of the color(s) assigned to the attribute (e.g., distinct color swatches for categories, a gradient for numerical ranges).
        -   An Edit Icon/Button to access configuration options.
-   **Data Context:** While listing all attributes, the *values* displayed are specific to the case(s) selected in other components like [`PlotView`](../dynplot/PlotView.md) or [`CaseTableComponent`](./CaseTableComponent.md).
-   **Attribute Editing:** Clicking the edit icon opens controls (likely in another component or modal) allowing users to modify properties of that specific [`Attribute`](../dynDataset/Attribute.md).

## Attribute Display Details

-   **Layout:** Presents attributes vertically, showing name, value, and color representation side-by-side.
-   **Categorical Attributes:** Displays distinct color swatches next to the attribute name or value, representing the colors assigned to each category.
-   **Numerical Attributes:** Shows a single color swatch or a gradient representing the color range used for that attribute's numerical scale.
-   **Selected Case Value:** Displays the value of the attribute for the currently selected case. Handles single and potentially multiple selections (e.g., showing "Multiple Values" if selected cases differ).

## Attribute Editing Features (Accessed via Edit Icon)

-   **Common:**
    -   Edit Attribute Name.
    -   Edit Attribute Description.
-   **Categorical Specific:**
    -   Modify colors assigned to individual categories (e.g., change 'Male' color, 'Female' color for Gender).
-   **Numerical Specific:**
    -   Modify the single color or gradient used.
    -   Update/set the range (min/max) for filtering or color mapping.
    -   Adjust formatting (e.g., decimal places, rounding).
    -   Potentially change the data type (needs confirmation based on implementation).

## Usage

-   Acts as the central hub for viewing attribute details and initiating attribute configuration.
-   Responds to case selections made elsewhere in the application.
-   Provides the entry point for detailed attribute customization.

## Dependencies

-   Requires access to the full list of **[`Attribute`](../dynDataset/Attribute.md)** objects (metadata, configuration).
-   Needs the data for the currently **selected case(s)** (from `Dyn.selectedCases` or similar state).
-   Interacts with application state (`Dyn`) to get selections and potentially trigger attribute updates.
-   Launches or controls **Attribute Editing** components/modals.
-   Receives selection updates from **[`PlotView`](../dynplot/PlotView.md)** and **[`CaseTableComponent`](./CaseTableComponent.md)**.

```jsx
// Inside TuvaDataTools.jsx render method (simplified):

render() {
  // ... other setup ...

  return (
    <div className="tuva-data-tool">
      {/* ... ToolbarComponent ... */}
      <SplitPane /* ... options ... */ >
        <div> {/* Top Pane: Plot View / ElemPlay */} </div>
        <div> {/* Bottom Pane */} 
          <CaseCardComponent
            Dyn={this.Dyn}
            mode={this.props.mode}
            language={this.props.language}
            // dataType might be passed conditionally
          />
          {/* ... CaseTable / SummaryView / SampleStats ... */}
        </div>
      </SplitPane>
    </div>
  );
}
```

## Props

| Prop       | Type     | Default     | Description                                                                                           |
|------------|----------|-------------|-------------------------------------------------------------------------------------------------------|
| `Dyn`      | `object` | `undefined` | The core internal `Dyn` object containing the dataset, plot state, and utilities. Required.           |
| `dataType` | `string` | `undefined` | (Optional) If provided, filters the attributes displayed in the list view to only this data type. |
| `mode`     | `string` | `"explore"` | The operational mode (e.g., "explore", "edit", "jr"), passed down to child components.             |
| `language` | `string` | `"en"`      | The current language code, passed down to child components for localization.                        |

## State Management

Key internal state includes:

-   `activeCard`: A string (from the internal `CARDS` enum) indicating which view is currently displayed.
-   `editingAttribute`: Stores the attribute object being configured when the `ATTRIBUTE_EDIT` view is active. See [`Attribute`](../dynDataset/Attribute.md).
-   `recordIndex`: The index of the currently selected data case, used to display relevant values in the attribute list.
-   `attribs`: An array of attribute information derived from `Dyn.dataSet` for display.
-   `onAxisAttribIds`, `filteredAttribIds`, `onLegendAttribIDs`: Track attribute usage/status for styling the list.

## Key Methods

-   `openCard(cardName)`: Switches the view to the specified card.
-   `addOrEditAttribute(attribute)`: Opens the Add or Edit view, optionally pre-filling with an existing attribute.
-   `save()`: Returns an object representing the current state (active card, editing attribute ID) for serialization (e.g., saving plot state).
-   `restore(savedState)`: Restores the component's view based on a previously saved state object.

## Interaction with `Dyn`

-   **Reads Data:** Populates its attribute list (`attribs` state) by processing data from `Dyn.dataSet`. See [`DataSet`](../dynDataset/DataSet.md).
-   **Listens to Events:** Subscribes to mediator events from `Dyn` to stay synchronized with changes happening elsewhere, such as:
    -   Case selections (`setCasesSelected`).
    -   Attributes being added/removed from plot axes (`setAddedAttribute`, `setRemovedAttribute`).
    -   Data filtering (`setCasesFiltered`).
    -   Attribute metadata changes (`setAttributeMetadata`).

## Usage Example

The `<CaseCardComponent />` is typically rendered within the [`<TuvaDataTools />`](../containers/TuvaDataTools.md) container.

```jsx
// Inside TuvaDataTools.jsx render method (simplified):

render() {
  // ... other setup ...

  return (
    <div className="tuva-data-tool">
      {/* ... ToolbarComponent ... */}
      <SplitPane /* ... options ... */ >
        <div> {/* Top Pane: Plot View / ElemPlay */} </div>
        <div> {/* Bottom Pane */} 
          <CaseCardComponent
            Dyn={this.Dyn}
            mode={this.props.mode}
            language={this.props.language}
            // dataType might be passed conditionally
          />
          {/* ... CaseTable / SummaryView / SampleStats ... */}
        </div>
      </SplitPane>
    </div>
  );
}
```

## Dependencies

-   Strongly dependent on the **`Dyn` object**.
-   Renders various child components for its different views (e.g., `AttributeListComponent`, `AttributeEditComponent`, `PlotSettingComponent`, etc.). (Links to be added when these are documented).
-   Uses `react-transition-group` for view animations. 