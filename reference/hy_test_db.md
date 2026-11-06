# Get the location of the HYDAT database

The full HYDAT database needs to be downloaded from
[download_hydat](https://docs.ropensci.org/tidyhydat/reference/download_hydat.md),
but for testing purposes, a small test database is included in this
package. Use `hydat_path = hy_test_db()` in hy\_\* functions to
explicitly use the test database; use `hydat_path = hy_downloaded_db()`
to explicitly use the full, most recent downloaded database (this is
also the path returned by `hy_default_db()`).

## Usage

``` r
hy_test_db()

hy_downloaded_db()

hy_default_db()
```

## Value

The file location of a HYDAT database.

## See also

[hy_src](https://docs.ropensci.org/tidyhydat/reference/hy_src.md),
[hy_set_default_db](https://docs.ropensci.org/tidyhydat/reference/hy_set_default_db.md).

## Examples

``` r
if (FALSE) { # \dontrun{
hy_test_db()
hy_downloaded_db()
hy_default_db()
} # }
```
