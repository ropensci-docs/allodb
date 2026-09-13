# Explanations of missing values codes

Explanation of the codes used to indicate missing information in
equation table.

## Usage

``` r
missing_values
```

## Format

An object of class `spec_tbl_df` (inherits from `tbl_df`, `tbl`,
`data.frame`) with 4 rows and 3 columns.

## See also

Other database datasets:
[`equations`](https://docs.ropensci.org/allodb/reference/equations.md),
[`references`](https://docs.ropensci.org/allodb/reference/references.md),
[`sites_info`](https://docs.ropensci.org/allodb/reference/sites_info.md),
[`sitespecies`](https://docs.ropensci.org/allodb/reference/sitespecies.md)

## Examples

``` r
# preview the dataset
print(head(missing_values))
#> # A tibble: 4 × 3
#>   Code  Definition            Description                                       
#>   <chr> <chr>                 <chr>                                             
#> 1 NA    Not Applicable        Data does not apply to that particular case       
#> 2 NAC   Not Acquired          Information may be available but has not been acq…
#> 3 NRA   Not Readily Available Information was not readily available to the auth…
#> 4 NI    No Information        No information available in original publication  
```
