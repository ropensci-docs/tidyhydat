# Extract station information from the HYDAT database

Provides wrapper to turn the hy_stations table in HYDAT into a tidy data
frame of station information. `station_number` and `prov_terr_state_loc`
can both be supplied. If both are omitted all values from the
`hy_stations` table are returned. This is the entry point for most
analyses is tidyhydat as establish the stations for consideration is
likely the first step in many instances.

## Usage

``` r
hy_stations(
  station_number = NULL,
  hydat_path = NULL,
  prov_terr_state_loc = NULL
)
```

## Format

A tibble with 15 variables:

- **STATION_NUMBER**: Unique 7 digit Water Survey of Canada station
  number

- **STATION_NAME**: Official name for station identification

- **PROV_TERR_STATE_LOC**: The province, territory or state in which the
  station is located

- **REGIONAL_OFFICE_ID**: The identifier of the regional office
  responsible for the station. Links to
  [hy_reg_office_list](https://docs.ropensci.org/tidyhydat/reference/hy_reg_office_list.md)

- **HYD_STATUS**: Current status of discharge or level monitoring in the
  hydrometric network

- **SED_STATUS**: Current status of sediment monitoring in the
  hydrometric network

- **LATITUDE**: North-South Coordinates of the gauging station in
  decimal degrees

- **LONGITUDE**: East-West Coordinates of the gauging station in decimal
  degrees

- **DRAINAGE_AREA_GROSS**: The total surface area that drains to the
  gauge site (km^2)

- **DRAINAGE_AREA_EFFECT**: The portion of the drainage basin that
  contributes runoff to the gauge site, calculated by subtracting any
  noncontributing portion from the gross drainage area (km^2)

- **RHBN**: Logical. Reference Hydrometric Basin Network station. The
  Reference Hydrometric Basin Network (RHBN) is a sub-set of the
  national network that has been identified for use in the detection,
  monitoring, and assessment of climate change.

- **REAL_TIME**: Logical. Indicates if a station has the capacity to
  deliver data in real-time or near real-time

- **CONTRIBUTOR_ID**: Unique ID of an agency that contributes data to
  the HYDAT database. The agency is non-WSC and non WSC funded

- **OPERATOR_ID**: Unique ID of an agency that operates a hydrometric
  station

- **DATUM_ID**: Unique ID for a datum

## Source

HYDAT

## Arguments

- station_number:

  A seven digit Water Survey of Canada station number. If this argument
  is omitted, the value of `prov_terr_state_loc` is returned.

- hydat_path:

  The path to the hydat database or NULL to use the default location
  used by
  [download_hydat](https://docs.ropensci.org/tidyhydat/reference/download_hydat.md).
  It is also possible to pass in an existing database connection from
  [`hy_src()`](https://docs.ropensci.org/tidyhydat/reference/hy_src.md)
  such that the database only needs to be opened once per user-level
  call.

- prov_terr_state_loc:

  Province, state or territory. If this argument is omitted, the value
  of `station_number` is returned. See
  `unique(allstations$prov_terr_state_loc)`. Will also accept `CA` to
  return only Canadian stations.

## Value

A tibble of stations and associated metadata

## See also

Other HYDAT functions:
[`hy_agency_list()`](https://docs.ropensci.org/tidyhydat/reference/hy_agency_list.md),
[`hy_annual_instant_peaks()`](https://docs.ropensci.org/tidyhydat/reference/hy_annual_instant_peaks.md),
[`hy_annual_stats()`](https://docs.ropensci.org/tidyhydat/reference/hy_annual_stats.md),
[`hy_daily()`](https://docs.ropensci.org/tidyhydat/reference/hy_daily.md),
[`hy_daily_flows()`](https://docs.ropensci.org/tidyhydat/reference/hy_daily_flows.md),
[`hy_daily_levels()`](https://docs.ropensci.org/tidyhydat/reference/hy_daily_levels.md),
[`hy_data_symbols`](https://docs.ropensci.org/tidyhydat/reference/hy_data_symbols.md),
[`hy_data_types`](https://docs.ropensci.org/tidyhydat/reference/hy_data_types.md),
[`hy_datum_list()`](https://docs.ropensci.org/tidyhydat/reference/hy_datum_list.md),
[`hy_monthly_flows()`](https://docs.ropensci.org/tidyhydat/reference/hy_monthly_flows.md),
[`hy_monthly_levels()`](https://docs.ropensci.org/tidyhydat/reference/hy_monthly_levels.md),
[`hy_reg_office_list()`](https://docs.ropensci.org/tidyhydat/reference/hy_reg_office_list.md),
[`hy_sed_daily_loads()`](https://docs.ropensci.org/tidyhydat/reference/hy_sed_daily_loads.md),
[`hy_sed_daily_suscon()`](https://docs.ropensci.org/tidyhydat/reference/hy_sed_daily_suscon.md),
[`hy_sed_monthly_loads()`](https://docs.ropensci.org/tidyhydat/reference/hy_sed_monthly_loads.md),
[`hy_sed_monthly_suscon()`](https://docs.ropensci.org/tidyhydat/reference/hy_sed_monthly_suscon.md),
[`hy_sed_samples()`](https://docs.ropensci.org/tidyhydat/reference/hy_sed_samples.md),
[`hy_sed_samples_psd()`](https://docs.ropensci.org/tidyhydat/reference/hy_sed_samples_psd.md),
[`hy_stn_data_coll()`](https://docs.ropensci.org/tidyhydat/reference/hy_stn_data_coll.md),
[`hy_stn_data_range()`](https://docs.ropensci.org/tidyhydat/reference/hy_stn_data_range.md),
[`hy_stn_op_schedule()`](https://docs.ropensci.org/tidyhydat/reference/hy_stn_op_schedule.md),
[`hy_stn_regulation()`](https://docs.ropensci.org/tidyhydat/reference/hy_stn_regulation.md),
[`hy_version()`](https://docs.ropensci.org/tidyhydat/reference/hy_version.md)

## Examples

``` r
if (FALSE) { # \dontrun{
## Multiple stations province not specified
hy_stations(station_number = c("08NM083", "08NE102"))

## Multiple province, station number not specified
hy_stations(prov_terr_state_loc = c("AB", "YT"))
} # }
```
