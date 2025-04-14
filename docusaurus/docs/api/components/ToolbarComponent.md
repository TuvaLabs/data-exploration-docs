---
sidebar_position: 1
title: ToolbarComponent
---

# `<ToolbarComponent />`

This component renders the main toolbar for the [`<TuvaDataTools />`](../containers/TuvaDataTools.md) widget. It serves as the primary control center, allowing users to select plot types, add statistical measures, manage annotations, change settings, perform data actions, and export the visualization.

## Overview

The `<ToolbarComponent />` utilizes a dynamic menu system to present available options to the user. Key responsibilities include:

-   Rendering menu bars and dropdowns based on configurations (likely defined in `ToolbarMenus.js`).
-   Translating user clicks on menu items into specific actions by mapping the item's value to predefined actions and parameters (using an internal `menuValueDict`).
-   Interacting heavily with the `Dyn` object to:
    -   Read the current plot state (e.g., active plot type, available measures) to enable/disable or check/uncheck menu items.
    -   Execute commands to modify the plot (e.g., `Dyn.plotView.addPlotElement()`, `Dyn.plotView.removePlotElement()`, `Dyn.plotView.togglePlotElement()`). See [`PlotView`](../dynplot/PlotView.md).
    -   Trigger data actions (e.g., `Dyn.dataSet.undo()`, `Dyn.dataSet.redo()`, `Dyn.dataSet.setCaseFilter()`). See [`DataSet`](../dynDataset/DataSet.md).
    -   Change settings (e.g., `Dyn.plotView.setColorScheme()`, `Dyn.plotView.setPrecision()`).
-   Handling UI aspects like tooltips, responsive collapsing of menus into a "More" group, and managing menu open/close state.
-   Providing functionality to export the plot view as a PNG image.

## Props

| Prop          | Type       | Default     | Description                                                                                                |
|---------------|------------|-------------|------------------------------------------------------------------------------------------------------------|
| `Dyn`         | `object`   | `undefined` | The core internal object containing the dataset (`Dyn.dataSet`), plot view (`Dyn.plotView`), state, and utilities. Required. |
| `isPlayViewOn`| `boolean`  | `false`     | Indicates if the alternative "Play" view (likely authoring mode) is active, which might affect toolbar options. |
| `mode`        | `string`   | `"explore"` | The operational mode (e.g., "explore", "edit", "jr"), which can influence available menu items.        |
| `language`    | `string`   | `"en"`      | The current language code, used for localization of menu item text via `Jed`.                              |

## Key Features & Menu Actions (Examples)

The toolbar provides access to a wide range of features, typically grouped into menus:

-   **Graph Type Menu:** Allows selection of the primary visualization type (e.g., [`DotPlotElement`](../dynplot/plotElement/DotPlotElement.md), [`LineGraphSingleElement`](../dynplot/plotElement/LineGraphSingleElement.md), [`FreqBarElement`](../dynplot/plotElement/FreqBarElement.md), Histogram, Box Plot, Pie Chart, Map).
-   **Measure Menu:** Enables adding/removing statistical overlays and measures (e.g., [`MeanElement`](../dynplot/plotElement/MeanElement.md), Median, Standard Deviation, IQR, Variance, Ref Lines, Least Squares Regression Line).
-   **Annotate Menu:** Provides tools for drawing on the plot (e.g., Pencil, Rectangle, Circle, Arrow, Text, Image) and clearing annotations. See `AnnotateElement`.
-   **Settings Menu:** Contains options to configure the appearance and behavior (e.g., Color Scheme, Animation On/Off, Font Size, Numeric Precision, Show/Hide Labels).
-   **Data Actions (Implicit/Contextual):** Undo, Redo actions become available based on the history stack managed by `Dyn.history`. Filtering options (`Exclude Selected`, `Keep Selected`) appear based on data selection state.
-   **Sampling Menu:** (If applicable) Controls for configuring and applying data sampling methods.
-   **Export/Help:** Saving the plot as a PNG image, accessing user guides or tutorials.

## Action Mapping

The component uses an internal mapping (`menuValueDict`) to link clicked menu item values (e.g., `'FreqHistogram'`) to specific methods and parameters used to interact with the `Dyn` object. For instance, clicking "Mean" might map to an action that calls `Dyn.plotView.addRemovePlotElement(Dyn.MeanElement, Dyn.EPlotControl.kControlsMean)`.

## Usage Example

The `<ToolbarComponent />` is designed to be rendered within the [`<TuvaDataTools />`](../containers/TuvaDataTools.md) container, which provides the necessary `Dyn` object and other props.

```jsx
// Inside TuvaDataTools.jsx render method (simplified):

render() {
  // ... other setup ...

  return (
    <div className="tuva-data-tool">
      <ToolbarComponent
        Dyn={this.Dyn}
        isPlayViewOn={this.state.isPlayViewOn}
        mode={this.props.mode}
        language={this.props.language}
      />
      {/* ... Plot View, Case Card, Bottom Panel ... */}
    </div>
  );
}
```

## Dependencies

-   Strongly dependent on the **`Dyn` object** for state information and action execution.
-   Relies on menu configuration objects (likely from `ToolbarMenus.js`).
-   Uses helper components like `<Menu />`, `<MenuItem />`, `<ToolTip />`. 