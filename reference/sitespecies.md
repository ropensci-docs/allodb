# Sites and tree species used in allodb and associated metadata

- sitespecies: Table of extratropical ForestGEO sites in allodb (n=24)
  and their tree species.

- sitespecies_metadata: Metadata for sitespecies table.

## Usage

``` r
sitespecies

sitespecies_metadata
```

## Format

An object of class `spec_tbl_df` (inherits from `tbl_df`, `tbl`,
`data.frame`) with 1113 rows and 10 columns.

An object of class `spec_tbl_df` (inherits from `tbl_df`, `tbl`,
`data.frame`) with 10 rows and 4 columns.

## See also

Other database datasets:
[`equations`](https://docs.ropensci.org/allodb/reference/equations.md),
[`missing_values`](https://docs.ropensci.org/allodb/reference/missing_values.md),
[`references`](https://docs.ropensci.org/allodb/reference/references.md),
[`sites_info`](https://docs.ropensci.org/allodb/reference/sites_info.md)

## Examples

``` r
# preview the datasets
print(head(sitespecies))
#> # A tibble: 6 × 10
#>   site         family   genus species variety subspecies latin_name species_code
#>   <chr>        <chr>    <chr> <chr>   <chr>   <chr>      <chr>      <chr>       
#> 1 changbaishan Pinaceae Abies holoph… NA      NA         Abies hol… NA          
#> 2 changbaishan Pinaceae Abies nephro… NA      NA         Abies nep… NA          
#> 3 changbaishan Araliac… Acan… sentic… NA      NA         Acanthopa… NA          
#> 4 changbaishan Acerace… Acer  barbin… NA      NA         Acer barb… NA          
#> 5 changbaishan Acerace… Acer  ginnala NA      NA         Acer ginn… NA          
#> 6 changbaishan Acerace… Acer  mandsh… NA      NA         Acer mand… NA          
#> # ℹ 2 more variables: life_form <chr>, notes <chr>
print(head(sitespecies_metadata))
#> # A tibble: 6 × 4
#>   Column Field      Description                                      Column_type
#>   <chr>  <chr>      <chr>                                            <chr>      
#> 1 1 / A  site       ForestGEO site name (full site name or abbrevia… character  
#> 2 2 / B  family     Plant family name revised in Taxonomic Name Res… character  
#> 3 3 / C  genus      Plant genus name                                 character  
#> 4 4 / D  species    Plant specific name or epithet. When referring … character  
#> 5 5 / E  variety    Variation recognized within a species            character  
#> 6 6 / F  subspecies Subspecies recognized within a species           character  
```
