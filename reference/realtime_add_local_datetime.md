# Add local datetime column to realtime tibble

Adds `local_datetime` and `tz_used` columns based on either the most
common timezone in the original data or a user supplied timezone. This
function is meant to used in a pipe with the
[`realtime_dd()`](https://docs.ropensci.org/tidyhydat/reference/realtime_dd.md)
function.

## Usage

``` r
realtime_add_local_datetime(.data, set_tz = NULL)
```

## Arguments

- .data:

  Tibble created by `realtime_dd`

- set_tz:

  A timezone string in the format of
  [`OlsonNames()`](https://rdrr.io/r/base/timezones.html)

## Details

`Date` from `realtime_dd` is supplied in UTC which is the easiest format
to work with across timezones. This function does not change `Date` from
UTC. Rather `station_tz` specifies the local timezone name and is useful
in instances where `realtime_add_local_datetime` adjusts local_datetime
to a common timezone that is not the `station_tz`. This function is most
useful when all stations exist within the same timezone.

## Examples

``` r
if (FALSE) { # \dontrun{

realtime_dd(c("08MF005", "02LA004")) |>
  realtime_add_local_datetime()
} # }
```
