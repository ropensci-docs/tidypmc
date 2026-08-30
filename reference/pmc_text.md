# Split section paragraphs into sentences

Split section paragraph tags into a table with subsection titles and
sentences using `tokenize_sentences`

## Usage

``` r
pmc_text(doc)
```

## Arguments

- doc:

  `xml_document` from PubMed Central

## Value

a tibble with section, paragraph and sentence number and text

## Note

Subsections may be nested to arbitrary depths and this function will
return the entire path to the subsection title as a delimited string
like "Results; Predicted functions; Pathogenicity". Tables, figures and
formulas that are nested in section paragraphs are removed,
superscripted references are replaced with brackets, and any other
superscripts or subscripts are separared with ^ and \_.

## Author

Chris Stubben

## Examples

``` r
# doc <- pmc_xml("PMC2231364")
doc <- xml2::read_xml(system.file("extdata/PMC2231364.xml",
  package = "tidypmc"
))
txt <- pmc_text(doc)
txt
#> # A tibble: 194 × 4
#>    section    paragraph sentence text                                           
#>    <chr>          <int>    <int> <chr>                                          
#>  1 Title              1        1 Comparative transcriptomics in Yersinia pestis…
#>  2 Abstract           1        1 Environmental modulation of gene expression in…
#>  3 Abstract           1        2 Using cDNA microarray technology, we have anal…
#>  4 Abstract           2        1 To provide us with a comprehensive view of env…
#>  5 Abstract           2        2 Almost all known virulence genes of Y. pestis …
#>  6 Abstract           2        3 Clustering enabled us to functionally classify…
#>  7 Abstract           2        4 Collections of operons were predicted from the…
#>  8 Abstract           2        5 Several regulatory DNA motifs, probably recogn…
#>  9 Abstract           3        1 The comparative transcriptomics analysis we pr…
#> 10 Background         1        1 Yersinia pestis is the etiological agent of pl…
#> # ℹ 184 more rows
dplyr::count(txt, section, sort = TRUE)
#> # A tibble: 21 × 2
#>    section                                                                     n
#>    <chr>                                                                   <int>
#>  1 Results and Discussion; Clustering analysis and functional classificat…    22
#>  2 Background                                                                 20
#>  3 Results and Discussion; Virulence genes in response to multiple enviro…    20
#>  4 Methods; Collection of microarray expression data                          17
#>  5 Results and Discussion; Computational discovery of regulatory DNA moti…    16
#>  6 Methods; Gel mobility shift analysis of Fur binding                        13
#>  7 Results and Discussion; Verification of predicted operons by RT-PCR        10
#>  8 Abstract                                                                    8
#>  9 Methods; Discovery of regulatory DNA motifs                                 8
#> 10 Methods; Clustering analysis                                                7
#> # ℹ 11 more rows
```
