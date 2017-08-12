
<!-- README.md is generated from README.Rmd. Please edit that file -->
discoappend
===========

The `discoappend` package allows you to output additional data columns (beyond just IDs) to [`discoveryengine` definitions](https://tarakc02.github.io/discodocs/). This can be useful in a variety of situations, including:

-   sanity-check your work by previewing some basic data (like names, addresses, ratings, degrees, etc) about your definition
-   quickly output a report without having to wait out the 15-minute savedlist delay in CADS
-   so much more!

Installation
------------

You can install discoappend from github with:

``` r
devtools::install_github("cwolfsonseeley/discoappend")
```

Examples
--------

`discoappend` provides you with pre-defined report chunks that can be "appended" to your disco engine definition, resulting in reports that can be analyzed in R or exported to a spreadsheet. We won't be printing the output of the following, but once you've installed the package you can try out this code yourself to see how it works:

``` r
library(discoveryengine)
library(discoappend)

is_wealthy = has_capacity(1)
is_wealthy %>% 
  basic_bio %>% 
  display
```

That example outputs the `basic_bio` chunk, which, as the name suggests, includes basic biographical information such as names and addresses.

What makes `discoappend` so much fun, though, is that you can easily add on additional chunks as you need them:

``` r
is_wealthy %>%
  basic_bio %>%
  degrees %>%
  employment %>%
  giving %>%
  display
```

The `display` function that we're using should be familiar to disco engine users, and it does in fact work the same way. That means that you can easily household your report:

``` r
is_wealthy %>%
  basic_bio %>%
  degrees %>%
  employment %>%
  giving %>%
  display(household = TRUE)
```

For exporting to a file, as always just use the `file` argument:

``` r
is_wealthy %>%
  basic_bio %>%
  degrees %>%
  employment %>%
  giving %>%
  display(file = "wealthy-prospects-report")
```
