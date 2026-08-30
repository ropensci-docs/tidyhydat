# Convenience function to plot realtime data

This is an easy way to visualize a single station using base R graphics.
More complicated plotting needs should consider using `ggplot2`.
Inputting more 5 stations will result in very busy plots and longer load
time. Legend position will sometimes overlap plotted points.

## Usage

``` r
realtime_plot(station_number = NULL, Parameter = c("Flow", "Level"))
```

## Arguments

- station_number:

  A seven digit Water Survey of Canada station number. Can only be one
  value.

- Parameter:

  Parameter of interest. Either "Flow" or "Level". Defaults to "Flow".

## Value

A plot of recent realtime values

## Examples

``` r
if (FALSE) { # \dontrun{
## One station
realtime_plot("08MF005")

## Multiple stations
realtime_plot(c("07EC002", "01AD003"))
} # }
```
