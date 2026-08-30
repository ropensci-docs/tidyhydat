# Convenience function to pull station number from tidyhydat functions

This function mimics
[`dplyr::pull`](https://dplyr.tidyverse.org/reference/pull.html) to
avoid having to always type dplyr::pull(STATION_NUMBER). Instead we can
now take advantage of autocomplete. This can be used with `realtime_`
and `hy_` functions.

## Usage

``` r
pull_station_number(.data)
```

## Arguments

- .data:

  A table of data

## Value

A vector of station_numbers

## Examples

``` r
if (FALSE) { # \dontrun{

hy_stations(prov_terr_state_loc = "PE") |>
  pull_station_number() |>
  hy_annual_instant_peaks()
} # }
```
