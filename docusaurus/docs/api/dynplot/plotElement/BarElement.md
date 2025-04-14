---
sidebar_position: 5
title: BarElement (Base for Bar Charts)
---

# `BarElement` Base Class

(`src/lib/dynplot/plotElement/barElement.js`)

This class extends the base [`PlotElement`](./PlotElement.md) and serves as the foundation for various types of Bar Charts. Unlike [`DotPlotBase`](./DotPlotBase.md) which positions individual case icons, `BarElement` focuses on representing aggregated data (frequencies, sums, means) for categories using rectangular bars.

## Role and Purpose

`BarElement` encapsulates the shared logic for:

-   **Determining Axis Roles:** Analyzing the attributes assigned to the X and Y axes to determine which axis represents categories and which represents the value (or frequency/percentage) determining bar length (`calcAxisOptions`).
-   **Bar Orientation:** Deciding whether bars should be drawn horizontally or vertically based on the axis configuration.
-   **Data Aggregation:** Calculating the necessary aggregate values (counts, sums, means) for each category using the internal `BarSums` helper class. This aggregation is essential for determining the length of each bar.
-   **Axis Configuration:** Setting appropriate ranges and types for the axes based on the calculated aggregates and the type of bar chart (`calcAxis`, `calcPlotSpecificRange`).
-   **Position Calculation (`calcPosition`):** Determining the position (x, y) and dimensions (width, height) of each bar (or segments within stacked/stretched bars). This involves mapping category positions and aggregate values to pixel coordinates.
-   **Handling Variations:** Providing flags and properties (`barsStacked`, `barsStretched`, `barsByFrequencyOnly`, etc.) that subclasses use to define their specific behavior (e.g., Frequency vs. Sum, Stacked vs. Grouped).

## Core Concepts

-   **Aggregation:** Bar lengths represent summaries (count, sum, mean) of data within categories, not individual data points.
-   **Axis Roles:** One axis is typically categorical (determining *which* bar), and the other is numerical/quantitative (determining bar *length*).
-   **Orientation:** Bars can be vertical or horizontal.
-   **Stacking/Stretching:** Supports variations where bars representing sub-categories (often from a legend attribute) are stacked within the main category bar, potentially normalized to 100% (stretched).

## Key Properties (Inherited/Set)

-   Inherits properties from [`PlotElement`](./PlotElement.md) (`dyn`, `plotShaper`, `primaryType`, `replaceType`, `priority`).
-   `barsStacked`, `barsStretched`, `barsByFrequencyOnly`, `multipleNumericAttributesOK`, `negativeCaseValuesOK`: Booleans set by subclasses to define the chart type.
-   `barsHorizontal`: `boolean` - Calculated property indicating bar orientation.
-   `onX`, `onY`, `onLegend`: `BarAxisOptions` - Objects holding flags about how each axis/legend is being used (Value, Frequency, Percent, Disabled).
-   `sums`: `BarSums` - Internal helper object holding calculated aggregate values.

## Key Methods (Implementations/Overrides)

-   `calcAxisOptions()`: Determines how axes are used (value, frequency, percent) and sets `onX`, `onY`, `onLegend` flags.
-   `calcAxis()`: Configures axis types (categorical, numeric) based on `calcAxisOptions`.
-   `calcPlotSpecificRange()`: Sets the range of the value/frequency/percent axis based on calculated aggregates in `sums`.
-   `calcPosition()`: Calculates the position and dimensions (x, y, width, height) for each bar or bar segment. This is a core method involving data aggregation and mapping to pixel coordinates.
-   `replaces()`: Subclasses override this to ensure only one main bar chart type is active.

## Subclassing

Concrete bar chart types extend `BarElement` and set specific flags in their constructors:

-   [`FreqBarElement`](./FreqBarElement.md): Sets `barsByFrequencyOnly = true`, `barsStacked = true`.
-   [`ValueBarElement`](./ValueBarElement.md): Represents raw values (less common).
-   [`BarOfSumsElement`](./BarOfSumsElement.md): Sets flags for summing a value attribute.
-   [`BarOfMeansElement`](./BarOfMeansElement.md): Sets flags for averaging a value attribute.
-   [`StretchedBarElement`](./StretchedBarElement.md): Sets `barsStacked = true`, `barsStretched = true`.

Subclasses rely on the base `BarElement` logic for most calculations but define their specific aggregation method and axis requirements.

## Helper Classes

-   `BarSums`: Calculates aggregates (counts, sums, means, min/max).
-   `BarAxisOptions`: Stores flags describing axis roles.
-   `BarSection`, `BarValue`, `BarData`, `BarStyle`: Likely internal helpers used within `calcPosition` for managing bar geometry and data.

## Dependencies

-   Extends **[`PlotElement`](./PlotElement.md)**.
-   Relies on **`AxisView`** instances to get axis types and scales.
-   Uses internal helper classes (**`BarSums`**, **`BarAxisOptions`**, etc.).
-   Interacts with **[`Dyn.dataSet`](../../dynDataset/DataSet.md)** to read data for aggregation. 