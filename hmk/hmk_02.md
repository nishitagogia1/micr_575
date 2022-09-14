hmk_02
================
Nishita Gogia

## Question 1

# Loading of the tidyverse package into a quarto document

``` r
library("tidyverse")
```

## Question 2.1

# To check when object ‘b’ is greater or equal to object ‘a’

``` r
a <- 25
b <- 100
a <= b
```

    [1] TRUE

## Question 2.2

# To check when object ‘a’ is greater or equal to object ‘b’

``` r
a <- 25
b <- 100
a >= b
```

    [1] FALSE

## Question 3

# showing list of the objects and then removal of the objects using rm function

``` r
ls()
```

    [1] "a" "b"

``` r
rm(list=ls())
```
