---
sidebar_position: 7 # Position after CaseSampler
title: MissingCaseManager
---

# MissingCaseManager Class

(*Path likely `src/lib/dynDataset/missingCaseManager.js` or similar*)

This helper class is likely responsible for managing information and potentially strategies related to handling missing values within the [`DataSet`](./DataSet.md).

## Overview

Missing data is a common issue. This class centralizes logic for identifying which cases have missing values for which attributes and potentially applying imputation or other handling strategies.

-   **Functionality:**
    -   **Identification:** May pre-process the dataset to identify and track the locations (case index, attribute ID) of missing values.
    -   **Information Provider:** Provides information about missingness (e.g., count per attribute, count per case), perhaps used by [`MissingValueComponent`](../components/MissingValueComponent.md).
    -   **Imputation (Optional):** Might contain logic to apply basic imputation methods (e.g., replacing missing numerical values with the mean or median) if configured.
    -   **Filtering:** Could provide functionality to filter *out* cases with missing values in specific attributes.
-   **Integration:** An instance is likely held and managed by the main [`DataSet`](./DataSet.md) class.

## Key Properties (Conceptual)

-   `missingInfo`: A data structure storing information about missing value locations or counts.
-   `imputationSettings`: Configuration for any automatic imputation methods.

## Key Methods (Conceptual)

-   `initialize(dataSet)`: Analyzes the dataset to identify missing values upon loading.
-   `getMissingCount(attributeId)`: Returns the number of missing values for a specific attribute.
-   `getMissingIndices(attributeId)`: Returns the indices of cases missing a value for a specific attribute.
-   `imputeMissingValues()`: Applies configured imputation methods (if any).
-   `getIndicesWithoutMissing(attributeIds)`: Returns indices of cases that have *no* missing values for the specified set of attributes.

## Usage

-   An instance is likely created and managed by **[`DataSet`](./DataSet.md)**.
-   Provides data used by **[`MissingValueComponent`](../components/MissingValueComponent.md)**.
-   Its methods might be called by `DataSet` during filtering or analysis steps to handle missing data appropriately (e.g., excluding cases with missing values before calculating statistics or running models).

## Dependencies

-   Managed by **[`DataSet`](./DataSet.md)**.
-   Operates on case data and **[`Attribute`](./Attribute.md)** information.
-   May involve statistical calculations (e.g., mean for imputation). 