# Extract instantaneous sediment sample information from the HYDAT database

Provides wrapper to turn the hy_sed_samples table in HYDAT into a tidy
data frame of instantaneous sediment sample information.
`station_number` and `prov_terr_state_loc` can both be supplied. If both
are omitted all values from the `hy_stations` table are returned. That
is a large vector for `hy_sed_samples`.

## Usage

``` r
hy_sed_samples(
  station_number = NULL,
  hydat_path = NULL,
  prov_terr_state_loc = NULL,
  start_date = NULL,
  end_date = NULL
)
```

## Format

A tibble with 19 variables:

- **STATION_NUMBER**: Unique 7 digit Water Survey of Canada station
  number

- **SED_DATA_TYPE**: Contains the type of sampling method used in
  collecting sediment for a station

- **Date**: Contains the time to the nearest minute of when the sample
  was taken

- **SAMPLE_REMARK_CODE**: Descriptive Sediment Sample Remark in English

- **TIME_SYMBOL**: An "E" symbol means the time is an estimate only

- **FLOW**: Contains the instantaneous discharge in cubic metres per
  second at the time the sample was taken

- **SYMBOL_EN**: Indicates a condition where the daily mean has a larger
  than expected error

- **SAMPLER_TYPE**: Contains the type of measurement device used to take
  the sample

- **SAMPLING_VERTICAL_LOCATION**: The location on the cross-section of
  the river at which the single sediment samples are collected. If one
  of the standard locations is not used the distance in meters will be
  shown

- **SAMPLING_VERTICAL_EN**: Indicates sample location relative to the
  regular measurement cross-section or the regular sampling site

- **TEMPERATURE**: Contains the instantaneous water temperature in
  Celsius at the time the sample was taken

- **CONCENTRATION_EN**: Contains the instantaneous concentration sampled
  in milligrams per litre

- **SV_DEPTH2**: Depth 2 for split vertical depth integrating (m)

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

- start_date:

  Leave blank if all dates are required. Date format needs to be in
  YYYY-MM-DD. Date is inclusive.

- end_date:

  Leave blank if all dates are required. Date format needs to be in
  YYYY-MM-DD. Date is inclusive.

## Value

A tibble of instantaneous sediment samples data

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
hy_sed_samples(station_number = "01CA004")
} # }
```
