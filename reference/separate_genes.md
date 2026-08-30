# Separate genes and operons into multiple rows

Separate genes and operons mentioned in full text into multiple rows

## Usage

``` r
separate_genes(txt, pattern = "\\b[A-Za-z][a-z]{2}[A-Z0-9]+\\b",
  genes, operon = 6, column = "text")
```

## Arguments

- txt:

  a table

- pattern:

  regular expression to match genes, default is to match microbial genes
  like AbcD, default \[A-Za-z\]\[a-z\]2\[A-Z0-9\]+

- genes:

  an optional vector of genes, set pattern to NA to only match this
  list.

- operon:

  operon length, default 6. Split genes with 6 or more letters into
  separate genes, for example AbcDEF is split into abcD, abcE and abcF.

- column:

  column name to search, default "text"

## Value

a tibble with gene name, matching text and rows.

## Note

Check for genes in italics using
`xml_text(xml_find_all(doc, "//sec//p//italic"))` and update the pattern
or add additional genes as an optional vector if needed

## Author

Chris Stubben

## Examples

``` r
x <- data.frame(row = 1, text = "Genes like YacK, hmu and sufABC")
separate_genes(x)
#>       gene  match row                            text
#> 1     yacK   YacK   1 Genes like YacK, hmu and sufABC
#> 1.1   sufA sufABC   1 Genes like YacK, hmu and sufABC
#> 1.1.1 sufB sufABC   1 Genes like YacK, hmu and sufABC
#> 1.1.2 sufC sufABC   1 Genes like YacK, hmu and sufABC
separate_genes(x, genes = "hmu")
#>       gene  match row                            text
#> 1     yacK   YacK   1 Genes like YacK, hmu and sufABC
#> 1.1    hmu    hmu   1 Genes like YacK, hmu and sufABC
#> 1.2   sufA sufABC   1 Genes like YacK, hmu and sufABC
#> 1.2.1 sufB sufABC   1 Genes like YacK, hmu and sufABC
#> 1.2.2 sufC sufABC   1 Genes like YacK, hmu and sufABC
```
