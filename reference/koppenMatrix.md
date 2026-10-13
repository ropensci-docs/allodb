# Koppen climate classification matrix

A table built to facilitate the comparison between the Koppen climate of
a site and the allometric equation in question.

## Usage

``` r
koppenMatrix
```

## Format

An object of class `tbl_df` (inherits from `tbl`, `data.frame`) with 900
rows and 3 columns.

## Details

The value of column `we` is the weight given to the combination of
Koppen climates in columns `zone1` and `zone2`; the table is symmetric:
`zone1` and `zone2` can be interchanged. This weight is calculated in 3
steps: (1) if the main climate group (first letter) is the same, the
climate weight starts at 0.4; if one of the groups is "C" (temperate
climate) and the other is "D" (continental climate), the climate weight
starts at 0.2 because the 2 groups are considered similar enough;
otherwise, the weight is 0; (2) if the equation and site belong to the
same group, the weight is incremented by an additional value between 0
and 0.3 based on precipitation pattern similarity (second letter of the
Koppen zone), and (3) by an additional value between 0 and 0.3 based on
temperature pattern similarity (third letter of the Koppen zone). The
resulting weight has a value between 0 (different climate groups) and 1
(exactly the same climate classification).

## See also

Other datasets:
[`genus_family`](https://docs.ropensci.org/allodb/reference/genus_family.md),
[`gymno_genus`](https://docs.ropensci.org/allodb/reference/gymno_genus.md),
[`scbi_stem1`](https://docs.ropensci.org/allodb/reference/scbi_stem1.md),
[`shrub_species`](https://docs.ropensci.org/allodb/reference/shrub_species.md)

## Examples

``` r
# preview the dataset
print(head(koppenMatrix))
#> # A tibble: 6 × 3
#>   zone1 zone2       we
#>   <chr> <chr>    <dbl>
#> 1 Af    Af    1       
#> 2 Am    Af    0.9     
#> 3 As    Af    0.7     
#> 4 Aw    Af    0.8     
#> 5 BSh   Af    0.000001
#> 6 BSk   Af    0.000001
```
