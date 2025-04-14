---
title: Understanding Sampling Distributions
sidebar_label: Sampling Distributions Guide
sidebar_position: 3 # Example position, adjust as needed relative to other guides/tutorials
---

# Guide: Understanding Sampling Distributions

This guide explains how to use the integrated feature to explore the concept of sampling distributions. This powerful tool helps visualize how statistics (like the mean or median) vary from sample to sample, which is a fundamental concept in statistical inference.

## What is a Sampling Distribution?

Imagine you have a large population (your full dataset) and you repeatedly draw random samples of a certain size (e.g., samples of 30 cases). For each sample, you calculate a specific statistic (e.g., the average 'Age'). If you did this thousands of times, the distribution of those calculated sample statistics (all the sample means) is called the **sampling distribution** of that statistic.

This tool automates that process, allowing you to see how sample statistics behave.

## Prerequisites

To use this feature, you need:

1.  A **Numerical Attribute:** You must have at least one numerical attribute selected or available in your dataset to calculate statistics on (e.g., 'Age', 'Height', 'Sales').
2.  (Implicit) Access to the sampling feature, likely via a button or menu associated with the [`CaseCardComponent`](../api/components/CaseCardComponent.md) or [`ToolbarComponent`](../api/components/ToolbarComponent.md).

## Workflow

Using the sampling distribution feature typically involves these steps:

1.  **Initiate Sampling:** Find the option to generate samples or explore sampling distributions (often labeled "Sample" or "Collect Samples").
2.  **Select Numerical Attribute:** Choose the numerical attribute from your dataset whose sampling distribution you want to explore.
3.  **Choose a Statistic:** Select the statistic you want to calculate for each sample. Common options include:
    *   Mean
    *   Median
    *   Standard Deviation (SD)
    *   Variance
    *   Interquartile Range (IQR)
4.  **Configure Sampling:**
    *   **Sample Size:** Specify how many cases should be in each random sample.
    *   **Number of Samples:** Specify how many times you want to draw a sample (e.g., 100, 1000). More samples give a clearer picture of the distribution.
5.  **Generate Samples:** Click the button to start the process. The application will now automatically:
    *   Draw the specified number of samples.
    *   Calculate the chosen statistic for each sample.
    *   Store these results.
    *   (Under the hood, this uses the logic described in [`CaseSampler`](../api/dynDataset/CaseSampler.md)).

## Exploring the Results: The Three Views

After generating the samples, the application typically presents the results in three distinct views, allowing you to explore different aspects:

1.  **Population View:**
    *   **What it shows:** A plot (often a histogram or dot plot) of the **original population data** for the numerical attribute you selected. This is rendered using the standard [`PlotView`](../api/dynplot/PlotView.md).
    *   **Purpose:** Shows the overall distribution of your full dataset, providing context for the samples.

2.  **Sample View:**
    *   **What it shows:** Allows you to look at the **individual samples** that were drawn. You can typically step through them one by one (e.g., Sample 1, Sample 2, ...).
    *   For each sample, you might see:
        *   A plot of the data points *within that specific sample*.
        *   The calculated statistic for *that specific sample* (e.g., the mean of Sample 1 was 45.2, the mean of Sample 2 was 43.8, etc.), possibly displayed in a [`SummaryView`](../api/components/SummaryView.md) or similar panel.
    *   **Purpose:** Helps understand the variability between individual samples and how each sample relates to the population.

3.  **Distribution of Sample Statistic View:**
    *   **What it shows:** This is the **sampling distribution** itself. It's a plot (usually a histogram or dot plot) where each data point represents the **calculated statistic** from one of your samples (e.g., one dot for each sample mean).
    *   **Purpose:** This is the core visualization. It shows the shape, center, and spread of the chosen sample statistic across many samples. You can see how the sample means (or medians, etc.) cluster and vary.

By switching between these views, you can gain a deep understanding of how sample statistics relate to the population parameter and how they vary due to random sampling.

# Sampling Distributions Guide

This guide provides an overview of the sampling distribution feature in the data-exploration tool, focusing on how to use the `CaseSampler` and related UI components. This documentation pertains to version `[INSERT COMMIT HASH OR TAG]` of the data-exploration codebase.

## Overview

The sampling distribution feature allows users to explore and visualize the distribution of sample statistics, such as means or proportions, from repeated random samples of a dataset. This is particularly useful for understanding the variability and behavior of sample statistics under different sampling conditions.

## Key Components

-   **`CaseSampler`:** The core component responsible for generating random samples from the dataset and calculating sample statistics.
-   **UI Components:** Various UI elements that allow users to configure sampling parameters, visualize results, and interact with the sampling process.

## Using the Sampling Distribution Feature

### Step 1: Accessing the Feature

To access the sampling distribution feature:

1.  Open the data-exploration tool.
2.  Navigate to the sampling distribution section via the toolbar or menu.

### Step 2: Configuring Sampling Parameters

-   **Sample Size:** Specify the number of cases to include in each sample.
-   **Number of Samples:** Define how many random samples to generate.
-   **Statistic of Interest:** Choose the statistic to calculate for each sample (e.g., mean, proportion).

### Step 3: Generating and Visualizing Samples

-   Click the "Generate Samples" button to create random samples based on the configured parameters.
-   The results are displayed in a visualization, typically a histogram or dot plot, showing the distribution of the sample statistic.

### Step 4: Interpreting Results

-   Analyze the distribution of the sample statistic to understand its variability and behavior.
-   Use the visualization to identify patterns, such as the shape of the distribution and the presence of outliers.

## Examples and Use Cases

-   **Understanding Central Limit Theorem:** Explore how the distribution of sample means approaches a normal distribution as the sample size increases.
-   **Comparing Sampling Methods:** Compare the results of different sampling methods (e.g., simple random sampling vs. stratified sampling).

## Dependencies

-   **`CaseSampler`:** Core functionality for generating samples and calculating statistics.
-   **UI Components:** Elements for configuring parameters and visualizing results.

## Version-Specific Details

-   **Version:** `[INSERT COMMIT HASH OR TAG]`
-   **Features:** This version includes support for simple random sampling and basic statistical calculations.
-   **Limitations:** Advanced sampling methods (e.g., stratified sampling) are not yet supported in this version.

## Next Steps

-   Explore advanced sampling methods and their implementation.
-   Enhance visualization options for more complex sampling scenarios. 