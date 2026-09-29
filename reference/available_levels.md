# Get all available level data (final + provisional)

Convenience function that combines final historical data (from HYDAT or
web service) with provisional real-time data in a single call.

## Usage

``` r
available_levels(
  station_number,
  start_date = NULL,
  end_date = Sys.Date(),
  hydat_path = NULL,
  prov_terr_state_loc = NULL
)
```

## Format

A tibble with 6 variables:

- **STATION_NUMBER**: Unique 7 digit Water Survey of Canada station
  number

- **Date**: Observation date. Formatted as a Date class.

- **Parameter**: Parameter being measured. Value is "Level"

- **Value**: Level value. The units are metres.

- **Symbol**: Measurement/river conditions

- **Approval**: Approval status: "final" (approved) or "provisional"
  (subject to revision)

## Arguments

- station_number:

  A seven digit Water Survey of Canada station number. If this argument
  is omitted, the value of `prov_terr_state_loc` is returned.

- start_date:

  Start date for data retrieval in YYYY-MM-DD format. Defaults to NULL
  (retrieves all available historical data).

- end_date:

  End date for data retrieval in YYYY-MM-DD format. Defaults to current
  date (Sys.Date()).

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

A tibble with class `available` combining final and provisional data
with an additional `Approval` column indicating whether each record is
"final" or "provisional". The object includes attributes for tracking
data sources and query metadata.

## Details

This function combines data from final and provisional data sources to
provide a complete water level record.

### Data Sources and Priority

**Historical (Final) Data:**

The function automatically determines the best source for historical
data:

- **`hydat_path` provided** (path to database): Uses local HYDAT
  database at that path

- **`hydat_path = FALSE`**: Forces use of web service (useful when HYDAT
  unavailable)

- **`hydat_path = NULL`** (default): Uses HYDAT default location,
  automatically falls back to web service if HYDAT is unavailable

**Real-time (Provisional) Data:**

Provisional data is retrieved from ECCC's real-time web service using
the
[`realtime_ws()`](https://docs.ropensci.org/tidyhydat/reference/realtime_ws.md)
function. This data covers approximately the last 18 months and is
updated regularly. Since real-time data is collected at sub-daily
intervals, values are aggregated to daily means to match the daily
format of HYDAT data. For non-aggregated real-time data, use
[`realtime_ws()`](https://docs.ropensci.org/tidyhydat/reference/realtime_ws.md)
directly.

### Data Approval Status

The `Approval` column uses ECCC's terminology (see
<https://wateroffice.ec.gc.ca/contactus/faq_e.html>):

- **"final"**: Historical data from HYDAT or web service that has been
  approved by ECCC.

- **"provisional"**: Real-time data from the web service representing
  the best available measurements, but subject to revision and not yet
  approved by ECCC.

## See also

Other available functions:
[`available_flows()`](https://docs.ropensci.org/tidyhydat/reference/available_flows.md)

## Examples

``` r
if (FALSE) { # \dontrun{
## Basic usage - get all available data
levels <- available_levels("08MF005")

## Multiple stations
levels <- available_levels(c("08MF005", "08NM116"))

## Get only recent data (last 2 years)
recent_levels <- available_levels(
  "08MF005",
  start_date = Sys.Date() - lubridate::years(2),
  end_date = Sys.Date()
)

## Force use of web service (when HYDAT not available)
levels_ws <- available_levels("08MF005", hydat_path = FALSE)
} # }
```
