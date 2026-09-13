# Genus and family table for selected ForestGEO sites

Genus and their associated family identified in the extratropical
ForestGEO sites used in allodb.

## Usage

``` r
genus_family
```

## Format

An object of class `tbl_df` (inherits from `tbl`, `data.frame`) with 248
rows and 2 columns.

## See also

Other datasets:
[`gymno_genus`](https://docs.ropensci.org/allodb/reference/gymno_genus.md),
[`koppenMatrix`](https://docs.ropensci.org/allodb/reference/koppenMatrix.md),
[`scbi_stem1`](https://docs.ropensci.org/allodb/reference/scbi_stem1.md),
[`shrub_species`](https://docs.ropensci.org/allodb/reference/shrub_species.md)

## Examples

``` r
# preview the dataset
print(head(genus_family))
#> # A tibble: 6 × 2
#>   genus       family      
#>   <chr>       <chr>       
#> 1 Acer        Sapindaceae 
#> 2 Amelanchier Rosaceae    
#> 3 Asimina     Annonaceae  
#> 4 Carpinus    Betulaceae  
#> 5 Carya       Juglandaceae
#> 6 Celtis      Cannabaceae 
```
