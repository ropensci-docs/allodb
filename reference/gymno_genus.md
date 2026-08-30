# Gymnosperms identified in selected ForestGEO sites

Table with genus and their associated family for Gymnosperms identified
in the ForestGEO sites used in allodb.

## Usage

``` r
gymno_genus
```

## Format

An object of class `tbl_df` (inherits from `tbl`, `data.frame`) with 95
rows and 3 columns.

## See also

Other datasets:
[`genus_family`](https://docs.ropensci.org/allodb/reference/genus_family.md),
[`koppenMatrix`](https://docs.ropensci.org/allodb/reference/koppenMatrix.md),
[`scbi_stem1`](https://docs.ropensci.org/allodb/reference/scbi_stem1.md),
[`shrub_species`](https://docs.ropensci.org/allodb/reference/shrub_species.md)

## Examples

``` r
# preview the dataset
print(head(gymno_genus))
#> # A tibble: 6 × 3
#>   Family        Genus         conifer
#>   <chr>         <chr>         <lgl>  
#> 1 Araucariaceae Agathis       TRUE   
#> 2 Araucariaceae Araucaria     TRUE   
#> 3 Araucariaceae Columbea      TRUE   
#> 4 Araucariaceae Eutacta       TRUE   
#> 5 Araucariaceae Wollemia      TRUE   
#> 6 Cupressaceae  Actinostrobus TRUE   
```
