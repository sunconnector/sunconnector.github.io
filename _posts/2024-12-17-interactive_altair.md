---
title:  "[ python ] interactive with altair"
excerpt: "interactive test"
categories:
    - polars
    - altair
toc : true
toc_sticky : true
author_profile: true
---

## # test interactive chart in github blog


```python
import polars as pl
import altair as alt
```

### # make DatraFrame
---


```python
df = pl.DataFrame( { 
    'a' : [ 1, 3 ,4 ], 
    'b' : [ 1, 3, 4 ],
    'c' : [ 3, 8, 4 ]
} )
```

### # Visualiztion with altair

<style>
  #altair-viz-3fa5d233d9814c4faa952aeec48a6901.vega-embed {
    width: 100%;
    display: flex;
  }

  #altair-viz-3fa5d233d9814c4faa952aeec48a6901.vega-embed details,
  #altair-viz-3fa5d233d9814c4faa952aeec48a6901.vega-embed details summary {
    position: relative;
  }
</style>
<div id="altair-viz-3fa5d233d9814c4faa952aeec48a6901"></div>
<script type="text/javascript">
  var VEGA_DEBUG = (typeof VEGA_DEBUG == "undefined") ? {} : VEGA_DEBUG;
  (function(spec, embedOpt){
    let outputDiv = document.currentScript.previousElementSibling;
    if (outputDiv.id !== "altair-viz-3fa5d233d9814c4faa952aeec48a6901") {
      outputDiv = document.getElementById("altair-viz-3fa5d233d9814c4faa952aeec48a6901");
    }

    const paths = {
      "vega": "https://cdn.jsdelivr.net/npm/vega@5?noext",
      "vega-lib": "https://cdn.jsdelivr.net/npm/vega-lib?noext",
      "vega-lite": "https://cdn.jsdelivr.net/npm/vega-lite@5.20.1?noext",
      "vega-embed": "https://cdn.jsdelivr.net/npm/vega-embed@6?noext",
    };

    function maybeLoadScript(lib, version) {
      var key = `${lib.replace("-", "")}_version`;
      return (VEGA_DEBUG[key] == version) ?
        Promise.resolve(paths[lib]) :
        new Promise(function(resolve, reject) {
          var s = document.createElement('script');
          document.getElementsByTagName("head")[0].appendChild(s);
          s.async = true;
          s.onload = () => {
            VEGA_DEBUG[key] = version;
            return resolve(paths[lib]);
          };
          s.onerror = () => reject(`Error loading script: ${paths[lib]}`);
          s.src = paths[lib];
        });
    }

    function showError(err) {
      outputDiv.innerHTML = `<div class="error" style="color:red;">${err}</div>`;
      throw err;
    }

    function displayChart(vegaEmbed) {
      vegaEmbed(outputDiv, spec, embedOpt)
        .catch(err => showError(`Javascript Error: ${err.message}<br>This usually means there's a typo in your chart specification. See the javascript console for the full traceback.`));
    }

    if(typeof define === "function" && define.amd) {
      requirejs.config({paths});
      let deps = ["vega-embed"];
      require(deps, displayChart, err => showError(`Error loading script: ${err.message}`));
    } else {
      maybeLoadScript("vega", "5")
        .then(() => maybeLoadScript("vega-lite", "5.20.1"))
        .then(() => maybeLoadScript("vega-embed", "6"))
        .catch(showError)
        .then(() => displayChart(vegaEmbed));
    }
  })({"config": {"view": {"continuousWidth": 300, "continuousHeight": 300, "stroke": null}, "axis": {"grid": false, "labelAngle": 0, "title": null}}, "vconcat": [{"mark": {"type": "circle"}, "encoding": {"size": {"aggregate": "sum", "field": "value", "legend": null, "type": "quantitative"}, "x": {"field": "key", "type": "nominal"}}, "name": "view_6", "transform": [{"fold": ["a", "b", "c"]}]}, {"mark": {"type": "bar"}, "encoding": {"x": {"field": "key", "type": "nominal"}, "y": {"aggregate": "sum", "field": "value", "type": "quantitative"}}, "transform": [{"fold": ["a", "b", "c"]}, {"filter": {"param": "param_6"}}]}], "data": {"name": "data-d2523f05b75addaf28cc3eb5b9d9104d"}, "params": [{"name": "param_6", "select": {"type": "point", "fields": ["key"]}, "views": ["view_6"]}], "$schema": "https://vega.github.io/schema/vega-lite/v5.20.1.json", "datasets": {"data-d2523f05b75addaf28cc3eb5b9d9104d": [{"a": 1, "b": 1, "c": 3}, {"a": 3, "b": 3, "c": 8}, {"a": 4, "b": 4, "c": 4}]}}, {"mode": "vega-lite"});
</script>


