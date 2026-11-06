# Open a connection to the HYDAT database

This function gives low-level access to the underlying HYDAT database
used by other functions. Many of these tables are too large to load into
memory, so it is best to use dplyr to
[`dplyr::filter()`](https://dplyr.tidyverse.org/reference/filter.html)
them before using
[`dplyr::collect()`](https://dplyr.tidyverse.org/reference/compute.html)
to read them into memory.

## Usage

``` r
hy_src(hydat_path = NULL)

hy_src_disconnect(src)
```

## Arguments

- hydat_path:

  The path to the hydat database or NULL to use the default location
  used by
  [download_hydat](https://docs.ropensci.org/tidyhydat/reference/download_hydat.md).
  It is also possible to pass in an existing database connection from
  `hy_src()` such that the database only needs to be opened once per
  user-level call.

- src:

  A as returned by `hy_src()`.

## Value

A SQLite DBIConnection

## See also

[`download_hydat()`](https://docs.ropensci.org/tidyhydat/reference/download_hydat.md)

## Examples

``` r
if (FALSE) { # \dontrun{
library(dplyr)

# src is a src_sqlite
src <- hy_src(hydat_path = hy_test_db())
src_tbls(src)

# to get a table, use dplyr::tbl()
tbl(src, "STATIONS")

# one you're sure the results are what you want
# get a data.frame using collect()
tbl(src, "STATIONS") |>
  filter(PROV_TERR_STATE_LOC == "BC") |>
  collect()

# close the connection to the database
hy_src_disconnect(src)
} # }
```
