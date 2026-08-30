# Calculate daily means from higher resolution realtime data

This function is meant to be used within a pipe as a means of easily
moving from higher resolution data to daily means.

## Usage

``` r
realtime_daily_mean(.data, na.rm = FALSE)
```

## Arguments

- .data:

  A data argument that is designed to take only the output of
  realtime_dd

- na.rm:

  a logical value indicating whether NA values should be stripped before
  the computation proceeds.

## Examples

``` r
if (FALSE) { # \dontrun{
realtime_dd("08MF005") |> realtime_daily_mean()
} # }
```
