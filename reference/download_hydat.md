# Download and set the path to HYDAT

Download the HYDAT sqlite database. This database contains all the
historical hydrometric data for Canada's integrated hydrometric network.
The function will check for a existing sqlite file and won't download
the file if the same version is already present.

## Usage

``` r
download_hydat(dl_hydat_here = NULL, ask = TRUE)
```

## Arguments

- dl_hydat_here:

  Directory to the HYDAT database. The path is chosen by the `rappdirs`
  package and is OS specific and can be view by
  [`hy_dir()`](https://docs.ropensci.org/tidyhydat/reference/hy_dir.md).
  This path is also supplied automatically to any function that uses the
  HYDAT database. A user specified path can be set though this is not
  the advised approach. It also downloads the database to a directory
  specified by
  [`hy_dir()`](https://docs.ropensci.org/tidyhydat/reference/hy_dir.md).

- ask:

  Whether to ask (as `TRUE`/`FALSE`) if HYDAT should be downloaded. If
  `FALSE` the keypress question is skipped.

## Examples

``` r
if (FALSE) { # \dontrun{
download_hydat()
} # }
```
