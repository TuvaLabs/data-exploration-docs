---
sidebar_position: 1
title: PlotView (Core Plotting Engine)
---

# `PlotView` Class

(`src/lib/dynplot/plotView.js`)

This class is the core engine responsible for rendering the main visualization area and managing user interactions within it. It does **not** use React but instead directly manipulates SVG elements using the **RaphaelJS** library.

## Role and Responsibilities

`PlotView` acts as the central orchestrator for the visual plot, connecting the underlying data model ([`Dyn.dataSet`](../dynDataset/DataSet.md)), plot configuration state, and the visual SVG output. Its primary responsibilities include:

-   **Canvas Initialization:** Sets up the RaphaelJS drawing surface (`this.paper`) within the designated HTML container.
-   **Sub-View Management:** Creates and coordinates helper view classes:
    -   `AxisView` (`this.xAxis`, `this.yAxis`, `this.y2Axis`): Manages the rendering and interaction logic for plot axes. (Not documented yet)
    -   `TopMarginView` (`this.topMargin`): Manages the area above the plot, typically for titles. (Not documented yet)
    -   `RightMarginView` (`this.rightMargin`): Manages the area to the right, often used for color legends. (Not documented yet)
-   **Plot Shaping (`PlotShaper`):** Utilizes a `PlotShaper` instance (`this.plotShaper`) to determine the type of plot and calculate the precise SVG coordinates (`this.casePositions`) for each data point based on assigned attributes and plot type. (Not documented yet)
-   **Rendering Case Icons:** Draws, positions, styles (color, shape, size), and updates the SVG elements (`this.icons`) that represent individual data cases (e.g., dots, bars) based on `this.casePositions`.
-   **Rendering Adornments (`PlotAdornments`):** Manages the rendering of non-case visual elements like statistical lines (mean, median), reference lines, regression lines, data counts/percentages, and annotations. These are typically controlled by specific [`PlotElement`](./plotElement/PlotElement.md) instances.
-   **Axis Interaction:** Handles dropping attributes onto axes (via `AxisView`) and updates the plot accordingly. Manages axis swapping.
-   **User Interaction:** Captures and processes user interactions directly on the plot canvas:
    -   Hover effects on cases.
    -   Marquee selection to select multiple cases.
    -   Dragging cases (if applicable for the plot type).
    -   Dragging map elements.
    -   Annotation drawing.
-   **State Synchronization:** Listens to mediator events from `Dyn.mediator` to react to changes in data, selections, filtering, settings, or plot configuration originating from other components (like [`ToolbarComponent`](../../components/ToolbarComponent.md) or [`CaseCardComponent`](../../components/CaseCardComponent.md)).
-   **Update Loop:** Triggers `updatePlotView()` to recalculate layout and re-render SVG elements when necessary.
-   **Undo/Redo:** Implements undo/redo functionality for plot-specific actions.
-   **Serialization:** Provides `save()` and `restore()` methods to capture and reapply the plot's visual state (attributes on axes, active elements, configuration).
-   **Animation:** Coordinates visual transitions using `PlotAnimator`.
-   **Sonification:** Includes logic for mapping data points to sounds.

## Core Properties (Conceptual)

-   `paper`: The RaphaelJS drawing surface object.
-   `plotShaper`: Instance of `PlotShaper`, calculates layout.
-   `casePositions`: Array of calculated coordinates and properties for each data point.
-   `icons`: Array of RaphaelJS SVG elements representing the data points.
-   `adornments`: Instance of `PlotAdornments`, manages non-case visuals (lines, stats).
-   `xAxis`, `yAxis`, `y2Axis`: Instances of `AxisView`.
-   `topMargin`, `rightMargin`: Instances of `TopMarginView`, `RightMarginView`.
-   `dataSet`: Reference to the [`Dyn.dataSet`](../dynDataset/DataSet.md) instance.
-   `plotAnimator`: Instance of `PlotAnimator`.

## Key Methods (Conceptual)

-   `init()`: Sets up the Raphael paper, sub-views, and event listeners.
-   `updatePlotView()`: The main method called to refresh the entire plot visualization based on current data and state.
-   `save()` / `restore()`: Handles saving and loading the plot's visual configuration.
-   `addPlot()` / `removePlot()` / `modifyTogglePlotElement()`: Core methods used (often triggered by the Toolbar) to change the active [`PlotElement`](./plotElement/PlotElement.md) instances controlling the visualization.
-   `dropAttribute()` / `removeAttribute()`: Manages adding/removing attributes from axes.
-   Interaction Handlers (e.g., `handleCasesSelected`, `handleAxisButtonClick`, `marqueeSelect`): Methods that respond to user actions or mediator events.

## Interaction with Other Classes

-   **[`Dyn.dataSet`](../dynDataset/DataSet.md)**: Reads data case values and attribute information.
-   **`Dyn.mediator`**: Subscribes to and publishes events for cross-component communication.
-   **`PlotShaper`**: Delegates layout calculations.
-   **`AxisView`, `TopMarginView`, `RightMarginView`**: Delegates rendering and interaction for specific UI regions.
-   **[`PlotElement` Subclasses](./plotElement/PlotElement.md)** (e.g., [`DotPlotElement`](./plotElement/DotPlotElement.md), [`MeanElement`](./plotElement/MeanElement.md), [`AnnotateElement`](./plotElement/AnnotateElement.md)): `PlotView` manages instances of these classes via `PlotShaper`. Each `PlotElement` controls the logic and rendering for a specific visual feature.

## Dependencies

-   Requires the **RaphaelJS** library for all SVG rendering.
-   Deeply integrated with the internal **`Dyn` object** and its sub-modules (`dataSet`, `mediator`, utilities).
-   Depends on various classes within the `dynplot` and `dynDataset` libraries (`PlotShaper`, `AxisView`, [`PlotElement`](./plotElement/PlotElement.md), etc.). 