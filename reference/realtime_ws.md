# Download realtime data from the ECCC web service

Function to actually retrieve data from ECCC web service. The maximum
number of days that can be queried depends on other parameters being
requested. If one station is requested, 18 months of data can be
requested. If you continually receiving errors when invoking this
function, reduce the number of observations (via station_number,
parameters or dates) being requested.

## Usage

``` r
realtime_ws(
  station_number,
  parameters = NULL,
  start_date = Sys.Date() - lubridate::days(30),
  end_date = Sys.Date()
)
```

## Format

A tibble with 6 variables:

- **STATION_NUMBER**: Unique 7 digit Water Survey of Canada station
  number

- **Date**: Observation date and time. Formatted as a POSIXct class as
  UTC for consistency.

- **Name_En**: Code name in English

- **Value**: Value of the measurement.

- **Unit**: Value units

- **Grade**: future use

- **Symbol**: future use

- **Approval**: future use

- **Parameter**: Numeric parameter code

- **Code**: Letter parameter code

## Arguments

- station_number:

  Water Survey of Canada station number.

- parameters:

  parameter ID. Can take multiple entries. Parameter is a numeric code.
  See `param_id` for some options though undocumented parameters may be
  implemented. Defaults to Water level provisional, Secondary water
  level, Tertiary water level, Discharge Provisional, Discharge, sensor,
  Water temperature, Secondary water temperature, Accumulated
  precipitation

- start_date:

  Accepts either YYYY-MM-DD or YYYY-MM-DD HH:MM:SS. If only \`start
  date“ is supplied (i.e. YYYY-MM-DD) values are returned from the start
  of that day. Defaults to 30 days before current date. Time is supplied
  in UTC.

- end_date:

  Accepts either YYYY-MM-DD or YYYY-MM-DD HH:MM:SS. If only \`end_date“
  is supplied (i.e. YYYY-MM-DD) values are returned from the end of that
  day. Defaults to current date. Time is supplied in UTC.

## See also

Other realtime functions:
[`realtime_dd()`](https://docs.ropensci.org/tidyhydat/reference/realtime_dd.md),
[`realtime_stations()`](https://docs.ropensci.org/tidyhydat/reference/realtime_stations.md)

## Examples

``` r
if (FALSE) { # \dontrun{

ws_08 <- realtime_ws(
  station_number = c("08NL071", "08NM174"),
  parameters = c(47, 5)
)

fivedays <- realtime_ws(
  station_number = c("08NL071", "08NM174"),
  parameters = c(47, 5),
  end_date = Sys.Date(), # today
  start_date = Sys.Date() - lubridate::days(5) # five days ago
)
} # }
```
