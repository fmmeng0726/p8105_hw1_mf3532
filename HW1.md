P8105_HW1
================
Meng Fang
2022-09-19

## Problem 1

### Load `penguins`

``` r
data("penguins", package = "palmerpenguins")
```

### Short Description of Dataset

-   Names/Values of Important Variables

``` r
names(penguins)
```

    ## [1] "species"           "island"            "bill_length_mm"   
    ## [4] "bill_depth_mm"     "flipper_length_mm" "body_mass_g"      
    ## [7] "sex"               "year"

We can see that there are 8 variables in this dataset describing
penguins, including species, island, bill_length_mm, bill_depth_mm,
flipper_length_mm, body_mass_g, sex, year.

-   Size of Dataset

``` r
nrow(penguins)
```

    ## [1] 344

``` r
ncol(penguins)
```

    ## [1] 8

This dataset has 344 rows and 8 columns.

-   Mean of flipper length

``` r
mean(penguins$flipper_length_mm, na.rm = TRUE)
```

    ## [1] 200.9152

By dropping 1 unknown flipper length in the datasetm we get that the
mean flipper length is 200.9152047

### Scatterplot of Flipper Length vs Bill Length

``` r
ggp <- penguins %>%
  ggplot() +
  geom_point(mapping = aes(x = bill_length_mm, y = flipper_length_mm, color = species), na.rm = TRUE)

ggp
```

![](HW1_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

``` r
#save scatterplot
ggsave(filename = "scatterplot_penguin.pdf", plot = ggp, height = 4, width = 6)
```

## Problem 2

``` r
df <- tibble(
  var_num = rnorm(10, mean = 0, sd = 1),
  var_logic = var_num > 0,
  var_char  = c('a','b','c','d','e','f','g','h','j','k'),
  var_factor = factor(c("low","middle","high","low","middle","high","low","middle","high","low"))
)
```

### Take Mean of Each variable

-   mean of numeric variable

``` r
#mean of numeric variable
mean(df$var_num)
```

    ## [1] -0.2937456

``` r
#mean of logic variable
mean(df$var_logic)
```

    ## [1] 0.4

``` r
#mean of character variable
mean(df$var_char)
```

    ## Warning in mean.default(df$var_char): argument is not numeric or logical:
    ## returning NA

    ## [1] NA

``` r
#mean of factor variable
mean(df$var_factor)
```

    ## Warning in mean.default(df$var_factor): argument is not numeric or logical:
    ## returning NA

    ## [1] NA

Shown above, we can take means of numerical and logical variables, and
we cannot take means of character and factor variables.

### Apply `as.numeric`

``` r
#mean of logic variable
mean(as.numeric(df$var_logic))
#mean of character variable
mean(as.numeric(df$var_char))
```

    ## Warning in mean(as.numeric(df$var_char)): NAs introduced by coercion

``` r
#mean of factor variable
mean(as.numeric(df$var_factor))
```

Now we see that we can get a mean from the factor variable and we still
cannot get a mean from the character variable. We can only take means
for numerical values. In this case the factor variable can be converted
to numeric variable based on the levels of each observation, but for the
character variable we are unable to make such conversion.
