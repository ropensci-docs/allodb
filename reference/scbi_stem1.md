# Tree census data from SCBI ForestGEO plot

A table with tree data from the Smithsonian Conservation Biology
Institute, USA (SCBI) ForestGEO dynamics plot. This dataset is an
extract from the first tree census in 2008, only covering 1 hectare
(SCBI plot is 25.6 ha). DBH in cm.

## Usage

``` r
scbi_stem1
```

## Format

An object of class `tbl_df` (inherits from `tbl`, `data.frame`) with
2287 rows and 6 columns.

## Source

Full datasets for tree census data at SCBI can be requested through the
ForestGEO portal (<https://forestgeo.si.edu/>). Census 1, 2, and 3 can
also be accessed at the public GitHub repository for SCBI-ForestGEO Data
(<https://github.com/SCBI-ForestGEO>).

## See also

Other datasets:
[`genus_family`](https://docs.ropensci.org/allodb/reference/genus_family.md),
[`gymno_genus`](https://docs.ropensci.org/allodb/reference/gymno_genus.md),
[`koppenMatrix`](https://docs.ropensci.org/allodb/reference/koppenMatrix.md),
[`shrub_species`](https://docs.ropensci.org/allodb/reference/shrub_species.md)

## Examples

``` r
# preview the datasets
print(head(scbi_stem1))
#> # A tibble: 6 × 6
#>   treeID stemID   dbh genus species Family     
#>    <int>  <int> <dbl> <chr> <chr>   <chr>      
#> 1   2695   2695  1.41 Acer  negundo Sapindaceae
#> 2   1229  38557  1.67 Acer  negundo Sapindaceae
#> 3   1230   1230  1.42 Acer  negundo Sapindaceae
#> 4   1295  32303  1.04 Acer  negundo Sapindaceae
#> 5   1229  32273  2.47 Acer  negundo Sapindaceae
#> 6     66  31258  2.19 Acer  negundo Sapindaceae
```
