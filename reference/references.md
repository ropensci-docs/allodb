# Equation references and associated metadata

- references: A data frame listing all references used in `equation`
  table.

- references_metadata: Metadata for `reference` table.

## Usage

``` r
references

references_metadata
```

## Format

An object of class `spec_tbl_df` (inherits from `tbl_df`, `tbl`,
`data.frame`) with 57 rows and 6 columns.

An object of class `spec_tbl_df` (inherits from `tbl_df`, `tbl`,
`data.frame`) with 7 rows and 4 columns.

## Details

Bibliographical information for sourced equations. Links to the
[equations](https://docs.ropensci.org/allodb/reference/equations.md)
table by `ref_id`.

## See also

Other database datasets:
[`equations`](https://docs.ropensci.org/allodb/reference/equations.md),
[`missing_values`](https://docs.ropensci.org/allodb/reference/missing_values.md),
[`sites_info`](https://docs.ropensci.org/allodb/reference/sites_info.md),
[`sitespecies`](https://docs.ropensci.org/allodb/reference/sitespecies.md)

## Examples

``` r
# preview the datasets
print(head(references))
#> # A tibble: 6 × 6
#>   ref_id            ref_doi ref_author ref_year ref_title References full cita…¹
#>   <chr>             <chr>   <chr>      <chr>    <chr>     <chr>                 
#> 1 ali_2015_abef     dx.doi… Ali        2015     Allometr… "Ali A.,\xa0Xu M.-S.,…
#> 2 barney_1977_bdac  doi.or… Barney     1977     Biomass … "Barney, R. VanCleve,…
#> 3 baskerville_1966… doi.or… Baskervil… 1966     Dry-Matt… "Baskerville, G.L. 19…
#> 4 bohn_2014_ocai    doi.or… Bohn       2014     Of clima… "Bohn F, Frak K, Huth…
#> 5 bond-lamberty_20… doi.or… Bond-lamb… 2002     Abovegro… "Bond-Lamberty, B., C…
#> 6 bridge_1979_fpom  NRA     Bridge     1979     Fuelwood… "Bridge J. 1979. Fuel…
#> # ℹ abbreviated name: ¹​`References full citation`
print(head(references_metadata))
#> # A tibble: 6 × 4
#>   Column Field       Description                                      Colum_type
#>   <chr>  <chr>       <chr>                                            <chr>     
#> 1 1 / A  ref_id      Unique reference identification number to our d… numeric   
#> 2 2 / B  ref_doi     Publication DOI (Digital object identifier)      character…
#> 3 3 / C  ref_author  Last name of first author of a cited publication character…
#> 4 4 / D  ref_year    Year of publication                              numeric   
#> 5 5 / E  ref_title   Title of publication                             character…
#> 6 6 / F  ref_journal Journal, book, report where published            character…
```
