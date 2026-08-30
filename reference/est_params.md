# Calibrate new allometric equations

This function calibrates new allometric equations from sampling previous
ones. New allometric equations are calibrated for each species and
location by resampling the original compiled equations; equations with a
larger sample size, and/or higher taxonomic rank, and climatic
similarity with the species and location in question are given a higher
weight in this process.

## Usage

``` r
est_params(
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

  a character vector, containing the genus (e.g. "Quercus") of each
  tree.

- coords:

  a numeric vector of length 2 with longitude and latitude (if all trees
  were measured in the same location) or a matrix with 2 numerical
  columns giving the coordinates of each tree.

- species:

  a character vector (same length as genus), containing the species
  (e.g. "rubra") of each tree. Default is `NULL`, when no species
  identification is available.

- new_eqtable:

  Optional. An equation table created with the
  [`new_equations()`](https://docs.ropensci.org/allodb/reference/new_equations.md)
  function. Default is the compiled *allodb* equation table.

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

An object of class "data.frame" of fitted coefficients (columns) of the
non-linear least-square regression: \$\$AGB = a \* dbh ^ b + e, \space
\mathit{with} \space e ~ N(0, sigma^2)\$\$

## See also

[`weight_allom()`](https://docs.ropensci.org/allodb/reference/weight_allom.md),
[`new_equations()`](https://docs.ropensci.org/allodb/reference/new_equations.md).

## Examples

``` r
# calibrate new allometries for all Lauraceae species
lauraceae <- subset(scbi_stem1, Family == "Lauraceae")
est_params(
  genus = lauraceae$genus,
  species = lauraceae$species,
  coords = c(-78.2, 38.9)
)
#> # A tibble: 2 × 7
#>   genus     species  long   lat      a     b sigma
#>   <chr>     <chr>   <dbl> <dbl>  <dbl> <dbl> <dbl>
#> 1 Lindera   benzoin -78.2  38.9 0.0834  2.52  354.
#> 2 Sassafras albidum -78.2  38.9 0.0817  2.52  339.
```
