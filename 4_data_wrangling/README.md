Data wrangling
================
Antoinette Gambaro
(17 June, 2022)

-   [Data set `muders` from `dslab`:](#data-set-muders-from-dslab)
    -   [Filter:](#filter)
    -   [Select:](#select)
    -   [Arrange:](#arrange)
    -   [Observation:](#observation)
    -   [Summarize:](#summarize)
        -   [*Observation*:](#observation-1)
    -   [Removing NA:](#removing-na)
    -   [Joining 2 datasets: `results_us_election_2016` and
        `murders`](#joining-2-datasets-results_us_election_2016-and-murders)

# Data set `muders` from `dslab`:

US gun murders by state for 2010, from FBI reports. Also contains the
population of each state.

``` r
library(dslabs)
data(murders)
library(dplyr)
library(tidyverse)
library(knitr)
murders %>% head() %>% kable()
```

| state      | abb | region | population | total |
|:-----------|:----|:-------|-----------:|------:|
| Alabama    | AL  | South  |    4779736 |   135 |
| Alaska     | AK  | West   |     710231 |    19 |
| Arizona    | AZ  | West   |    6392017 |   232 |
| Arkansas   | AR  | South  |    2915918 |    93 |
| California | CA  | West   |   37253956 |  1257 |
| Colorado   | CO  | West   |    5029196 |    65 |

## Filter:

Filter the data by **Region**; *South* and *North Central* and
**population** over *1000000*

``` r
murdersfiltered  <- murders %>%
  filter(region %in% c("North Central", "South"), population > 1000000)
murdersfiltered %>% head() %>% kable()
```

| state    | abb | region        | population | total |
|:---------|:----|:--------------|-----------:|------:|
| Alabama  | AL  | South         |    4779736 |   135 |
| Arkansas | AR  | South         |    2915918 |    93 |
| Florida  | FL  | South         |   19687653 |   669 |
| Georgia  | GA  | South         |    9920000 |   376 |
| Illinois | IL  | North Central |   12830632 |   364 |
| Indiana  | IN  | North Central |    6483802 |   142 |

## Select:

I selected the filtered data frame: ***state***,***population***,
***total***

``` r
 murderselected <- murdersfiltered  %>%
  select(state, population, total)
murderselected %>% print() %>% kable()
```

    ##             state population total
    ## 1         Alabama    4779736   135
    ## 2        Arkansas    2915918    93
    ## 3         Florida   19687653   669
    ## 4         Georgia    9920000   376
    ## 5        Illinois   12830632   364
    ## 6         Indiana    6483802   142
    ## 7            Iowa    3046355    21
    ## 8          Kansas    2853118    63
    ## 9        Kentucky    4339367   116
    ## 10      Louisiana    4533372   351
    ## 11       Maryland    5773552   293
    ## 12       Michigan    9883640   413
    ## 13      Minnesota    5303925    53
    ## 14    Mississippi    2967297   120
    ## 15       Missouri    5988927   321
    ## 16       Nebraska    1826341    32
    ## 17 North Carolina    9535483   286
    ## 18           Ohio   11536504   310
    ## 19       Oklahoma    3751351   111
    ## 20 South Carolina    4625364   207
    ## 21      Tennessee    6346105   219
    ## 22          Texas   25145561   805
    ## 23       Virginia    8001024   250
    ## 24  West Virginia    1852994    27
    ## 25      Wisconsin    5686986    97

| state          | population | total |
|:---------------|-----------:|------:|
| Alabama        |    4779736 |   135 |
| Arkansas       |    2915918 |    93 |
| Florida        |   19687653 |   669 |
| Georgia        |    9920000 |   376 |
| Illinois       |   12830632 |   364 |
| Indiana        |    6483802 |   142 |
| Iowa           |    3046355 |    21 |
| Kansas         |    2853118 |    63 |
| Kentucky       |    4339367 |   116 |
| Louisiana      |    4533372 |   351 |
| Maryland       |    5773552 |   293 |
| Michigan       |    9883640 |   413 |
| Minnesota      |    5303925 |    53 |
| Mississippi    |    2967297 |   120 |
| Missouri       |    5988927 |   321 |
| Nebraska       |    1826341 |    32 |
| North Carolina |    9535483 |   286 |
| Ohio           |   11536504 |   310 |
| Oklahoma       |    3751351 |   111 |
| South Carolina |    4625364 |   207 |
| Tennessee      |    6346105 |   219 |
| Texas          |   25145561 |   805 |
| Virginia       |    8001024 |   250 |
| West Virginia  |    1852994 |    27 |
| Wisconsin      |    5686986 |    97 |

``` r
murderselected %>% head() %>% kable()
```

| state    | population | total |
|:---------|-----------:|------:|
| Alabama  |    4779736 |   135 |
| Arkansas |    2915918 |    93 |
| Florida  |   19687653 |   669 |
| Georgia  |    9920000 |   376 |
| Illinois |   12830632 |   364 |
| Indiana  |    6483802 |   142 |

``` r
murderselected  %>% tail()  %>% kable()
```

|     | state          | population | total |
|:----|:---------------|-----------:|------:|
| 20  | South Carolina |    4625364 |   207 |
| 21  | Tennessee      |    6346105 |   219 |
| 22  | Texas          |   25145561 |   805 |
| 23  | Virginia       |    8001024 |   250 |
| 24  | West Virginia  |    1852994 |    27 |
| 25  | Wisconsin      |    5686986 |    97 |

## Arrange:

I ordered the selected data frame descendant order by **population** and
then **total**

``` r
library(knitr)
murderselected <- murderselected %>% 
  arrange(desc(population), total) 
murderselected %>% head() %>% kable()
```

| state    | population | total |
|:---------|-----------:|------:|
| Texas    |   25145561 |   805 |
| Florida  |   19687653 |   669 |
| Illinois |   12830632 |   364 |
| Ohio     |   11536504 |   310 |
| Georgia  |    9920000 |   376 |
| Michigan |    9883640 |   413 |

## Observation:

We can see from this data frame, that in North Central and South of US,
**Texas** has the most amount of murder compared the other state, also
because it has **bigger population**. However **Ohio** ,which is the
fourth biggest state in terms of population, shows **fewer numbers** of
murders compared to the other state that are smaller.

## Summarize:

to get insight from the data, I grouped by regions: ***South*** and
***North Central***

``` r
summarizemurders  <- murdersfiltered %>%
  group_by(region) %>%
  summarize(average_total=mean(total, na.rm=TRUE), sd_total= sd(total, na.rm=TRUE)) %>%
arrange(average_total)
summarizemurders %>% print() %>% kable()
```

    ## # A tibble: 2 × 3
    ##   region        average_total sd_total
    ##   <fct>                 <dbl>    <dbl>
    ## 1 North Central          182.     153.
    ## 2 South                  271.     216.

| region        | average_total | sd_total |
|:--------------|--------------:|---------:|
| North Central |      181.6000 | 152.8385 |
| South         |      270.5333 | 215.6508 |

### *Observation*:

By comparing South and North Central states we can see that in the
**South there is a higher rate of murders overall.**

-   **South**: 270
-   **North Central**: 181

## Removing NA:

``` r
cleanmurders <- na.omit(murders)
str(cleanmurders)
```

    ## 'data.frame':    51 obs. of  5 variables:
    ##  $ state     : chr  "Alabama" "Alaska" "Arizona" "Arkansas" ...
    ##  $ abb       : chr  "AL" "AK" "AZ" "AR" ...
    ##  $ region    : Factor w/ 4 levels "Northeast","South",..: 2 4 4 2 4 4 1 2 2 2 ...
    ##  $ population: num  4779736 710231 6392017 2915918 37253956 ...
    ##  $ total     : num  135 19 232 93 1257 ...

By using the function to remove the NA from the original data, we can
see that there are no changes, the number of observation remained the
same, thus there is no NA in the original data frame.

## Joining 2 datasets: `results_us_election_2016` and `murders`

Joining from dslabs`package,`results_us_election_2016`and`murders\`:

``` r
joineddata<-full_join(results_us_election_2016, murders)
head(kable(joineddata))
```

    ## [1] "|state                | electoral_votes| clinton| trump| others|abb |region        | population| total|"
    ## [2] "|:--------------------|---------------:|-------:|-----:|------:|:---|:-------------|----------:|-----:|"
    ## [3] "|California           |              55|    61.7|  31.6|    6.7|CA  |West          |   37253956|  1257|"
    ## [4] "|Texas                |              38|    43.2|  52.2|    4.5|TX  |South         |   25145561|   805|"
    ## [5] "|Florida              |              29|    47.8|  49.0|    3.2|FL  |South         |   19687653|   669|"
    ## [6] "|New York             |              29|    59.0|  36.5|    4.5|NY  |Northeast     |   19378102|   517|"

It would interesting seeing whether people who come from a specif region
are more prone to vote Trump or Clinton, thus if there is a significant
difference in the votes, by controlling for the region. I would group
the data by region, and summarize the average and the standard deviation
of votes for Clinton and Trump.
