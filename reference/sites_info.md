# ForestGEO sites used in allodb

Table with geographical information for extratropical ForestGEO sites
used in allodb (n=24).

## Usage

``` r
sites_info
```

## Format

An object of class `spec_tbl_df` (inherits from `tbl_df`, `tbl`,
`data.frame`) with 24 rows and 6 columns.

## Details

More details on geographical aspects of these ForestGEO sites can be
found in the accompanying manuscript.

## See also

Other database datasets:
[`equations`](https://docs.ropensci.org/allodb/reference/equations.md),
[`missing_values`](https://docs.ropensci.org/allodb/reference/missing_values.md),
[`references`](https://docs.ropensci.org/allodb/reference/references.md),
[`sitespecies`](https://docs.ropensci.org/allodb/reference/sitespecies.md)

## Examples

``` r
# preview the datasets
print(head(sites_info))
#> # A tibble: 6 × 6
#>   Site               site           lat   long   elevation.m koppen
#>   <chr>              <chr>          <chr> <chr>  <chr>       <chr> 
#> 1 Changbaishan       changbaishan   42.38 128.08 785         Dwb   
#> 2 Gutianshan         gutianshan     29.25 118.12 448         Cfa   
#> 3 Harvard Forest     harvard forest 42.54 -72.18 371         Dfb   
#> 4 Heishiding         heishiding     23.27 111.53 128         Cfa   
#> 5 Indian Cave        indian cave    40.25 -95.54 285         Dfa   
#> 6 Lilly Dickey Woods lilly dickey   39.24 -86.22 275         Cfa   
```
