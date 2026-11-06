# A search function for hydrometric station name or number

Use this search function when you only know the partial station name or
want to search.

## Usage

``` r
search_stn_name(search_term, hydat_path = NULL)

search_stn_number(search_term, hydat_path = NULL)
```

## Arguments

- search_term:

  Only accepts one word.

- hydat_path:

  The path to the hydat database or NULL to use the default location
  used by
  [download_hydat](https://docs.ropensci.org/tidyhydat/reference/download_hydat.md).
  It is also possible to pass in an existing database connection from
  [`hy_src()`](https://docs.ropensci.org/tidyhydat/reference/hy_src.md)
  such that the database only needs to be opened once per user-level
  call.

## Value

A tibble of stations that match the `search_term`

## Examples

``` r
if (FALSE) { # \dontrun{
search_stn_name("Cowichan")

search_stn_number("08HF")
} # }
```
