Universities & Colleges with Actuarial Programs (UCAP):
================

# Introduction:

In this project, web scraping was used to gather information about
universities around the world that offer bachelor’s, master’s, and PhD
programs in actuarial science. The data was collected from the Society
of Actuaries’ Listing of Universities and Colleges with Actuarial
Programs, but it should be noted that this project does not guarantee
the accuracy of the information. If you need a reliable list of
institutions, please visit the SOA’s website at
[**https://www.soa.org/institutions/**](https://www.soa.org/institutions/).

This project was completed as part of my research on master’s degree
programs in actuarial science in the United States and has been
recognized by the SOA.

## Library Used

Following are the list of package used for the purpose of this project.

- `dplyr` : For data manipulation

- `rvest` : For web scraping

- `tidyr` : For Data cleaning

- `stringr` : for manipulating string

- `janitor` : cleaning names

### Loading library

``` r
library(dplyr)
library(tidyr)
library(rvest)
library(janitor)
library(stringr)
```

## Web scraping

To extract table from webpage using `R`, we need `rvest` package.

First we need to install and lead the `rvest` package which i have
already done in previous section

Next, use the `read_html()` function to read the HTML content of the
webpage into R.

``` r
url <- "https://www.soa.org/institutions/"
html <- read_html(url)
```

After this , Use the `html_nodes()` function to find the table element
in the HTML.We can use `css` argument to specify a CSS selector that
matches the table elements

``` r
table <- html_nodes(html, css = "table")
```

At last , we use `html_table()` function to extract the table data from
the table element. This returns a list of data frames, one for each
table on the webpage. Since there is only one table, i have used `[[1]]`
to extract the first element of the list which is the data frame for the
table that we required

``` r
df <- html_table(table)[[1]]
```

## Data Cleaning

In r programming , we need to perform series of steps to fix or remove
any issues with the data such as errors, missing values or
inconsistencies.

Here are the problem that i obeserved and perform to clean a data frame:

### Standardize variable names and values

``` r
df <- df %>%
  janitor::clean_names()
head(df)
```

    ## # A tibble: 6 × 5
    ##   name                         level_of_actuarial_cour…¹ soa_r…² state…³ count…⁴
    ##   <chr>                        <chr>                     <chr>   <chr>   <chr>  
    ## 1 Abilene Christian University Bachelors                 UCAP-IC Texas   United…
    ## 2 Acadia University            Bachelors                 UCAP-IC Nova S… Canada 
    ## 3 Anahuac University           Bachelors                 UCAP-IC Huixqu… Mexico 
    ## 4 Anderson University          Bachelors                 UCAP-IC Indiana United…
    ## 5 Appalachian State University Bachelors                 UCAP-AC North … United…
    ## 6 Arcadia University           Bachelors                 UCAP-AC Pennsy… United…
    ## # … with abbreviated variable names ¹​level_of_actuarial_courses_offered,
    ## #   ²​soa_recognition_tier, ³​state_province, ⁴​country_territory

### Inconsistencies

``` r
df <- df %>%
  separate_rows(level_of_actuarial_courses_offered, sep = ",")

head(df)
```

    ## # A tibble: 6 × 5
    ##   name                         level_of_actuarial_cour…¹ soa_r…² state…³ count…⁴
    ##   <chr>                        <chr>                     <chr>   <chr>   <chr>  
    ## 1 Abilene Christian University Bachelors                 UCAP-IC Texas   United…
    ## 2 Acadia University            Bachelors                 UCAP-IC Nova S… Canada 
    ## 3 Anahuac University           Bachelors                 UCAP-IC Huixqu… Mexico 
    ## 4 Anderson University          Bachelors                 UCAP-IC Indiana United…
    ## 5 Appalachian State University Bachelors                 UCAP-AC North … United…
    ## 6 Arcadia University           Bachelors                 UCAP-AC Pennsy… United…
    ## # … with abbreviated variable names ¹​level_of_actuarial_courses_offered,
    ## #   ²​soa_recognition_tier, ³​state_province, ⁴​country_territory

### Unnecessary white space

``` r
df <- df %>%
  mutate(country_territory = str_trim(country_territory),
         level_of_actuarial_courses_offered = str_trim(level_of_actuarial_courses_offered))
head(df)
```

    ## # A tibble: 6 × 5
    ##   name                         level_of_actuarial_cour…¹ soa_r…² state…³ count…⁴
    ##   <chr>                        <chr>                     <chr>   <chr>   <chr>  
    ## 1 Abilene Christian University Bachelors                 UCAP-IC Texas   United…
    ## 2 Acadia University            Bachelors                 UCAP-IC Nova S… Canada 
    ## 3 Anahuac University           Bachelors                 UCAP-IC Huixqu… Mexico 
    ## 4 Anderson University          Bachelors                 UCAP-IC Indiana United…
    ## 5 Appalachian State University Bachelors                 UCAP-AC North … United…
    ## 6 Arcadia University           Bachelors                 UCAP-AC Pennsy… United…
    ## # … with abbreviated variable names ¹​level_of_actuarial_courses_offered,
    ## #   ²​soa_recognition_tier, ³​state_province, ⁴​country_territory
