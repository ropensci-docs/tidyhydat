# Summarize available data by station

Returns a tibble with date ranges and record counts for each station,
broken down by approval status (final vs provisional).

## Usage

``` r
# S3 method for class 'available'
summary(object, ...)
```

## Arguments

- object:

  Object created by
  [`available_flows()`](https://docs.ropensci.org/tidyhydat/reference/available_flows.md)
  or
  [`available_levels()`](https://docs.ropensci.org/tidyhydat/reference/available_levels.md)

- ...:

  ignored

## Value

A tibble with columns:

- STATION_NUMBER

- final_start, final_end - date range for validated data

- provisional_start, provisional_end - date range for provisional data

- final_n, provisional_n - record counts

## Examples

``` r
if (FALSE) { # \dontrun{
flows <- available_flows(c("08MF005", "08MF010"))
summary(flows)
} # }
```
