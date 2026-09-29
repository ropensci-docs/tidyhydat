# Function to chose a station based on consistent arguments for hydat functions.

A function to avoid duplication in HYDAT functions. This function is not
intended for external use.

## Usage

``` r
station_choice(hydat_con, station_number, prov_terr_state_loc)
```

## Arguments

- hydat_con:

  A database connection

- station_number:

  A seven digit Water Survey of Canada station number. If this argument
  is omitted, the value of `prov_terr_state_loc` is returned.

- prov_terr_state_loc:

  Province, state or territory. If this argument is omitted, the value
  of `station_number` is returned. See
  `unique(allstations$prov_terr_state_loc)`. Will also accept `CA` to
  return only Canadian stations.
