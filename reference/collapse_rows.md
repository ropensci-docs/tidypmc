# Collapse a list of PubMed Central tables

Collapse rows into a semi-colon delimited list with column names and
cell values

## Usage

``` r
collapse_rows(pmc, na.string)
```

## Arguments

- pmc:

  a list of tables, usually from
  [`pmc_table`](https://docs.ropensci.org/tidypmc/reference/pmc_table.md)

- na.string:

  additional cell values to skip, default is NA and ""

## Value

A tibble with table and row number and collapsed text

## Author

Chris Stubben

## Examples

``` r
x <- data.frame(
  genes = c("aroB", "glnP", "ndhA", "pyrF"),
  fold_change = c(2.5, 1.7, -3.1, -2.6)
)
collapse_rows(list(`Table 1` = x))
#> # A tibble: 4 × 3
#>   table     row text                        
#>   <chr>   <int> <chr>                       
#> 1 Table 1     1 genes=aroB; fold_change=2.5 
#> 2 Table 1     2 genes=glnP; fold_change=1.7 
#> 3 Table 1     3 genes=ndhA; fold_change=-3.1
#> 4 Table 1     4 genes=pyrF; fold_change=-2.6
```
