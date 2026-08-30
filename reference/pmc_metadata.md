# Get article metadata

Get a list of journal and article metadata in /front tag

## Usage

``` r
pmc_metadata(doc)
```

## Arguments

- doc:

  `xml_document` from PubMed Central

## Value

a list

## Author

Chris Stubben

## Examples

``` r
# doc <- pmc_xml("PMC2231364") # OR
doc <- xml2::read_xml(system.file("extdata/PMC2231364.xml",
  package = "tidypmc"
))
pmc_metadata(doc)
#> $PMCID
#> [1] "PMC2231364"
#> 
#> $Title
#> [1] "Comparative transcriptomics in Yersinia pestis: a global view of environmental modulation of gene expression"
#> 
#> $Authors
#> [1] "Yanping Han, Jingfu Qiu, Zhaobiao Guo, He Gao, Yajun Song, Dongsheng Zhou, Ruifu Yang"
#> 
#> $Year
#> [1] 2007
#> 
#> $Journal
#> [1] "BMC Microbiology"
#> 
#> $Volume
#> [1] "7"
#> 
#> $Pages
#> [1] "96"
#> 
#> $`Published online`
#> [1] "2007-10-29"
#> 
#> $`Date received`
#> [1] "2007-6-2"
#> 
#> $DOI
#> [1] "10.1186/1471-2180-7-96"
#> 
#> $Publisher
#> [1] "BioMed Central"
#> 
```
