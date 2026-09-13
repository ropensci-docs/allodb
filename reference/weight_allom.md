# Attribute weights to equations

This function attributes a weight to each equation based on its sampling
size, and taxonomic and climatic similarity with the species/site
combination considered.

## Usage

``` r
weight_allom(
  genus,
  coords,
  species = NULL,
  new_eqtable = NULL,
  wna = 0.1,
  w95 = 500
)
```

## Arguments

- genus:

  a character value, containing the genus (e.g. "Quercus") of the tree.

- coords:

  a numeric vector of length 2 with longitude and latitude.

- species:

  a character vector (same length as genus), containing the species
  (e.g. "rubra") of the tree. Default is `NULL`, when no species
  identification is available.

- new_eqtable:

  Optional. An equation table created with the
  [`new_equations()`](https://docs.ropensci.org/allodb/reference/new_equations.md)
  function.

- wna:

  a numeric vector, this parameter is used in the `weight_allom()`
  function to determine the sample-size related weights attributed to
  equations without a specified sample size. Default is 0.1.

- w95:

  a numeric vector, this parameter is used to determine the value at
  which the sample-size-related weight reaches 95% of its maximum value
  (max=1). Default is 500.

## Value

A named "numeric" vector with one weight for each equation.

## Details

Each equation is given a weight by the function `weight_allom()`,
calculated as the product of the following components:

\(1\) sample-size weight, calculated as:

\$\$1-exp(-n\*(log(20)/w95))\$\$

where n is the sample size of the equation; the weight given to
equations with no sample size information is determined by argument
`wna` (0.1 by default).

\(2\) climate weight, based on the similarity between the climatic
conditions of the equation site and the target location, using the
three-letter system of Koppen's climate scheme. Climate weights
associated with each combination of two Koppen climates are provided in
`data("koppenMatrix")`. The resulting weight has a value between 1e-6
(different climate groups) and 1 (exactly the same climate
classification). When an equation was calibrated with trees from several
locations with different Koppen climates, the maximum value out of all
pairwise equation-site climate weights is used.

\(3\) taxonomic weight: equal to 1 for same species equations, 0.8 for
same genus equations, 0.5 for same family equations and for equations
calibrated for the same broad functional or taxonomic group (e.g.
shrubs, conifers, angiosperms). All other equations are given a low
taxonomic weight of 1e-6: these equations will have a significant
relative weight in the final prediction only when no other more specific
equation is available.

## See also

[`get_biomass()`](https://docs.ropensci.org/allodb/reference/get_biomass.md),
[`new_equations()`](https://docs.ropensci.org/allodb/reference/new_equations.md).

## Examples

``` r
x <- weight_allom(
  genus = "Acer",
  species = "negundo",
  coords = c(-78.2, 38.9)
)
str(x)
#>  Named num [1:477] 6.13e-08 5.25e-08 1.00e-07 1.00e-07 1.00e-07 ...
#>  - attr(*, "names")= chr [1:477] "4b4063" "e2c7c7" "e42e41" "9f138f" ...
head(x)
#>       4b4063       e2c7c7       e42e41       9f138f       9e3b6a       e57b77 
#> 6.134069e-08 5.245305e-08 1.000000e-07 1.000000e-07 1.000000e-07 1.000000e-07 
```
