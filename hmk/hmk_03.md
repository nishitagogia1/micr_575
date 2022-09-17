hmk_03
================
nishita gogia

## Loading the tidyverse library

``` r
library("tidyverse")
```

## Reading of the csv data file created in hmk folder

``` r
experiment <- read_csv(file= "C:/Users/ngogia/Documents/classes_2022/micr_575/hmk/my_data.csv")
```

    Rows: 20 Columns: 8
    ── Column specification ────────────────────────────────────────────────────────
    Delimiter: ","
    chr (3): ID, Gene Symbol, Description
    dbl (5): log2.adipogenesisAvg, control Avg (log2), Foldchange, P-val, FDR P-val

    ℹ Use `spec()` to retrieve the full column specification for this data.
    ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

\##Investigating the properties of data frames

``` r
glimpse(experiment)
```

    Rows: 20
    Columns: 8
    $ ID                   <chr> "207175_at", "203548_s_at", "203980_at", "235978_…
    $ log2.adipogenesisAvg <dbl> 12.28, 11.69, 13.18, 12.02, 11.89, 10.56, 10.15, …
    $ `control Avg (log2)` <dbl> 3.05, 2.71, 4.49, 3.35, 3.47, 2.95, 2.96, 4.76, 2…
    $ Foldchange           <dbl> 600.18, 502.98, 412.70, 407.82, 342.93, 196.15, 1…
    $ `P-val`              <dbl> 5.81e-07, 4.00e-04, 7.73e-06, 2.90e-03, 1.10e-03,…
    $ `FDR P-val`          <dbl> 0.0079, 0.0715, 0.0235, 0.1386, 0.0972, 0.0358, 0…
    $ `Gene Symbol`        <chr> "ADIPOQ", "LPL", "FABP4", "FABP4", "LPL", "THRSP"…
    $ Description          <chr> "adiponectin, C1Q and collagen domain containing"…

``` r
str(experiment)
```

    spec_tbl_df [20 × 8] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
     $ ID                  : chr [1:20] "207175_at" "203548_s_at" "203980_at" "235978_at" ...
     $ log2.adipogenesisAvg: num [1:20] 12.3 11.7 13.2 12 11.9 ...
     $ control Avg (log2)  : num [1:20] 3.05 2.71 4.49 3.35 3.47 2.95 2.96 4.76 2.42 3.18 ...
     $ Foldchange          : num [1:20] 600 503 413 408 343 ...
     $ P-val               : num [1:20] 5.81e-07 4.00e-04 7.73e-06 2.90e-03 1.10e-03 5.90e-05 3.30e-06 4.10e-06 9.08e-05 3.00e-04 ...
     $ FDR P-val           : num [1:20] 0.0079 0.0715 0.0235 0.1386 0.0972 ...
     $ Gene Symbol         : chr [1:20] "ADIPOQ" "LPL" "FABP4" "FABP4" ...
     $ Description         : chr [1:20] "adiponectin, C1Q and collagen domain containing" "lipoprotein lipase" "fatty acid binding protein 4, adipocyte" "fatty acid binding protein 4, adipocyte" ...
     - attr(*, "spec")=
      .. cols(
      ..   ID = col_character(),
      ..   log2.adipogenesisAvg = col_double(),
      ..   `control Avg (log2)` = col_double(),
      ..   Foldchange = col_double(),
      ..   `P-val` = col_double(),
      ..   `FDR P-val` = col_double(),
      ..   `Gene Symbol` = col_character(),
      ..   Description = col_character()
      .. )
     - attr(*, "problems")=<externalptr> 

I tried the function glimpse and str- in case of str it gives you very
elaborate version of your file including the type of vector is used in
particular column. Glimpse is very handy to check if you have loaded all
the data you needed but it just reads only the data frame and not any
object unlike the str feature. They both are equally good depending upon
the circumstances you are using in.

## Manipulating the data frames

``` r
experiment$Change2 <- 2 / experiment$Foldchange
glimpse(experiment)
```

    Rows: 20
    Columns: 9
    $ ID                   <chr> "207175_at", "203548_s_at", "203980_at", "235978_…
    $ log2.adipogenesisAvg <dbl> 12.28, 11.69, 13.18, 12.02, 11.89, 10.56, 10.15, …
    $ `control Avg (log2)` <dbl> 3.05, 2.71, 4.49, 3.35, 3.47, 2.95, 2.96, 4.76, 2…
    $ Foldchange           <dbl> 600.18, 502.98, 412.70, 407.82, 342.93, 196.15, 1…
    $ `P-val`              <dbl> 5.81e-07, 4.00e-04, 7.73e-06, 2.90e-03, 1.10e-03,…
    $ `FDR P-val`          <dbl> 0.0079, 0.0715, 0.0235, 0.1386, 0.0972, 0.0358, 0…
    $ `Gene Symbol`        <chr> "ADIPOQ", "LPL", "FABP4", "FABP4", "LPL", "THRSP"…
    $ Description          <chr> "adiponectin, C1Q and collagen domain containing"…
    $ Change2              <dbl> 0.003332334, 0.003976301, 0.004846135, 0.00490412…

## Calculating the mean of columns for original column and added column

``` r
mean(experiment$Foldchange)
```

    [1] 183.276

``` r
mean (experiment$Change2)
```

    [1] 0.01925863

``` r
glimpse(experiment)
```

    Rows: 20
    Columns: 9
    $ ID                   <chr> "207175_at", "203548_s_at", "203980_at", "235978_…
    $ log2.adipogenesisAvg <dbl> 12.28, 11.69, 13.18, 12.02, 11.89, 10.56, 10.15, …
    $ `control Avg (log2)` <dbl> 3.05, 2.71, 4.49, 3.35, 3.47, 2.95, 2.96, 4.76, 2…
    $ Foldchange           <dbl> 600.18, 502.98, 412.70, 407.82, 342.93, 196.15, 1…
    $ `P-val`              <dbl> 5.81e-07, 4.00e-04, 7.73e-06, 2.90e-03, 1.10e-03,…
    $ `FDR P-val`          <dbl> 0.0079, 0.0715, 0.0235, 0.1386, 0.0972, 0.0358, 0…
    $ `Gene Symbol`        <chr> "ADIPOQ", "LPL", "FABP4", "FABP4", "LPL", "THRSP"…
    $ Description          <chr> "adiponectin, C1Q and collagen domain containing"…
    $ Change2              <dbl> 0.003332334, 0.003976301, 0.004846135, 0.00490412…

## Show what each of the following returns, and explain what each line of code is doing: - using read.csv function for loading the feline data

``` r
cats <- read.csv (file = "C:/Users/ngogia/Documents/classes_2022/micr_575/hmk/feline_data.csv")
```

-   this function delineates the first row of the data along with its
    header

``` r
cats[1]
```

        coat
    1 calico
    2  black
    3  tabby
    4  black

-   this function just reads the contents of the first row without the
    header of the row

``` r
cats[[1]]
```

    [1] "calico" "black"  "tabby"  "black" 

-   this function delienates the contents of the header coat in the cats
    object

``` r
cats$coat
```

    [1] "calico" "black"  "tabby"  "black" 

-   this function reads the first row and column of the data frame

``` r
cats[1, 1]
```

    [1] "calico"

-   this function reads the contents of the first row without its header

``` r
cats[ , 1]
```

    [1] "calico" "black"  "tabby"  "black" 

-   this function calls for all the columns of the first row

``` r
cats[1, ]
```

        coat weight likes.string
    1 calico    2.1         TRUE
