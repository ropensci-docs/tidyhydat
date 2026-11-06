# Download a tibble of active realtime stations

An up to date dataframe of all stations in the Realtime Water Survey of
Canada hydrometric network operated by Environment and Climate Change
Canada

## Usage

``` r
realtime_stations(prov_terr_state_loc = NULL)
```

## Format

A tibble with 6 variables:

- **STATION_NUMBER**: Unique 7 digit Water Survey of Canada station
  number

- **STATION_NAME**: Official name for station identification

- **LATITUDE**: North-South Coordinates of the gauging station in
  decimal degrees

- **LONGITUDE**: East-West Coordinates of the gauging station in decimal
  degrees

- **PROV_TERR_STATE_LOC**: The province, territory or state in which the
  station is located

- **TIMEZONE**: Timezone of the station

## Arguments

- prov_terr_state_loc:

  Province, state or territory. If this argument is omitted, the value
  of `station_number` is returned. See
  `unique(allstations$prov_terr_state_loc)`. Will also accept `CA` to
  return only Canadian stations.

## See also

Other realtime functions:
[`realtime_dd()`](https://docs.ropensci.org/tidyhydat/reference/realtime_dd.md),
[`realtime_ws()`](https://docs.ropensci.org/tidyhydat/reference/realtime_ws.md)

## Examples

``` r
if (FALSE) { # \dontrun{
## Available inputs for prov_terr_state_loc argument:
unique(realtime_stations()$prov_terr_state_loc)

realtime_stations(prov_terr_state_loc = "BC")
realtime_stations(prov_terr_state_loc = c("QC", "PE"))
} # }
```
