# Modify the original equation table

This function modifies the original equation table to be used in other
functions of the package including: subset the original equation table,
add new equations, and choose whether to include equations with a height
allometry.

## Usage

``` r
new_equations(
  subset_taxa = "all",
  subset_climate = "all",
  subset_region = "all",
  subset_ids = "all",
  subset_output = c("Total aboveground biomass", "Whole tree (above stump)"),
  new_taxa = NULL,
  new_allometry = NULL,
  new_coords = NULL,
  new_min_dbh = NULL,
  new_max_dbh = NULL,
  new_sample_size = NULL,
  new_unit_dbh = "cm",
  new_unit_output = "kg",
  new_input_var = "DBH",
  new_output_var = "Total aboveground biomass",
  use_height_allom = TRUE
)
```

## Arguments

- subset_taxa:

  character vector with taxa to be kept. Default is "all", in which case
  all taxa are kept.

- subset_climate:

  character vector with Koppen climate classification to be kept.
  Default is "all", in which case all climates are kept.

- subset_region:

  character vector with name of location(s) or country(ies) or broader
  region(s) (eg. "Europe", "North America") to be kept. Default is
  "all", in which case all regions/countries are kept.

- subset_ids:

  character vector with equation IDs to be kept. Default is "all", in
  which case all equations are kept.

- subset_output:

  What dependent variable(s) should be provided in the output? Default
  is "Total aboveground biomass" and "Whole tree (above stump)", other
  possible values are: "Bark biomass", "Branches (dead)", "Branches
  (live)", "Branches total (live, dead)", "Foliage total", "Height",
  "Leaves", "Stem (wood only)", "Stem biomass", "Stem biomass (with
  bark)", "Stem biomass (without bark)", "Whole tree (above and
  belowground)". Be aware that currently only a few equations represent
  those other variables, so estimated values might not be very accurate.

- new_taxa:

  character string or vector specifying the taxon (or taxa) for which
  the allometry has been calibrated.

- new_allometry:

  a character string with the allometric equation.

- new_coords:

  a vector or matrix of coordinates (longitude, latitude) of the
  calibration data.

- new_min_dbh:

  numerical value, minimum DBH for which the equation is valid (in cm).
  Default is `NULL` (nothing is added).

- new_max_dbh:

  numerical value, maximum DBH for which the equation is valid (in cm).
  Default is `NULL` (nothing is added).

- new_sample_size:

  number of measurements with which the allometry was calibrated.
  Default is `NULL` (nothing is added).

- new_unit_dbh:

  character string with unit of DBH in the equation (either `cm`, `mm`
  or `inch`). Default is "cm".

- new_unit_output:

  character string with unit of equation output (either "g", "kg", "Mg"
  or "lbs" if the output is a mass, or "m" if the output is a height).

- new_input_var:

  independent variable(s) needed in the allometry. Default is "DBH",
  other option is "DBH, H".

- new_output_var:

  dependent variable estimated by the allometry. Default is "Total
  aboveground biomass".

- use_height_allom:

  a logical value. In *allodb* we use Bohn et al. (2014) for European
  sites. User need to provide height allometry when needed to calculate
  AGB. Default is `TRUE`.

## Value

An object of class "data.frame" of new equations.

## Examples

``` r
new_equations(
  new_taxa = "Faga",
  new_allometry = "exp(-2+log(dbh)*2.5)",
  new_coords = c(-0.07, 46.11),
  new_min_dbh = 5,
  new_max_dbh = 50,
  new_sample_size = 50
)
#> # A tibble: 478 × 15
#>    equation_id equation_taxa           equation_allometry   independent_variable
#>    <chr>       <chr>                   <chr>                <chr>               
#>  1 726f1d      Larix laricina          10^(2.648+0.715*(lo… DBH                 
#>  2 a4d879      Acer saccharum          10^(1.2315+1.6376*(… DBH                 
#>  3 b9ebe4      Alnus rubra             exp(5.13118+2.15046… DBH                 
#>  4 5e2dea      Viburnum lantanoides    29.615*((1.488+1.19… DBH                 
#>  5 21800b      Pinus strobus           exp(5.2831+2.0369*l… DBH                 
#>  6 1257b1      Abies                   exp(3.1689+2.6825*l… DBH                 
#>  7 9e2124      Populus davidiana       10^(1.826+2.558*(lo… DBH                 
#>  8 74d0ce      Ostrya virginiana       exp(4.89+2.3*log(db… DBH                 
#>  9 94f593      Liriodendron tulipifera 10^(0.8306+1.527*(l… DBH                 
#> 10 8c94e8      Nyssa sylvatica         10^(1.1468+1.4806*(… DBH                 
#> # ℹ 468 more rows
#> # ℹ 11 more variables: dependent_variable <chr>, long <chr>, lat <chr>,
#> #   koppen <chr>, dbh_min_cm <dbl>, dbh_max_cm <dbl>, sample_size <dbl>,
#> #   dbh_units_original <chr>, dbh_unit_cf <dbl>, output_units_original <chr>,
#> #   output_units_cf <dbl>
```
