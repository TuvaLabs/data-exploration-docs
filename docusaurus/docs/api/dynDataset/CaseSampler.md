---
sidebar_position: 6 # Position after CaseFilter
title: CaseSampler
---

# CaseSampler Class

(*Path likely `src/lib/dynDataset/caseSampler.js` or similar*)

This helper class is responsible for the core logic of drawing multiple random samples from the dataset and calculating specified sample statistics for each sample. It underpins the application's feature for exploring sampling distributions.

## Overview

The `CaseSampler` is likely invoked when the user initiates the sampling distribution feature, typically requiring a numerical attribute and a chosen statistic. It performs the repetitive sampling and calculation process.

-   **Functionality:**
    -   Takes parameters: sample size, number of samples to draw, the target numerical attribute, and the statistic to calculate (e.g., Mean, Median, SD, Variance, IQR).
    -   Iteratively draws the specified number of random samples (with replacement) of the given size from the active cases of the target attribute.
    -   For each drawn sample, calculates the chosen statistic.
    -   Stores the results (potentially the samples themselves and definitely the calculated statistics for each sample).
-   **Prerequisites:** Requires a numerical [`Attribute`](./Attribute.md) to be selected for analysis.
-   **Integration:** An instance of `CaseSampler` might be held by the [`DataSet`](./DataSet.md) or instantiated temporarily when the feature is used.

## Key Properties (Conceptual)

-   `samples`: An array or structure potentially holding the drawn samples (or just their indices).
-   `calculatedStatistics`: An array storing the calculated statistic for each drawn sample (e.g., an array of sample means).
-   `configuration`: Stores the parameters used for the last run (sample size, num samples, attribute ID, statistic type).

## Key Methods (Conceptual)

-   `configure(settings)`: Sets the parameters (sample size, num samples, attribute, statistic).
-   `run(activeCaseData)`: Executes the sampling and calculation process using the provided active case data for the target attribute.
-   `getSamples()`: Returns the stored samples (if retained).
-   `getCalculatedStatistics()`: Returns the array of calculated statistics (this is key for the "Distribution of Sample Statistic" view).
-   `getSample(index)`: Returns data for a specific sample (used by the "Sample View").
-   `clearResults()`: Resets the stored samples and statistics.

## Usage

-   Instantiated or managed by **[`DataSet`](./DataSet.md)** or a dedicated controller for the sampling distribution feature.
-   Configuration options might be set via a UI component (similar to [`RandomSampleComponent`](../components/RandomSampleComponent.md) but more specialized for this feature).
-   The results (`calculatedStatistics`) are used to generate the "Distribution of Sample Statistic" plot within **[`PlotView`](../dynplot/PlotView.md)**.
-   Individual samples and their statistics might be displayed via a **`SummaryView`** component when browsing in the "Sample View".

## Dependencies

-   Works with data from **[`Attribute`](./Attribute.md)** and **[`DataSet`](./DataSet.md)** (specifically, the active cases for the target attribute).
-   Requires robust logic for random sampling (with replacement).
-   Requires implementations for calculating various **statistical measures** (Mean, Median, SD, etc.), potentially using `Dyn.mathUtil` or external libraries. 