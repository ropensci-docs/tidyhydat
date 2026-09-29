# This function is deprecated in favour of generic plot methods

This is an easy way to visualize a single station using base R graphics.
More complicated plotting needs should consider using `ggplot2`.
Inputting more 5 stations will result in very busy plots and longer load
time. Legend position will sometimes overlap plotted points.

## Usage

``` r
hy_plot(
  station_number = NULL,
  Parameter = c("Flow", "Level", "Suscon", "Load")
)
```

## Arguments

- station_number:

  A (or several) seven digit Water Survey of Canada station number.

- Parameter:

  Parameter of interest. Either "Flow" or "Level".
