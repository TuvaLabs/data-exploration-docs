---
sidebar_position: 2
title: TuvaDataToolsFileUpload
---

# `<TuvaDataToolsFileUpload />`

This component provides a user-friendly interface for uploading local CSV files and visualizing them using the main [`<TuvaDataTools />`](./TuvaDataTools.md) component.

## Overview

`<TuvaDataToolsFileUpload />` acts as a wrapper around [`<TuvaDataTools />`](./TuvaDataTools.md). It handles:

1.  Displaying a drag-and-drop zone (`react-dropzone`) for CSV files.
2.  Reading the selected CSV file using `FileReader`.
3.  Parsing the CSV data using `papaparse`.
4.  Structuring the parsed data into the format expected by [`<TuvaDataTools />`](./TuvaDataTools.md) (adding a 'Case' column, generating column IDs, creating basic metadata).
5.  Rendering [`<TuvaDataTools />`](./TuvaDataTools.md) with the processed data once a file is successfully loaded.

## Usage

Typically, you would render this component directly without passing many props, as it manages the data loading process internally.

```jsx
import React from 'react';
import TuvaDataToolsFileUpload from '@tuvalabs/data-exploration/src/containers/TuvaDataToolsFileUpload';

function App() {
  return (
    <div>
      <h1>Upload and Explore Your Data</h1>
      <TuvaDataToolsFileUpload />
    </div>
  );
}

export default App;
```

## Data Processing

When a CSV file is dropped:

-   The first row is assumed to be the header row (attribute names).
-   A "Case" column is automatically added as the first column, containing sequential numbers for each data row.
-   Unique IDs are generated for each attribute based on a slugified version of the attribute name (e.g., "Student Name" might become `student-name-attrib0`).
-   Basic metadata is generated for each attribute.

## Rendering Logic

-   If no data has been loaded yet, it displays the drop zone prompting the user to upload a CSV.
-   Once a CSV is processed, it hides the drop zone and renders the [`<TuvaDataTools />`](./TuvaDataTools.md) component, passing the `columnNames`, `columnIds`, `rowData`, and `metaData` derived from the CSV as props.

## Props

This component generally doesn't require specific props for its core file upload functionality. Any props passed to it might be intended for the underlying [`<TuvaDataTools />`](./TuvaDataTools.md) component, but it's primarily designed to manage the upload flow itself.

*(Note: For detailed configuration and data options after the file is loaded, refer to the documentation for the [`<TuvaDataTools />`](./TuvaDataTools.md) component.)* 