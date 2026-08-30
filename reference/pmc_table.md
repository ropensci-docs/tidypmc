# Convert table nodes to tibbles

Convert PubMed Central table nodes into a list of tibbles

## Usage

``` r
pmc_table(doc)
```

## Arguments

- doc:

  `xml_document` from PubMed Central

## Value

a list of tibbles

## Note

Saves the caption and footnotes as attributes and collapses multiline
headers, expands all rowspan and colspan attributes and adds subheadings
to column one.

## Author

Chris Stubben

## Examples

``` r
# doc <- pmc_xml("PMC2231364")
doc <- xml2::read_xml(system.file("extdata/PMC2231364.xml",
  package = "tidypmc"
))
x <- pmc_table(doc)
#> Parsing 4 tables
#> Adding footnotes to Table 1
sapply(x, dim)
#>      Table 1 Table 2 Table 3 Table 4
#> [1,]      39      23       4      34
#> [2,]       5       5       4       4
x
#> $`Table 1`
#> # A tibble: 39 × 5
#>    subheading            Potential operon (r …¹ `Gene ID` Putative or predicte…²
#>    <chr>                 <chr>                  <chr>     <chr>                 
#>  1 Iron uptake or heme … yfeABCD operon* (r > … YPO2439-… Transport/binding che…
#>  2 Iron uptake or heme … hmuRSTUV operon (r > … YPO0279-… Transport/binding hem…
#>  3 Iron uptake or heme … ysuJIHG* (r > 0.95)    YPO1529-… Iron uptake           
#>  4 Iron uptake or heme … sufABCDS* (r > 0.90)   YPO2400-… Iron-regulated Fe-S c…
#>  5 Iron uptake or heme … YPO1854-1856* (r > 0.… YPO1854-… Iron uptake or heme s…
#>  6 Sulfur metabolism     tauABCD operon (r > 0… YPO0182-… Transport/binding tau…
#>  7 Sulfur metabolism     ssuEADCB operon (r > … YPO3623-… Sulphur metabolism    
#>  8 Sulfur metabolism     cys operon (r > 0.92)  YPO3010-… Cysteine synthesis    
#>  9 Sulfur metabolism     YPO1317-1319 (r > 0.9… YPO1317-… Sulfur metabolism?    
#> 10 Sulfur metabolism     YPO4109-4111 (r > 0.9… YPO4109-… Sulfur metabolism?    
#> # ℹ 29 more rows
#> # ℹ abbreviated names: ¹​`Potential operon (r value)`,
#> #   ²​`Putative or predicted function`
#> # ℹ 1 more variable: `Reference (s)` <chr>
#> 
#> $`Table 2`
#> # A tibble: 23 × 5
#>    subheading           `Gene locus`   `Gene ID`           Description reference
#>    <chr>                <chr>          <chr>               <chr>       <chr>    
#>  1 Category A: Proven   yfeABCD        YPO2439-2442        Inorganic … [36]     
#>  2 Category A: Proven   yfuABC         YPO2958-2960        Inorganic … [37]     
#>  3 Category A: Proven   ybt locus      YPO1906-1916        Siderophor… [74]     
#>  4 Category A: Proven   hmuRSTUV       YPO0279-0283        Heme trans… [38]     
#>  5 Category A: Proven   TonB-exbB-exbD YPO2193, YPO0682-0… TonB-ExbB-… [75]     
#>  6 Category A: Proven   yiuABCR        YPO1310-1313        Putative s… [76]     
#>  7 Category A: Proven   ysuFJIHG       YPO1528-1532        Siderophor… [76]     
#>  8 Category B: Putative fitABCD        YPO4022-4025        Putative i… NA       
#>  9 Category B: Putative Others         YPO0778-0776        putative s… NA       
#> 10 Category B: Putative NA             YPO1011-1012        putative T… NA       
#> # ℹ 13 more rows
#> 
#> $`Table 3`
#> # A tibble: 4 × 4
#>   Cluster     Genes or operons for …¹ Strict consensus of …² `Hits of consensus`
#>   <chr>       <chr>                   <chr>                  <chr>              
#> 1 Cluster I   rps-rpm-rpl operon, rp… PurR-like box: 5' ACG… rps-rpm-rpl operon…
#> 2 Cluster II  hmuRSTUV, YPO0682, YPO… Fur-like box: 5' TGAT… hmuRSTUV, YPO0682,…
#> 3 Cluster III cysB, ssuEADCB, cysK, … Fnr-like box: 5' TGAN… ssuEADCB, cysK, YP…
#> 4 Cluster IV  sdhCDAB-sucABCD, nuoA-… Fnr/Crp-like box: 5' … sdhCDAB-sucABCD, p…
#> # ℹ abbreviated names: ¹​`Genes or operons for motif discovery`,
#> #   ²​`Strict consensus of known TF-like box (See also Figure 4)`
#> 
#> $`Table 4`
#> # A tibble: 34 × 4
#>    subheading        `Environmental perturbation`   Description  `Reference (s)`
#>    <chr>             <chr>                          <chr>        <chr>          
#>  1 Stimulon analysis Temperature shift              NA           [8, 9]         
#>  2 Stimulon analysis Vegetative growth temperatures Shift from … NA             
#>  3 Stimulon analysis Heat shock                     Shift from … NA             
#>  4 Stimulon analysis Cold shock                     Shift from … NA             
#>  5 Stimulon analysis Osmotic stress                 NA           [10]           
#>  6 Stimulon analysis High osmolarity                Treatment w… NA             
#>  7 Stimulon analysis High salinity                  Treatment w… NA             
#>  8 Stimulon analysis Oxidative stress               Treatment w… NA             
#>  9 Stimulon analysis Mild acid stress               Shift from … NA             
#> 10 Stimulon analysis Low Mg2+                       Growth unde… [15]           
#> # ℹ 24 more rows
#> 
attributes(x[[1]])
#> $names
#> [1] "subheading"                     "Potential operon (r value)"    
#> [3] "Gene ID"                        "Putative or predicted function"
#> [5] "Reference (s)"                 
#> 
#> $row.names
#>  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
#> [26] 26 27 28 29 30 31 32 33 34 35 36 37 38 39
#> 
#> $class
#> [1] "tbl_df"     "tbl"        "data.frame"
#> 
#> $caption
#> [1] "Stress-responsive operons in Y. pestis predicted from microarray expression data"
#> 
#> $footnotes
#> [1] "'r' represents the correlation coefficient of adjacent genes; '*' represent the defined operon has the similar expression pattern in two other published microarray datasets [7, 21]; '?' inferred functions of uncharacterized genes; '-' means the corresponding operons have not been experimentally validated in other bacteria."
#> 
```
