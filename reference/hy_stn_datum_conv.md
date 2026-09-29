# Extract station datum conversions from HYDAT database

hy_stn_datum_conv look-up Table

## Usage

``` r
hy_stn_datum_conv(
  station_number = NULL,
  hydat_path = NULL,
  prov_terr_state_loc = NULL
)
```

## Format

A tibble with 4 variables:

- **STATION_NUMBER**: Unique 7 digit Water Survey of Canada station
  number

- **DATUM_FROM**: Identifying a datum from which water level is being
  converted

- **DATUM_TO**: Identifying a datum to which water level is being
  converted

- **CONVERSTION_FACTOR**: The conversion factor applied to water levels
  referred to one datum to obtain water levels referred to another datum

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

A tibble of hy_stn_datum_conv

## Examples

``` r
if (FALSE) { # \dontrun{
hy_stn_datum_conv(station_number = c("02JE013", "08MF005"))
} # }
```
