# Separate locus tag into multiple rows

Separates locus tags mentioned in full text and expands ranges like
YPO1970-74 into new rows

## Usage

``` r
separate_tags(txt, pattern, column = "text")
```

## Arguments

- txt:

  a table

- pattern:

  regular expression to match locus tags like YPO\[0-9-\]+ or the locus
  tag prefix like YPO.

- column:

  column name to search, default "text"

## Value

a tibble with locus tag, matching text and rows.

## Author

Chris Stubben

## Examples

``` r
x <- data.frame(row = 1, text = "some genes like YPO1002 and YPO1970-74")
separate_tags(x, "YPO")
#>            id      match row                                   text
#> 1     YPO1002    YPO1002   1 some genes like YPO1002 and YPO1970-74
#> 1.1   YPO1970 YPO1970-74   1 some genes like YPO1002 and YPO1970-74
#> 1.1.1 YPO1971 YPO1970-74   1 some genes like YPO1002 and YPO1970-74
#> 1.1.2 YPO1972 YPO1970-74   1 some genes like YPO1002 and YPO1970-74
#> 1.1.3 YPO1973 YPO1970-74   1 some genes like YPO1002 and YPO1970-74
#> 1.1.4 YPO1974 YPO1970-74   1 some genes like YPO1002 and YPO1970-74
```
