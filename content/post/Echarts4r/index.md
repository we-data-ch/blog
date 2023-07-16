---
title: "Data Viz with Echarts4r"
author: "David Munoz Tord"
date: "2023-06-25"
categories: ["R"]
tags: ["dataviz", "interactive plots", "echarts4r"]
image: viz.png
---

<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r/echarts-en.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r/ecStat.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r/dataTool.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r-binding/echarts4r.js"></script>

By [David Munoz Tord](https://twitter.com/tord_munoz)

**Goal**: Learn about *data visualization* and familiarize yourself with some of the basic functions of the {[echarts4r](https://echarts4r.john-coene.com/index.html)}.

{[echarts4r](https://echarts4r.john-coene.com/index.html)} is back! And with version 4.5 the new features from version 5 of echarts.js are available now. Moreover, the morphing capabilities of echart.js have been ported to echarts4r as we will show in this post.

[Read more about it](https://echarts4r.john-coene.com/)

You can morph between plot like this:

``` r

library(echarts4r)

mtcars2 <- mtcars |> 
  head() |> 
  tibble::rownames_to_column("model")

e1 <- mtcars2 |> 
  e_charts(model) |> 
  e_bar(
    carb, 
    universalTransition = TRUE,
    animationDurationUpdate = 1000L
  )

e2 <- mtcars2 |> 
  e_charts(model) |> 
  e_pie(
    carb, 
    universalTransition = TRUE,
    animationDurationUpdate = 1000L
  )

cb <- "() => {
  let x = 0;
  setInterval(() => {
    x++
    chart.setOption(opts[x % 2], true);
  }, 3000);
}"
```

<br/>

``` r

e_morph(e1, e2, callback = cb)
## Warning in e_morph(e1, e2, callback = cb): This is experimental
```

<div class="figure">

<div class="echarts4r html-widget html-fill-item-overflow-hidden html-fill-item" id="htmlwidget-1" style="width:100%;height:500px;"></div>
<script type="application/json" data-for="htmlwidget-1">{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":[[{"yAxis":[{"show":true}],"xAxis":[{"data":["Mazda RX4","Mazda RX4 Wag","Datsun 710","Hornet 4 Drive","Hornet Sportabout","Valiant"],"type":"category","boundaryGap":true}],"legend":{"data":["carb"]},"series":[{"data":[{"value":["Mazda RX4","4"]},{"value":["Mazda RX4 Wag","4"]},{"value":["Datsun 710","1"]},{"value":["Hornet 4 Drive","1"]},{"value":["Hornet Sportabout","2"]},{"value":["Valiant","1"]}],"name":"carb","type":"bar","yAxisIndex":0,"xAxisIndex":0,"coordinateSystem":"cartesian2d","universalTransition":true,"animationDurationUpdate":1000}]},{"legend":{"data":["Mazda RX4","Mazda RX4 Wag","Datsun 710","Hornet 4 Drive","Hornet Sportabout","Valiant"]},"series":[{"name":"carb","type":"pie","universalTransition":true,"animationDurationUpdate":1000,"data":[{"value":4,"name":"Mazda RX4"},{"value":4,"name":"Mazda RX4 Wag"},{"value":1,"name":"Datsun 710"},{"value":1,"name":"Hornet 4 Drive"},{"value":2,"name":"Hornet Sportabout"},{"value":1,"name":"Valiant"}]}]}]],"dispose":true,"morphed":{"callback":"() => {\n  let x = 0;\n  setInterval(() => {\n    x++\n    chart.setOption(opts[x % 2], true);\n  }, 3000);\n}","default":0}},"evals":[],"jsHooks":[]}</script>
<p class="caption">
Figure 1: Morph between graphs.
</p>

</div>
