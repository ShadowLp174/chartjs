# Pie Chart

## Quick Start

```
<div class="chart"></div>

<script>
var pieChart = new PieChart();
pieChart.render({});
pieChart.setData({
  series: [
    [30, "mid"], [1, "small"], [20, "mezzo-mid"], [5, "small"], [10, "mezzo-small"], [1, "small"], [100, "biggest"]
  ],
  options: {
    series: {
      tooltip: {
        format: "%name% (%value% %percentage%%)"
      }
    }
  }
}); // Some random values
</script>
```

## Documentation

### **new PieChart()**

* Creates a pie chart object

#### Methods

* [PieChart.render(opts)](#renderopts)
* [PieChart.setData(data)](#setDatadata)

##### **.render(opts)**

- Parameter: ```opts``` typeof [render options object](#render-options)
- Renders the Chart. Must be called before setting data

##### **.setData(data)**

- Parameter: ```data``` typeof [chart data](#chart-data)

#### Types

##### render options

* Type: `Object`
* Properties:
  - ```container``` type *String*/*HTMLElement*; specifies the container of the chart. Must be either a CSS Selector String or HTMLElement. Default: ```.chart```
  - ```width``` type *Number*; specifies the width of the chart in pixels; Default: ```600```
  - ```height``` type *Number*; specifies the height of the chart; Default: ```300```

##### Chart Data

* Type: `Object`
* Properties:
  - ```options``` typeof [chart options](#chart-options)
  - ```series``` typeof [chart series](#chart-series)

##### Chart Options

* Type: `Object`
* Properties:
  - ```style``` typeof [Style Object](#style-object)
  - ```series``` typeof `Object`
    - `drawCentres` typeof `boolean`; Default: `false`
    - `tooltip` typeof `Object`
     - `format` typeof [Format String](#format-string)
     - `type` typeof `String`; Default: `inline-auto`; (currently not working)

##### Chart Series

* Type: `Array`
* Format: ```[[point, name], [point, name], [point, name]]```
  - ```point``` typeof ```Number```
  - ```name``` typeof ```String```
* Example:

```
[
  [30, "middle"], [1, "smallest"], [20, "nearly-middle"], [5, "small"], [10, "nearly-small"], [1, "smallest"], [100, "biggest"]
]
```

##### Style Object

* Type: `Object`
* Description: Specifies style options of the chart
  - `backgroundColor` typeof `String`; Background Color of the chart
  - `uiColor` typeof `String`; Color of UI parts
  - `series` typeof `Object`
    - `colors` typeof `Array`; Array of colors that will be used to draw the pie chart parts
    - `color` typeof `String`; Possible values: `alternating; random`; Default: `alternating`
    - `highlighted` typeof `String`; Color of the part, that will be highlighted on hover
  - `tooltip` typeof `Object`
    - `background` typeof `Array`; The first value will be used as the background color for the tooltip
    - `color` typeof `String`; Color of the tooltip text

##### Format String

* Type: `String`
* Description: A String that specifies the content of the tooltip that shows up onHover
* Usage: The format String can contain any valid String characters but `%percentage%`, `%value%` and `%name%`. These will be replaced wih the current values.
* Example: `%name% (%value% %percentage%%)` - can resolve in: `biggest (100 59.9%)`
* Default: `%percentage%%`
