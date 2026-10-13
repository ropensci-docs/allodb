# Compute tree aboveground biomass (AGB) based on allometric equations

This function calculates the aboveground biomass (or other tree
components) of a given tree based on published allometric equations.
Users need to provide a table (i.e. dataframe) with DBH (cm), parsed
species Latin names, and site(s) coordinates. The biomass of all trees
in one (or several) censuses can be estimated using this function.

## Usage

``` r
get_biomass(
  dbh,
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

- dbh:

  a numeric vector containing tree diameter at breast height (dbh)
  measurements, in cm.

- genus:

  a character vector (same length as dbh), containing the genus (e.g.
  "Quercus") of each tree.

- coords:

  a numeric vector of length 2 with longitude and latitude (if all trees
  were measured in the same location) or a matrix with 2 numerical
  columns giving the coordinates of each tree.

- species:

  a character vector (same length as dbh), containing the species (e.g.
  "rubra") of each tree. Default is `NULL`, when no species
  identification is available.

- new_eqtable:

  Optional. An equation table created with the
  [`new_equations()`](https://docs.ropensci.org/allodb/reference/new_equations.md)
  function.

- wna:

  a numeric vector, this parameter is used in the
  [`weight_allom()`](https://docs.ropensci.org/allodb/reference/weight_allom.md)
  function to determine the dbh-related weight attributed to equations
  without a specified dbh range. Default is 0.1.

- w95:

  a numeric vector, this parameter is used in the
  [`weight_allom()`](https://docs.ropensci.org/allodb/reference/weight_allom.md)
  function to determine the value at which the sample-size-related
  weight reaches 95% of its maximum value (max=1). Default is 500.

- nres:

  number of resampled values. Default is "1e4".

## Value

A "numeric" vector of the same length as dbh, containing AGB value (in
kg) for every stem.

## Details

`allodb` estimates AGB by calibrating a new allometric equation for each
taxon (arguments `genus` and `species`) and location (argument `coords`)
in the user-provided census data. The new allometric equation is based
on a set of allometric equations that can be customized using the
`new_eqtable` argument. Each equation is then given a weight with the
[`weight_allom()`](https://docs.ropensci.org/allodb/reference/weight_allom.md)
function, based on: 1) its original sample size (numbers of trees used
to develop a given allometry), 2) its climatic similarity with the
target location, and 3) its taxonomic similarity with the target taxon
(see documentation of the
[`weight_allom()`](https://docs.ropensci.org/allodb/reference/weight_allom.md)
function). The final weight attributed to each equation is the product
of those three weights. Equations are then resampled with
the[`resample_agb()`](https://docs.ropensci.org/allodb/reference/resample_agb.md)
function: the number of samples per equation is proportional to its
weight, and the total number of samples is provided by the argument
`nres`. The resampling is done by drawing DBH values from a uniform
distribution on the DBH range of the equation, and estimating the AGB
with the equation. The couples of values (DBH, AGB) obtained are then
used in the function
[`est_params()`](https://docs.ropensci.org/allodb/reference/est_params.md)
to calibrate a new allometric equation, by applying a linear regression
to the log-transformed data. The parameters of the new allometric
equations are then used in the `get_biomass()` function by
back-transforming the AGB predictions based on the user-provided DBHs.

## Warning

The function can run into some memory problems when used on large
datasets (usually several hundred thousand observations).

## See also

[`weight_allom()`](https://docs.ropensci.org/allodb/reference/weight_allom.md),
[`new_equations()`](https://docs.ropensci.org/allodb/reference/new_equations.md)

## Examples

``` r
# Estimate biomass of all individuals from the Lauraceae family at the SCBI
# plot
lau <- subset(scbi_stem1, Family == "Lauraceae")
lau$agb <- get_biomass(lau$dbh, lau$genus, lau$species,
  coords = c(-78.2, 38.9)
)
lau
#> # A tibble: 1,209 × 7
#>    treeID stemID   dbh genus   species Family        agb
#>     <int>  <int> <dbl> <chr>   <chr>   <chr>       <dbl>
#>  1      2      2  2.37 Lindera benzoin Lauraceae  0.731 
#>  2      2  31195  1.07 Lindera benzoin Lauraceae  0.0989
#>  3      1  31194  1.6  Lindera benzoin Lauraceae  0.272 
#>  4     13  36481  1.34 Lindera benzoin Lauraceae  0.174 
#>  5     15  31208  1.27 Lindera benzoin Lauraceae  0.152 
#>  6     13     13  1.54 Lindera benzoin Lauraceae  0.247 
#>  7     13  31206  1.37 Lindera benzoin Lauraceae  0.184 
#>  8     15     15  1.55 Lindera benzoin Lauraceae  0.251 
#>  9     16  38297  1.1  Lindera benzoin Lauraceae  0.106 
#> 10     17     17  6.82 Lindera benzoin Lauraceae 10.4   
#> # ℹ 1,199 more rows

# Estimate biomass from multiple sites (using scbi_stem1 as example with
# multiple coord)
dat <- scbi_stem1[1:100, ]
dat$long <- c(rep(-78, 50), rep(-80, 50))
dat$lat <- c(rep(40, 50), rep(41, 50))
dat$biomass <- get_biomass(
  dbh = dat$dbh,
  genus = dat$genus,
  species = dat$species,
  coords = dat[, c("long", "lat")]
)
dat
#> # A tibble: 100 × 9
#>    treeID stemID   dbh genus species Family       long   lat biomass
#>     <int>  <int> <dbl> <chr> <chr>   <chr>       <dbl> <dbl>   <dbl>
#>  1   2695   2695  1.41 Acer  negundo Sapindaceae   -78    40  0.183 
#>  2   1229  38557  1.67 Acer  negundo Sapindaceae   -78    40  0.282 
#>  3   1230   1230  1.42 Acer  negundo Sapindaceae   -78    40  0.187 
#>  4   1295  32303  1.04 Acer  negundo Sapindaceae   -78    40  0.0842
#>  5   1229  32273  2.47 Acer  negundo Sapindaceae   -78    40  0.766 
#>  6     66  31258  2.19 Acer  negundo Sapindaceae   -78    40  0.564 
#>  7   2600   2600  1.81 Acer  negundo Sapindaceae   -78    40  0.347 
#>  8   4936   4936  1.35 Acer  negundo Sapindaceae   -78    40  0.164 
#>  9   1229  36996  2.05 Acer  negundo Sapindaceae   -78    40  0.476 
#> 10   1005   1005  1.41 Acer  negundo Sapindaceae   -78    40  0.183 
#> # ℹ 90 more rows
```
