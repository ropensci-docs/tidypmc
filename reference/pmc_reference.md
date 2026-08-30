# Format references cited

Format references cited

## Usage

``` r
pmc_reference(doc)
```

## Arguments

- doc:

  `xml_document` from PubMed Central

## Value

a tibble with id, pmid, authors, year, title, journal, volume, pages,
and doi.

## Note

Mixed citations without any child tags are added to the author column.

## Author

Chris Stubben

## Examples

``` r
# doc <- pmc_xml("PMC2231364")
doc <- xml2::read_xml(system.file("extdata/PMC2231364.xml",
  package = "tidypmc"
))
x <- pmc_reference(doc)
#> Found 76 citation tags
x
#> # A tibble: 76 × 9
#>       id pmid     authors                  year title journal volume pages doi  
#>    <int> <chr>    <chr>                   <int> <chr> <chr>   <chr>  <chr> <chr>
#>  1     1 8993858  Perry RD, Fetherston JD  1997 Yers… Clin M… 10     35-66 NA   
#>  2     2 16053250 Hinnebusch BJ            2005 The … Curr I… 7      197-… NA   
#>  3     3 6469352  Straley SC, Harmon PA    1984 Yers… Infect… 45     655-… NA   
#>  4     4 15557646 Huang XZ, Lindler LE     2004 The … Infect… 72     7212… 10.1…
#>  5     5 15721832 Pujol C, Bliska JB       2005 Turn… Clin I… 114    216-… 10.1…
#>  6     6 12732299 Rhodius VA, LaRossa RA   2003 Uses… Curr O… 6      114-… 10.1…
#>  7     7 15342600 Motin VL, Georgescu AM…  2004 Temp… J Bact… 186    6298… 10.1…
#>  8     8 15557737 Han Y, Zhou D, Pang X,…  2004 Micr… Microb… 48     791-… NA   
#>  9     9 15777740 Han Y, Zhou D, Pang X,…  2005 DNA … Microb… 7      335-… 10.1…
#> 10    10 15808945 Han Y, Zhou D, Pang X,…  2005 Comp… Res Mi… 156    403-… 10.1…
#> # ℹ 66 more rows
```
