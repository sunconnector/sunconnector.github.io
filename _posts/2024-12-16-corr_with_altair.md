---
title:  "[ python ] heatmap with altair & polars"
excerpt: "뚝심있게 시각화는 altair로"
# classes : wide
categories:
    - polars
    - altair
toc : true
toc_sticky : true
#comments : true
---

```python
import polars as pl
import altair as alt
```

### # make DataFrame
---


```python
df = pl.DataFrame( { 
    'a' : [ 1, 3 ,4 ], 
    'b' : [ 1, 3, 4 ],
    'c' : [ 3, 8, 4 ]
} )
```

### # check corr
___


```python
df_c = df.corr().with_columns(
    pl.Series( df.columns ).alias( 'col' )
).unpivot( index = 'col' )
```

### # Visualiztion with altair

<style>
  #altair-viz-1e8e3cf225a04ad28dc2084629771656.vega-embed {
    width: 100%;
    display: flex;
  }

  #altair-viz-1e8e3cf225a04ad28dc2084629771656.vega-embed details,
  #altair-viz-1e8e3cf225a04ad28dc2084629771656.vega-embed details summary {
    position: relative;
  }
</style>
<div id="altair-viz-1e8e3cf225a04ad28dc2084629771656"></div>
<script type="text/javascript">
  var VEGA_DEBUG = (typeof VEGA_DEBUG == "undefined") ? {} : VEGA_DEBUG;
  (function(spec, embedOpt){
    let outputDiv = document.currentScript.previousElementSibling;
    if (outputDiv.id !== "altair-viz-1e8e3cf225a04ad28dc2084629771656") {
      outputDiv = document.getElementById("altair-viz-1e8e3cf225a04ad28dc2084629771656");
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
  })({"config": {"view": {"continuousWidth": 300, "continuousHeight": 300}, "axis": {"labelFontSize": 13}}, "layer": [{"mark": {"type": "rect"}, "encoding": {"color": {"field": "value", "type": "quantitative"}, "x": {"axis": {"labelAngle": 0}, "field": "col", "title": null, "type": "nominal"}, "y": {"field": "variable", "title": null, "type": "nominal"}}}, {"mark": {"type": "text"}, "encoding": {"color": {"condition": {"test": "(datum.value > 0.8)", "value": "white"}, "value": "gray"}, "text": {"field": "value", "format": ",.2%", "type": "quantitative"}, "x": {"axis": {"labelAngle": 0}, "field": "col", "title": null, "type": "nominal"}, "y": {"field": "variable", "title": null, "type": "nominal"}}}], "data": {"name": "data-2fb14dc0c9c76cea61193ac53700856c"}, "height": 300, "width": 300, "$schema": "https://vega.github.io/schema/vega-lite/v5.20.1.json", "datasets": {"data-2fb14dc0c9c76cea61193ac53700856c": [{"col": "a", "variable": "a", "value": 1.0}, {"col": "b", "variable": "a", "value": 1.0}, {"col": "c", "variable": "a", "value": 0.37115374447904514}, {"col": "a", "variable": "b", "value": 1.0}, {"col": "b", "variable": "b", "value": 1.0}, {"col": "c", "variable": "b", "value": 0.37115374447904514}, {"col": "a", "variable": "c", "value": 0.37115374447904514}, {"col": "b", "variable": "c", "value": 0.37115374447904514}, {"col": "c", "variable": "c", "value": 0.9999999999999998}]}}, {"mode": "vega-lite"});
</script>


