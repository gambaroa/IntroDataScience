Writing scientific reports
================
Antoinette Gambaro
(15 June, 2022)

-   [THE MIND; *collaboration game*](#the-mind-collaboration-game)
    -   [Goal of the experiment](#goal-of-the-experiment)
    -   [Measurement](#measurement)
    -   [Variables](#variables)
    -   [Picture](#picture)
    -   [Data set](#data-set)
    -   [References](#references)

# THE MIND; *collaboration game*

Can community groups succeed in non-verbal coordination tasks better
than isolated (non-community) groups?

## Goal of the experiment

The **goal** is to see whether the community groups do overall better in
a non-verbal coordination task. In a community group, people will be
more cooperative and adjust their behavior than in isolated groups

## Measurement

-   the overall time it takes the group to move to the next round (time
    to success per round),
-   the overall time it takes the group to succeed the task (overall
    time to success)
-   how many tries it took to succeed a round (nb of success/nb of
    trials) (success rate per round),
-   how many tries it took to succeed the task (nb of success/nb of
    trials overall) (overall success rate)
-   the number of times participant “connect” (except the 1st mandatory)
    during the round (number of connect)
-   the number of times participant “connect” overall across the game
    (overall number of connect)

## Variables

-   **ID (1/2/3)**: identity of the person that is playing
-   **T (1/2/3/4/5/6)**: trial (coded as 1 or 0 which means if they did
    trial or not)
-   **C (1/2/3/4/5/6)**: number of connects
-   **D (1/2/3/4/5/6)**: duration of the trial
-   **G (1/2/3/4/5/6)**: gini coefficient; how much the trial was
    difficult
-   **TT**: total trial in a round
-   **DT**: total duration of the round
-   **RATE**: measure success rate of the round (number of trial divided
    by 7)

## Picture

below the cover of the game

![](https://image.smythstoys.com/original/mobile/8026362.jpg)

## Data set

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──

    ## ✔ ggplot2 3.3.5     ✔ purrr   0.3.4
    ## ✔ tibble  3.1.6     ✔ dplyr   1.0.9
    ## ✔ tidyr   1.1.4     ✔ stringr 1.4.0
    ## ✔ readr   2.1.1     ✔ forcats 0.5.1

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
library(knitr)
library(readxl)
DATA <- read_excel("~/Desktop/DATA SCIENCE/IntroDataScience/data/DATA.xlsx")
head(kable(DATA))
```

    ## [1] "| GAME| ROUND|CONDITION |ID1 |ID2 |ID3 | T1|  D1| C1|G1     | T2|  D2| C2|G2     | T3|  D3| C3|G3     | T4|  D4| C4|G4     | T5|  D5| C5|G5     | T6|  D6| C6|G6     | T7| TT|  DT|      RATE|STATION    |"
    ## [2] "|----:|-----:|:---------|:---|:---|:---|--:|---:|--:|:------|--:|---:|--:|:------|--:|---:|--:|:------|--:|---:|--:|:------|--:|---:|--:|:------|--:|---:|--:|:------|--:|--:|---:|---------:|:----------|"
    ## [3] "|    1|     1|I         |M   |N   |O   |  1| 123|  0|0.0817 |  1|  13|  0|0.3097 | NA|  NA| NA|NA     | NA|  NA| NA|NA     | NA|  NA| NA|NA     | NA|  NA| NA|NA     | NA|  2| 136| 0.2857143|FLORIANA   |"
    ## [4] "|    2|     1|I         |C   |J   |K   |  1| 289|  1|0.2616 | NA|  NA| NA|NA     | NA|  NA| NA|NA     | NA|  NA| NA|NA     | NA|  NA| NA|NA     | NA|  NA| NA|NA     | NA|  1| 289| 0.1428571|RAPHAEL    |"
    ## [5] "|    3|     1|I         |D   |E   |F   |  1|  16|  1|0.1851 |  1|  42|  1|0.1234 |  1|  66|  2|0.4463 | NA|  NA| NA|NA     | NA|  NA| NA|NA     | NA|  NA| NA|NA     | NA|  3| 124| 0.4285714|LORENE     |"
    ## [6] "|    4|     1|I         |A   |B   |C   |  1|  29|  0|0.2723 | NA|  NA| NA|NA     | NA|  NA| NA|NA     | NA|  NA| NA|NA     | NA|  NA| NA|NA     | NA|  NA| NA|NA     | NA|  1|  29| 0.1428571|INES       |"

## References

Fay, N., Garrod, S., Roberts, L., & Swoboda, N. (2010). The interactive
evolution of human communication systems. Cognitive science, 34(3),
351-386​
