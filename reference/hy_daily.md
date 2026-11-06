# Extract all daily water level and flow measurements

A thin wrapper around `hy_daily_flows` and \`hy_daily_levels“ that
returns a data frames that contains both parameters. All arguments are
passed directly to these functions.

## Usage

``` r
hy_daily(
  station_number = NULL,
  prov_terr_state_loc = NULL,
  hydat_path = NULL,
  ...
)
```

## Format

A tibble with 5 variables:

- **STATION_NUMBER**: Unique 7 digit Water Survey of Canada station
  number

- **Date**: Observation date. Formatted as a Date class.

- **Parameter**: Parameter being measured.

- **Value**: Discharge value. The units are m^3/s.

- **Symbol**: Measurement/river conditions

## Source

HYDAT

## Arguments

- station_number:

  A seven digit Water Survey of Canada station number. If this argument
  is omitted, the value of `prov_terr_state_loc` is returned.

- prov_terr_state_loc:

  Province, state or territory. If this argument is omitted, the value
  of `station_number` is returned. See
  `unique(allstations$prov_terr_state_loc)`. Will also accept `CA` to
  return only Canadian stations.

- hydat_path:

  The path to the hydat database or NULL to use the default location
  used by
  [download_hydat](https://docs.ropensci.org/tidyhydat/reference/download_hydat.md).
  It is also possible to pass in an existing database connection from
  [`hy_src()`](https://docs.ropensci.org/tidyhydat/reference/hy_src.md)
  such that the database only needs to be opened once per user-level
  call.

- ...:

  See
  [`hy_daily_flows()`](https://docs.ropensci.org/tidyhydat/reference/hy_daily_flows.md)
  arguments

## Value

A tibble of daily flows and levels

## See also

Other HYDAT functions:
[`hy_agency_list()`](https://docs.ropensci.org/tidyhydat/reference/hy_agency_list.md),
[`hy_annual_instant_peaks()`](https://docs.ropensci.org/tidyhydat/reference/hy_annual_instant_peaks.md),
[`hy_annual_stats()`](https://docs.ropensci.org/tidyhydat/reference/hy_annual_stats.md),
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
[`hy_stations()`](https://docs.ropensci.org/tidyhydat/reference/hy_stations.md),
[`hy_stn_data_coll()`](https://docs.ropensci.org/tidyhydat/reference/hy_stn_data_coll.md),
[`hy_stn_data_range()`](https://docs.ropensci.org/tidyhydat/reference/hy_stn_data_range.md),
[`hy_stn_op_schedule()`](https://docs.ropensci.org/tidyhydat/reference/hy_stn_op_schedule.md),
[`hy_stn_regulation()`](https://docs.ropensci.org/tidyhydat/reference/hy_stn_regulation.md),
[`hy_version()`](https://docs.ropensci.org/tidyhydat/reference/hy_version.md)

## Examples

``` r
if (FALSE) { # \dontrun{
hy_daily(station_number = c("02JE013", "08MF005"))
} # }
```
