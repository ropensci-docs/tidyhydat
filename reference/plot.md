# Plot available data (final + provisional)

This method plots combined final and provisional data, visually
distinguishing between validated (final) and provisional records.

This method plots either daily time series data from HYDAT or realtime
data from the datamart. These plots are intended to be convenient and
quick methods to visualize hydrometric data.

## Usage

``` r
# S3 method for class 'available'
plot(x = NULL, ...)

# S3 method for class 'hy'
plot(x = NULL, ...)

# S3 method for class 'realtime'
plot(x = NULL, Parameter = c("Flow", "Level"), ...)
```

## Arguments

- x:

  Object created by either a hy_daily\_\* or realtime_dd data retrieval
  function

- ...:

  passed to `plot()`

- Parameter:

  Parameter of interest. Either "Flow" or "Level". Defaults to "Flow".

## Methods (by class)

- `plot(realtime)`: plot.realtime

## Examples

``` r
if (FALSE) { # \dontrun{
# One station
flows <- available_flows("08MF005")
plot(flows)
} # }

if (FALSE) { # \dontrun{
# One station
fraser <- hy_daily_flows("08MF005")
plot(fraser)
} # }

if (FALSE) { # \dontrun{
# One station
fraser_realtime <- realtime_dd("08MF005")
plot(fraser_realtime)
} # }
```
