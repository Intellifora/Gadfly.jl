---
title: smooth
author: Daniel Jones
part: Geometry
order: 1010
...

Plot a smooth function estimated from data. An alias for `Geom.line` with `Stat.smooth`.

# Aesthetics

  * `x`: Predictor data.
  * `y`: Response data.
  * `color`: (optional) Group categorically by color.

# Arguments

  * `method`: `:loess` and `:lm` are supported.
  * `smoothing`: Method specific parameter controlling the degree of smoothing.
    For loess, this is the span parameter giving the proportion of data
    used for each local fit where 0.75 is the default. Smaller values use more
    data (less local context), larger values use less data (more local context).

# Examples

```{.julia hide="true" results="none"}
using RDatasets
using Gadfly

Gadfly.set_default_plot_size(16cm, 10cm)
```

```julia
x_data = 0.0:0.1:2.0
y_data = x_data.^2 + rand(length(x_data))
plot(x=x_data, y=y_data, Geom.point, Geom.smooth(method=:loess,smoothing=0.9))
```

```julia
plot(x=x_data, y=y_data, Geom.point, Geom.smooth(method=:loess,smoothing=0.2))
```
