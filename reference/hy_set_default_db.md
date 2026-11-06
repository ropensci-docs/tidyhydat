# Set the default database path

For many reasons, it may be convenient to set the default database
location to somewhere other than the global default. Users may wish to
use a previously downloaded version of the database for reproducibility
purposes, store hydat somewhere other than hy_dir().

## Usage

``` r
hy_set_default_db(hydat_path = NULL)
```

## Arguments

- hydat_path:

  The path to the a HYDAT sqlite3 database file (e.g.,
  [hy_test_db](https://docs.ropensci.org/tidyhydat/reference/hy_test_db.md))

## Value

returns the previous value of
[hy_default_db](https://docs.ropensci.org/tidyhydat/reference/hy_test_db.md).

## Examples

``` r
if (FALSE) { # \dontrun{
# set default to the test database
hy_set_default_db(hy_test_db())

# get the default value
hy_default_db()

# set back to the default db location
hy_set_default_db(NULL)
} # }
```
