# @observablehq/vega

**Note: This project is outdated. We recommend that you use https://github.com/vega/vega-embed instead**

Convenience methods for using [Vega](https://github.com/vega/vega) and [Vega-Lite](https://github.com/vega/vega-lite) in [Observable](https://observablehq.com). See this notebook for examples:

https://beta.observablehq.com/@mbostock/exploring-data-with-vega-lite

To load Vega-Lite:

```js
vegalite = require("@observablehq/vega-lite@0.1")
```

To display a happy little chart:

```js
vegalite({
  data: {
    values: [
      {a: "A", b: 28}, {a: "B", b: 55}, {a: "C", b: 43},
      {a: "D", b: 91}, {a: "E", b: 81}, {a: "F", b: 53},
      {a: "G", b: 19}, {a: "H", b: 87}, {a: "I", b: 52}
    ]
  },
  mark: "bar",
  encoding: {
    x: {field: "a", type: "ordinal"},
    y: {field: "b", type: "quantitative"}
  }
})
```

Or to load data with D3 and then display with Vega-Lite:

```js
d3 = require("d3-fetch@1")
```
```js
data = d3.csv("https://vega.github.io/vega-lite/data/seattle-weather.csv")
```
```js
vegalite({
  data: {values: data},
  mark: "tick",
  encoding: {
    x: {field: "precipitation", type: "quantitative"}
  }
})
```

You can pass all [Vega-Embed options](https://github.com/vega/vega-embed#options) as the second argument (besides the specification). For example, to change the renderer to SVG use:

```js
view = viewof vegalite(spec, {renderer: 'svg'})
```

To get the [Vega view object](https://vega.github.io/vega/docs/api/view/), you can use `viewof`:

```js
view = viewof vegalite(spec)
```
