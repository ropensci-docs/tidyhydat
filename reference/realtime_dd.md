# Download a tibble of realtime river data from the last 30 days from the Meteorological Service of Canada datamart

Download realtime river data from the last 30 days from the
Meteorological Service of Canada (MSC) datamart. The function will
prioritize downloading data collected at the highest resolution. In
instances where data is not available at high (hourly or higher)
resolution daily averages are used. Currently, if a station does not
exist or is not found, no data is returned.

## Usage

``` r
realtime_dd(station_number = NULL, prov_terr_state_loc = NULL)
```

## Format

A tibble with 8 variables:

- **STATION_NUMBER**: Unique 7 digit Water Survey of Canada station
  number

- **PROV_TERR_STATE_LOC**: The province, territory or state in which the
  station is located

- **Date**: Observation date and time for last thirty days. Formatted as
  a POSIXct class in UTC for consistency.

- **Parameter**: Parameter being measured. Only possible values are Flow
  and Level

- **Value**: Value of the measurement. If Parameter equals Flow the
  units are m^3/s. If Parameter equals Level the units are metres.

- **Grade**: reserved for future use

- **Symbol**: reserved for future use

- **Code**: quality assurance/quality control flag for the discharge

- **station_tz**: Station timezone based on
  tidyhydat::allstations\$station_tz

## Arguments

- station_number:

  A seven digit Water Survey of Canada station number. If this argument
  is omitted, the value of `prov_terr_state_loc` is returned.

- prov_terr_state_loc:

  Province, state or territory. If this argument is omitted, the value
  of `station_number` is returned. See
  `unique(allstations$prov_terr_state_loc)`. Will also accept `CA` to
  return only Canadian stations.

## Value

A tibble of water flow and level values. The date and time of the query
(in UTC) is also stored as an attribute.

## See also

Other realtime functions:
[`realtime_stations()`](https://docs.ropensci.org/tidyhydat/reference/realtime_stations.md),
[`realtime_ws()`](https://docs.ropensci.org/tidyhydat/reference/realtime_ws.md)

## Examples

``` r
if (FALSE) { # \dontrun{
## Download from multiple provinces
realtime_dd(station_number = c("01CD005", "08MF005"))

## To download all stations in Prince Edward Island:
pei <- realtime_dd(prov_terr_state_loc = "PE")

## Access the time of query
attributes(pei)$query_time
} # }
```
