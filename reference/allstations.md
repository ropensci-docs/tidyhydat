# All Canadian stations

A shorthand to avoid having always call `hy_stations` or
`realtime_stations`. Populated by both realtime and historical data from
HYDAT.

## Usage

``` r
allstations
```

## Format

A tibble with 5 variables:

- **STATION_NUMBER**: Unique 7 digit Water Survey of Canada station
  number

- **STATION_NAME**: Official name for station identification

- **PROV_TERR_STATE_LOC**: The province, territory or state in which the
  station is located

- **HYD_STATUS**: Current status of discharge or level monitoring in the
  hydrometric network

- **REAL_TIME**: Logical. Indicates if a station has the capacity to
  deliver data in real-time or near real-time

- **LATITUDE**: North-South Coordinates of the gauging station in
  decimal degrees

- **LONGITUDE**: East-West Coordinates of the gauging station in decimal
  degrees

- **station_tz**: Timezone of station calculated using the lutz package
  based on LAT/LONG of stations

- **standard_offset**: Offset from UTC of local standard time

## Source

HYDAT, Meteorological Service of Canada datamart
