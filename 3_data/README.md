Data
================
Antoinette Gambaro
(15 June, 2022)

-   [Dataset 1 `beaver2`](#dataset-1-beaver2)
    -   [List of the variables](#list-of-the-variables)
    -   [Description of the variables](#description-of-the-variables)
    -   [Reference](#reference)
-   [Dataset 2 `death`](#dataset-2-death)
    -   [List of the variables:](#list-of-the-variables-1)
    -   [Description of the data set](#description-of-the-data-set)
    -   [Reference](#reference-1)
-   [Dataset 3 `TimeUse`](#dataset-3-timeuse)
    -   [Description of data set](#description-of-data-set)
    -   [Reference](#reference-2)

# Dataset 1 `beaver2`

Reynolds (1994) describes a small part of a study of the long-term
temperature dynamics of beaver Castor canadensis in north-central
Wisconsin. Body temperature was measured by telemetry every 10 minutes
for four females, but data from a one period of less than a day for each
of two animals is used there.

``` r
library(knitr)
kable(head(beaver2))
```

| day | time |  temp | activ |
|----:|-----:|------:|------:|
| 307 |  930 | 36.58 |     0 |
| 307 |  940 | 36.73 |     0 |
| 307 |  950 | 36.93 |     0 |
| 307 | 1000 | 37.15 |     0 |
| 307 | 1010 | 37.23 |     0 |
| 307 | 1020 | 37.24 |     0 |

``` r
str(beaver2)
```

    ## 'data.frame':    100 obs. of  4 variables:
    ##  $ day  : num  307 307 307 307 307 307 307 307 307 307 ...
    ##  $ time : num  930 940 950 1000 1010 1020 1030 1040 1050 1100 ...
    ##  $ temp : num  36.6 36.7 36.9 37.1 37.2 ...
    ##  $ activ: num  0 0 0 0 0 0 0 0 0 0 ...

## List of the variables

This data set is composed by **4 variables that are numeric**, thus we
are dealing with quantitative data

-   Day
-   Time
-   Temperature
-   Activity

## Description of the variables

-   **day**: Day of observation (in days since the beginning of 1990)
    November 3–4 (beaver2).
-   **time**: Time of observation, in the form 0330 for 3:30am
-   **temperature**: Measured body temperature in degrees Celsius
-   **activity**: Indicator of activity outside the retreat

## Reference

P. S. Reynolds (1994) Time-series analyses of beaver body temperatures.
Chapter 11 of Lange, N., Ryan, L., Billard, L., Brillinger, D.,
Conquest, L. and Greenhouse, J. eds (1994) Case Studies in Biometry. New
York: John Wiley and Sons.

# Dataset 2 `death`

Causes of death in France from 2001-2008. Variables include year,
gender, cause of death, and number of deaths.

``` r
library(readr)
death <- read_csv("~/Desktop/DATA SCIENCE/IntroDataScience/data/death.csv")
```

    ## Rows: 1056 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (6): GEO, UNIT, SEX, AGE, ICD10, Value
    ## dbl (1): TIME
    ## lgl (1): Flag and Footnotes
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
kable(head(death))
```

| TIME | GEO    | UNIT   | SEX   | AGE   | ICD10                                               | Value   | Flag and Footnotes |
|-----:|:-------|:-------|:------|:------|:----------------------------------------------------|:--------|:-------------------|
| 2001 | France | Number | Males | Total | All causes of death (A00-Y89) excluding S00-T98     | 277 858 | NA                 |
| 2001 | France | Number | Males | Total | Certain infectious and parasitic diseases (A00-B99) | 5 347   | NA                 |
| 2001 | France | Number | Males | Total | Tuberculosis                                        | 545     | NA                 |
| 2001 | France | Number | Males | Total | Meningococcal infection                             | 30      | NA                 |
| 2001 | France | Number | Males | Total | Viral hepatitis                                     | 471     | NA                 |
| 2001 | France | Number | Males | Total | Human immunodeficiency virus \[HIV\] disease        | 892     | NA                 |

## List of the variables:

-   Time
-   Geo
-   Unit
-   Sex
-   Age
-   Value
-   ICD10

## Description of the data set

The data set is composed by **8 variables** , only one variables is
continuous (TIME), the others are qualitative measure.

## Reference

**Link**: \[EUROSTAT\]
(<http://appsso.eurostat.ec.europa.eu/nui/show.do?dataset=hlth_cd_anr&lang=en>)

# Dataset 3 `TimeUse`

This data set reports how people spend their time depending on country
and sex, with activities such as paid work, household and family care,
etc.

``` r
library(readr)
TimeUse <- read_csv("~/Desktop/DATA SCIENCE/IntroDataScience/data/TimeUse.csv")
```

    ## Rows: 28 Columns: 58
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (10): SEX, GEO/ACL00, Free time study, Tending domestic animals, Walkin...
    ## time (48): Total, Personal care, Sleep, Eating, Other and/or unspecified per...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
kable(head(TimeUse))
```

| SEX   | GEO/ACL00                                | Total    | Personal care | Sleep    | Eating   | Other and/or unspecified personal care | Employment, related activities and travel as part of/during main and second job | Main and second job and related travel | Activities related to employment and unspecified employment | Study    | School and university except homework | Homework | Free time study | Household and family care | Food management except dish washing | Dish washing | Cleaning dwelling | Household upkeep except cleaning dwelling | Laundry  | Ironing  | Handicraft and producing textiles and other care for textiles | Gardening; other pet care | Tending domestic animals | Caring for pets | Walking the dog | Construction and repairs | Shopping and services | Childcare, except teaching, reading and talking | Teaching, reading and talking with child | Household management and help family member | Leisure, social and associative life | Organisational work | Informal help to other households | Participatory activities | Visiting and feasts | Other social life | Entertainment and culture | Resting  | Walking and hiking | Sports and outdoor activities except walking and hiking | Computer games | Computing | Hobbies and games except computing and computer games | Reading books | Reading, except books | TV and video | Radio and music | Unspecified leisure | Travel except travel related to jobs | Travel to/from work | Travel related to study | Travel related to shopping and services | Transporting a child | Travel related to other household purposes | Travel related to leisure, social and associative life | Unspecified travel | Unspecified time use |
|:------|:-----------------------------------------|:---------|:--------------|:---------|:---------|:---------------------------------------|:--------------------------------------------------------------------------------|:---------------------------------------|:------------------------------------------------------------|:---------|:--------------------------------------|:---------|:----------------|:--------------------------|:------------------------------------|:-------------|:------------------|:------------------------------------------|:---------|:---------|:--------------------------------------------------------------|:--------------------------|:-------------------------|:----------------|:----------------|:-------------------------|:----------------------|:------------------------------------------------|:-----------------------------------------|:--------------------------------------------|:-------------------------------------|:--------------------|:----------------------------------|:-------------------------|:--------------------|:------------------|:--------------------------|:---------|:-------------------|:--------------------------------------------------------|:---------------|:----------|:------------------------------------------------------|:--------------|:----------------------|:-------------|:----------------|:--------------------|:-------------------------------------|:--------------------|:------------------------|:----------------------------------------|:---------------------|:-------------------------------------------|:-------------------------------------------------------|:-------------------|:---------------------|
| Males | Belgium                                  | 24:00:00 | 10:45:00      | 08:15:00 | 01:49:00 | 00:42:00                               | 03:07:00                                                                        | 03:05:00                               | 00:02:00                                                    | 00:11:00 | 00:05:00                              | 00:03:00 | 0:03            | 02:28:00                  | 00:22:00                            | 00:10:00     | 00:08:00          | 00:18:00                                  | 00:01:00 | 00:01:00 | 00:00:00                                                      | 00:19:00                  | 0:00                     | 00:03:00        | 0:05            | 00:19:00                 | 00:24:00              | 00:05:00                                        | 00:04:00                                 | 00:08:00                                    | 05:58:00                             | 00:07:00            | 00:00:00                          | 00:03:00                 | 00:32:00            | 00:23:00          | 00:10:00                  | 00:27:00 | 00:12:00           | 00:15:00                                                | 0:05           | 00:22:00  | 00:13:00                                              | 00:06:00      | 00:22:00              | 02:35:00     | 00:05:00        | 00:01:00            | 01:30:00                             | 00:25:00            | 00:02:00                | 0:16                                    | 00:03:00             | 0:00                                       | 0:15                                                   | 0:30               | 00:01:00             |
| Males | Bulgaria                                 | 24:00:00 | 11:54:00      | 09:08:00 | 02:07:00 | 00:39:00                               | 03:32:00                                                                        | 03:27:00                               | 00:04:00                                                    | 00:03:00 | 00:02:00                              | 00:01:00 | 0:00            | 02:37:00                  | 00:15:00                            | 00:05:00     | 00:06:00          | 00:22:00                                  | 00:01:00 | 00:00:00 | 00:00:00                                                      | 00:36:00                  | 0:32                     | 00:01:00        | 0:02            | 00:16:00                 | 00:13:00              | 00:02:00                                        | 00:05:00                                 | 00:01:00                                    | 04:46:00                             | 00:00:00            | 00:09:00                          | 00:01:00                 | 00:04:00            | 00:37:00          | 00:01:00                  | 00:10:00 | 00:16:00           | 00:10:00                                                | 0:00           | 00:01:00  | 00:11:00                                              | 00:06:00      | 00:15:00              | 02:41:00     | 00:06:00        | 00:01:00            | 01:07:00                             | 00:23:00            | 00:00:00                | 0:12                                    | 00:01:00             | 0:06                                       | 0:21                                                   | 0:03               | 00:02:00             |
| Males | Germany (including former GDR from 1991) | 24:00:00 | 10:40:00      | 08:08:00 | 01:43:00 | 00:49:00                               | 03:27:00                                                                        | 03:21:00                               | 00:06:00                                                    | 00:15:00 | 00:06:00                              | 00:05:00 | 0:04            | 02:22:00                  | 00:16:00                            | 00:08:00     | 00:11:00          | 00:14:00                                  | 00:02:00 | 00:01:00 | 00:00:00                                                      | 00:17:00                  | 0:01                     | 00:03:00        | 0:03            | 00:19:00                 | 00:29:00              | 00:05:00                                        | 00:05:00                                 | 00:09:00                                    | 05:42:00                             | 00:09:00            | 00:08:00                          | 00:04:00                 | 00:17:00            | 00:45:00          | 00:14:00                  | 00:16:00 | 00:13:00           | 00:15:00                                                | 0:05           | 00:16:00  | 00:18:00                                              | 00:06:00      | 00:31:00              | 01:58:00     | 00:05:00        | 00:00:00            | 01:29:00                             | 00:27:00            | 00:02:00                | 0:16                                    | 00:02:00             | 0:05                                       | 0:34                                                   | 0:03               | 00:05:00             |
| Males | Estonia                                  | 24:00:00 | 10:35:00      | 08:24:00 | 01:19:00 | 00:52:00                               | 04:27:00                                                                        | 04:20:00                               | 00:07:00                                                    | 00:06:00 | 00:03:00                              | 00:02:00 | 0:02            | 02:33:00                  | 00:21:00                            | 00:06:00     | 00:09:00          | 00:22:00                                  | 00:01:00 | 00:00:00 | 00:01:00                                                      | 00:16:00                  | 0:04                     | 00:01:00        | 0:05            | 00:29:00                 | 00:20:00              | 00:06:00                                        | 00:04:00                                 | 00:06:00                                    | 05:02:00                             | 00:02:00            | 00:15:00                          | 00:01:00                 | 00:04:00            | 00:26:00          | 00:05:00                  | 00:21:00 | 00:10:00           | 00:13:00                                                | 0:01           | 00:02:00  | 00:05:00                                              | 00:14:00      | 00:23:00              | 02:29:00     | 00:11:00        | 00:00:00            | 01:12:00                             | 00:28:00            | 00:01:00                | 0:13                                    | 00:01:00             | 0:07                                       | 0:22                                                   | 0:01               | 00:04:00             |
| Males | Spain                                    | 24:00:00 | 11:11:00      | 08:36:00 | 01:47:00 | 00:48:00                               | 04:21:00                                                                        | 04:17:00                               | 00:03:00                                                    | 00:18:00 | 00:06:00                              | 00:07:00 | 0:04            | 01:37:00                  | 00:19:00                            | 00:04:00     | 00:07:00          | 00:06:00                                  | 00:01:00 | 00:00:00 | 00:00:00                                                      | 00:09:00                  | 0:03                     | 00:01:00        | 0:03            | 00:06:00                 | 00:19:00              | 00:07:00                                        | 00:04:00                                 | 00:06:00                                    | 05:16:00                             | 00:01:00            | 00:07:00                          | 00:03:00                 | 00:12:00            | 00:45:00          | 00:07:00                  | 00:24:00 | 00:39:00           | 00:14:00                                                | 0:02           | 00:09:00  | 00:10:00                                              | 00:04:00      | 00:13:00              | 02:00:00     | 00:05:00        | 00:00:00            | 01:16:00                             | 00:31:00            | 00:02:00                | 0:07                                    | 00:02:00             | 0:03                                       | 0:28                                                   | 0:02               | 00:02:00             |
| Males | France                                   | 24:00:00 | 11:44:00      | 08:45:00 | 02:18:00 | 00:41:00                               | 03:48:00                                                                        | 03:46:00                               | 00:02:00                                                    | 00:15:00 | 00:09:00                              | 00:05:00 | 0:01            | 02:24:00                  | 00:16:00                            | 00:08:00     | 00:11:00          | 00:08:00                                  | 00:01:00 | 00:01:00 | 00:00:00                                                      | 00:18:00                  | 0:03                     | 00:05:00        | :               | 00:32:00                 | 00:30:00              | 00:05:00                                        | 00:04:00                                 | 00:04:00                                    | 04:44:00                             | 00:01:00            | 00:10:00                          | 00:07:00                 | 00:21:00            | 00:20:00          | 00:05:00                  | 00:06:00 | 00:20:00           | 00:17:00                                                | :              | 00:07:00  | 00:14:00                                              | 00:01:00      | 00:22:00              | 02:08:00     | 00:04:00        | 00:00:00            | 01:03:00                             | 00:24:00            | 00:02:00                | :                                       | 00:02:00             | :                                          | :                                                      | 0:35               | 00:02:00             |

``` r
spec(TimeUse)
```

    ## cols(
    ##   SEX = col_character(),
    ##   `GEO/ACL00` = col_character(),
    ##   Total = col_time(format = ""),
    ##   `Personal care` = col_time(format = ""),
    ##   Sleep = col_time(format = ""),
    ##   Eating = col_time(format = ""),
    ##   `Other and/or unspecified personal care` = col_time(format = ""),
    ##   `Employment, related activities and travel as part of/during main and second job` = col_time(format = ""),
    ##   `Main and second job and related travel` = col_time(format = ""),
    ##   `Activities related to employment and unspecified employment` = col_time(format = ""),
    ##   Study = col_time(format = ""),
    ##   `School and university except homework` = col_time(format = ""),
    ##   Homework = col_time(format = ""),
    ##   `Free time study` = col_character(),
    ##   `Household and family care` = col_time(format = ""),
    ##   `Food management except dish washing` = col_time(format = ""),
    ##   `Dish washing` = col_time(format = ""),
    ##   `Cleaning dwelling` = col_time(format = ""),
    ##   `Household upkeep except cleaning dwelling` = col_time(format = ""),
    ##   Laundry = col_time(format = ""),
    ##   Ironing = col_time(format = ""),
    ##   `Handicraft and producing textiles and other care for textiles` = col_time(format = ""),
    ##   `Gardening; other pet care` = col_time(format = ""),
    ##   `Tending domestic animals` = col_character(),
    ##   `Caring for pets` = col_time(format = ""),
    ##   `Walking the dog` = col_character(),
    ##   `Construction and repairs` = col_time(format = ""),
    ##   `Shopping and services` = col_time(format = ""),
    ##   `Childcare, except teaching, reading and talking` = col_time(format = ""),
    ##   `Teaching, reading and talking with child` = col_time(format = ""),
    ##   `Household management and help family member` = col_time(format = ""),
    ##   `Leisure, social and associative life` = col_time(format = ""),
    ##   `Organisational work` = col_time(format = ""),
    ##   `Informal help to other households` = col_time(format = ""),
    ##   `Participatory activities` = col_time(format = ""),
    ##   `Visiting and feasts` = col_time(format = ""),
    ##   `Other social life` = col_time(format = ""),
    ##   `Entertainment and culture` = col_time(format = ""),
    ##   Resting = col_time(format = ""),
    ##   `Walking and hiking` = col_time(format = ""),
    ##   `Sports and outdoor activities except walking and hiking` = col_time(format = ""),
    ##   `Computer games` = col_character(),
    ##   Computing = col_time(format = ""),
    ##   `Hobbies and games except computing and computer games` = col_time(format = ""),
    ##   `Reading books` = col_time(format = ""),
    ##   `Reading, except books` = col_time(format = ""),
    ##   `TV and video` = col_time(format = ""),
    ##   `Radio and music` = col_time(format = ""),
    ##   `Unspecified leisure` = col_time(format = ""),
    ##   `Travel except travel related to jobs` = col_time(format = ""),
    ##   `Travel to/from work` = col_time(format = ""),
    ##   `Travel related to study` = col_time(format = ""),
    ##   `Travel related to shopping and services` = col_character(),
    ##   `Transporting a child` = col_time(format = ""),
    ##   `Travel related to other household purposes` = col_character(),
    ##   `Travel related to leisure, social and associative life` = col_character(),
    ##   `Unspecified travel` = col_character(),
    ##   `Unspecified time use` = col_time(format = "")
    ## )

## Description of data set

Since there are 58 variables in the data set, I will say how many
variables are qualitative measure and how many are defined as time

-   **Character**: 10 variables (such as “Free time study”, “Tending
    domestic animals”, “Walking the dog”, “Computer games”,..)

-   **Time**; 48 variables (such as “Personal care”, “Sleep”, “Eating”,
    “Other and/or unspecified personal care”, “Employment”,…)

## Reference

**Link**: \[EUROSTAT\]
(<http://appsso.eurostat.ec.europa.eu/nui/show.do?dataset=tus_00week&lang=en>)
