# Tables of allometric equations and associated metadata

- equations: Table of allometric equations.

- equations_metadata: Explanation of columns for equations table.

## Usage

``` r
equations

equations_metadata
```

## Format

An object of class `spec_tbl_df` (inherits from `tbl_df`, `tbl`,
`data.frame`) with 570 rows and 47 columns.

An object of class `spec_tbl_df` (inherits from `tbl_df`, `tbl`,
`data.frame`) with 47 rows and 7 columns.

## Source

See
[references](https://docs.ropensci.org/allodb/reference/references.md)
for equations original sources.

## Details

A compilation of best available allometry equations to calculate tree
above-ground biomass (AGB) per species based on extratropical ForestGEO
sites.

## See also

Other database datasets:
[`missing_values`](https://docs.ropensci.org/allodb/reference/missing_values.md),
[`references`](https://docs.ropensci.org/allodb/reference/references.md),
[`sites_info`](https://docs.ropensci.org/allodb/reference/sites_info.md),
[`sitespecies`](https://docs.ropensci.org/allodb/reference/sitespecies.md)

## Examples

``` r
# preview the datasets
print(head(equations))
#> # A tibble: 6 × 47
#>   ref_id         equation_id equation_allometry equation_form dependent_variable
#>   <chr>          <chr>       <chr>              <chr>         <chr>             
#> 1 barney_1977_b… 4b4063      exp(3.63+2.54*log… exp(a+b*log(… Total aboveground…
#> 2 baskerville_1… e2c7c7      exp(0.15+2.48*log… exp(a+b*(log… Total aboveground…
#> 3 bohn_2014_ocai e42e41      exp((1.091*(log(d… exp((a*(dbh-… Total aboveground…
#> 4 bohn_2014_ocai 2bc879      dbh/((1/1.711)+(d… dbh((1/a)+(d… Height            
#> 5 bohn_2014_ocai 9f138f      exp((1.202*(log(d… exp((a*(dbh-… Total aboveground…
#> 6 bohn_2014_ocai 7a3dce      dbh/((1/1.919)+(d… dbh((1/a)+(d… Height            
#> # ℹ 42 more variables: independent_variable <chr>, equation_taxa <chr>,
#> #   allometry_specificity <chr>, equation_categ <chr>, geographic_area <chr>,
#> #   original_coord <chr>, lat <chr>, long <chr>, elev_m <chr>,
#> #   geography_notes <chr>, mat_C <chr>, min.temp_C <chr>, max.temp_C <chr>,
#> #   map_mm <chr>, frost_free_period_days <chr>, climate_notes <chr>,
#> #   stand_age_range_yr <chr>, stand_age_history <chr>,
#> #   stand_basal_area_m2_ha <chr>, stand_trees_ha <chr>, …
print(head(equations_metadata))
#> # A tibble: 6 × 7
#>   Column Field                Description    Column_type Field_codes Units Range
#>   <chr>  <chr>                <chr>          <chr>       <chr>       <chr> <chr>
#> 1 1 / A  ref_id               Unique refere… character   NA          NA    NA   
#> 2 2 / B  equation_id          Unique equati… character   NA          NA    NA   
#> 3 3 / C  equation_allometry   Equation to c… character   NA          NA    NA   
#> 4 4 / D  equation_form        Algebraic for… character   NA          NA    NA   
#> 5 5 / E  dependent_variable   Tree componen… character   NA          NA    NA   
#> 6 6 / F  independent_variable Parameters in… character   NA          mm, … NA   
```
