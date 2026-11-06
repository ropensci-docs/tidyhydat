# Output OS-independent path to the HYDAT sqlite database

Provides the download location for
[download_hydat](https://docs.ropensci.org/tidyhydat/reference/download_hydat.md)
in an OS independent manner.

## Usage

``` r
hy_dir(...)
```

## Arguments

- ...:

  arguments potentially passed to
  [`rappdirs::user_data_dir`](https://rappdirs.r-lib.org/reference/user_data_dir.html)

## Examples

``` r
if (FALSE) { # \dontrun{
hy_dir()
} # }
```
