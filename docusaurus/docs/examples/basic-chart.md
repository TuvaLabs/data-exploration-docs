---
sidebar_position: 1
---

# Basic Chart Example

This example demonstrates how to create a basic chart using the Data Exploration library.

## Code Example

```javascript
import { Chart } from '@tuvalabs/data-exploration';

function BasicChart() {
  const data = [
    { category: 'A', value: 10 },
    { category: 'B', value: 20 },
    { category: 'C', value: 30 },
    { category: 'D', value: 40 },
  ];

  return (
    <Chart
      type="bar"
      data={data}
      xField="category"
      yField="value"
      title="Basic Bar Chart"
    />
  );
}
```

## Explanation

Let's break down the key components of this example:

1. **Import**: We import the `Chart` component from the library
2. **Data**: We define our data as an array of objects
3. **Chart Component**: We use the `Chart` component with the following props:
   - `type`: Specifies the chart type (bar, line, pie, etc.)
   - `data`: The data to visualize
   - `xField`: The field to use for the x-axis
   - `yField`: The field to use for the y-axis
   - `title`: The chart title

## Result

This will render a bar chart showing the values for each category.

## Additional Options

You can customize the chart further with these options:

```javascript
<Chart
  type="bar"
  data={data}
  xField="category"
  yField="value"
  title="Basic Bar Chart"
  theme="dark"
  showLegend={true}
  animation={true}
  tooltip={{
    show: true,
    formatter: (datum) => `${datum.category}: ${datum.value}`
  }}
/>
```

## Related Examples

- [Interactive Chart](/docs/examples/interactive-chart)
- [Multiple Series](/docs/examples/multiple-series)
- [Custom Styling](/docs/examples/custom-styling) 