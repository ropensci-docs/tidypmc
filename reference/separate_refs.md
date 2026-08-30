# Separate references cited into multiple rows

Separates references cited in brackets or parentheses into multiple rows
and splits the comma-delimited numeric strings and expands ranges like
7-9 into new rows

## Usage

``` r
separate_refs(txt, column = "text")
```

## Arguments

- txt:

  a table

- column:

  column name, default "text"

## Value

a tibble

## Author

Chris Stubben

## Examples

``` r
x <- data.frame(row = 1, text = "some important studies [7-9,15]")
separate_refs(x)
#>     id    match row                            text
#> 1    7 [7-9,15]   1 some important studies [7-9,15]
#> 1.1  8 [7-9,15]   1 some important studies [7-9,15]
#> 1.2  9 [7-9,15]   1 some important studies [7-9,15]
#> 1.3 15 [7-9,15]   1 some important studies [7-9,15]
```
