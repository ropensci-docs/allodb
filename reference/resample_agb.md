# Resample *allodb* equations to calibrate new allometries

After attributing a weight to each equation in *allodb* using the
[`weight_allom()`](https://docs.ropensci.org/allodb/reference/weight_allom.md)
function, equations are then resampled within their original DBH range
using `resample_agb()`: the number of resampled values for each equation
is proportional to its weight. It creates S3 objects of class "numeric".

## Usage

``` r
resample_agb(
  genus,
  coords,
  species = NULL,
  new_eqtable = NULL,
  wna = 0.1,
  w95 = 500,
  nres = 10000
)
```

## Arguments

- genus:

  a character value, containing the genus (e.g. "Quercus") of the tree.

- coords:

  a numeric vector of length 2 with longitude and latitude.

- species:

  a character value, containing the species (e.g. "rubra") of the tree.
  Default is "NULL", when no species identification is available.

- new_eqtable:

  Optional. An equation table created with the
  [`new_equations()`](https://docs.ropensci.org/allodb/reference/new_equations.md)
  function. Default is the original *allodb* equation table.

- wna:

  a numeric vector, this parameter is used in the
  [`weight_allom()`](https://docs.ropensci.org/allodb/reference/weight_allom.md)
  function to determine the dbh-related and sample-size related weights
  attributed to equations without a specified dbh range or sample size,
  respectively. Default is 0.1.

- w95:

  a numeric vector, this parameter is used in the
  [`weight_allom()`](https://docs.ropensci.org/allodb/reference/weight_allom.md)
  function to determine the value at which the sample-size-related
  weight reaches 95% of its maximum value (max=1). Default is 500.

- nres:

  number of resampled values. Default is "1e4".

## Value

An object of class "data.frame" of resampled DBHs and associated AGB
from the equation table; the number of resampled DBHs is proportional to
the weight provided by the
[`weight_allom()`](https://docs.ropensci.org/allodb/reference/weight_allom.md)
function.

## See also

[`weight_allom()`](https://docs.ropensci.org/allodb/reference/weight_allom.md),
[`new_equations()`](https://docs.ropensci.org/allodb/reference/new_equations.md).

## Examples

``` r
resample_agb(
  genus = "Quercus",
  species = "rubra",
  coords = c(-78.2, 38.9)
)
#> # A tibble: 9,973 × 3
#>    equation_id   dbh   agb
#>    <chr>       <dbl> <dbl>
#>  1 0cb0ce       23.2  249.
#>  2 0cb0ce       25.3  314.
#>  3 0cb0ce       23.3  251.
#>  4 0cb0ce       17.0  106.
#>  5 0cb0ce       17.9  122.
#>  6 0cb0ce       20.8  184.
#>  7 0cb0ce       18.0  124.
#>  8 0cb0ce       22.2  220.
#>  9 0cb0ce       19.8  162.
#> 10 0cb0ce       17.3  111.
#> # ℹ 9,963 more rows
```
