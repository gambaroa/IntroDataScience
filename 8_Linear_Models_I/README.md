Linear Models I
================
Antoinette Gambaro
(20 June, 2022)

-   [Data `gapminder` from `dslabs`:](#data-gapminder-from-dslabs)
    -   [Description of the data set
        `gapminder`](#description-of-the-data-set-gapminder)
    -   [Description of the variables](#description-of-the-variables)
    -   [Correlation](#correlation)
    -   [Fitting model](#fitting-model)
    -   [Logarithmic transformation](#logarithmic-transformation)
    -   [Checking assumptions](#checking-assumptions)
        -   [Linearity of Data](#linearity-of-data)
        -   [Homogeneity of variance](#homogeneity-of-variance)
        -   [Normality of the residuals](#normality-of-the-residuals)

# Data `gapminder` from `dslabs`:

This data set reports health and income outcomes of 184 countries from
1960 to 2016.

``` r
library(tidyverse)
library(knitr)
library(dslabs)
data("gapminder")
```

## Description of the data set `gapminder`

-   Country
-   Year
-   Infant_mortality (deaths per 1000)
-   Life_expectancy (in years)
-   Fertility. (Average no of children per woman)
-   Population
-   Gpd
-   Continent
-   Region

``` r
str(gapminder,  message=FALSE,warning= FALSE)
```

    ## 'data.frame':    10545 obs. of  9 variables:
    ##  $ country         : Factor w/ 185 levels "Albania","Algeria",..: 1 2 3 4 5 6 7 8 9 10 ...
    ##  $ year            : int  1960 1960 1960 1960 1960 1960 1960 1960 1960 1960 ...
    ##  $ infant_mortality: num  115.4 148.2 208 NA 59.9 ...
    ##  $ life_expectancy : num  62.9 47.5 36 63 65.4 ...
    ##  $ fertility       : num  6.19 7.65 7.32 4.43 3.11 4.55 4.82 3.45 2.7 5.57 ...
    ##  $ population      : num  1636054 11124892 5270844 54681 20619075 ...
    ##  $ gdp             : num  NA 1.38e+10 NA NA 1.08e+11 ...
    ##  $ continent       : Factor w/ 5 levels "Africa","Americas",..: 4 1 1 2 2 3 2 5 4 3 ...
    ##  $ region          : Factor w/ 22 levels "Australia and New Zealand",..: 19 11 10 2 15 21 2 1 22 21 ...

## Description of the variables

the data frame contain *10545 observation* of *9 variables*

-   **factors**: Country, Continent, Region
-   **numeric**: Infant_mortality, life_expectancy , Fertility,
    Population, Gpd.
-   **integer**; Year

## Correlation

I want to create a linear model where fertility is the explanatory
variable and the population is the response variable in Italy

-   **infant mortality** : explanatory variable
-   **life expectancy** : response variable

let’s check whether there is a correlation between this 2 variables

``` r
Italy60 <- subset(gapminder, country == "Italy")
datait<-as.data.frame(Italy60)
```

``` r
cor(Italy60$infant_mortality,Italy60$life_expectancy,use= "pairwise.complete.obs")
```

    ## [1] -0.9332033

The results indicate that there is a high negative correlation. In other
words, as infant mortality increases, life expectancy decreases.

## Fitting model

``` r
model <-lm(infant_mortality ~ life_expectancy, datait)
summary(model)
```

    ## 
    ## Call:
    ## lm(formula = infant_mortality ~ life_expectancy, data = datait)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -6.7701 -4.1005 -0.1619  3.9915 10.1281 
    ## 
    ## Coefficients:
    ##                 Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)     229.4527    11.2681   20.36   <2e-16 ***
    ## life_expectancy  -2.8198     0.1478  -19.08   <2e-16 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 4.569 on 54 degrees of freedom
    ##   (1 observation deleted due to missingness)
    ## Multiple R-squared:  0.8709, Adjusted R-squared:  0.8685 
    ## F-statistic: 364.2 on 1 and 54 DF,  p-value: < 2.2e-16

``` r
library(ggplot2)
ggplot(datait, aes(infant_mortality, life_expectancy)) +
  geom_point(size=0.5, aplha= 0.4,) +
 geom_smooth(method = "lm", se= FALSE) +
  xlab(label= "Life Expectancy")+
  ylab(label= "Infant Mortality") +
  ggtitle(label=" Plot Life Expectancy vs Infant Mortality ") +
 theme_classic()
```

![](READMEEE_files/figure-gfm/model-1.png)<!-- --> From the Plot we can
see that there is no linear model since the line curve a little. so I
decided to perform a Logarithmic transformation which is a convenient
means of transforming a highly skewed variable into a more normalized
dataset. When modeling variables with non-linear relationships, the
chances of producing errors may also be skewed negatively.

## Logarithmic transformation

``` r
loginfant<-log(datait$infant_mortality)
loglife<-log(datait$life_expectancy)
logmodel <-lm(loginfant ~ loglife, datait)
summary(logmodel)
```

    ## 
    ## Call:
    ## lm(formula = loginfant ~ loglife, data = datait)
    ## 
    ## Residuals:
    ##      Min       1Q   Median       3Q      Max 
    ## -0.12984 -0.03806 -0.01219  0.04029  0.11885 
    ## 
    ## Coefficients:
    ##             Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)  71.6181     0.6555   109.3   <2e-16 ***
    ## loglife     -16.0000     0.1513  -105.7   <2e-16 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.06171 on 54 degrees of freedom
    ##   (1 observation deleted due to missingness)
    ## Multiple R-squared:  0.9952, Adjusted R-squared:  0.9951 
    ## F-statistic: 1.118e+04 on 1 and 54 DF,  p-value: < 2.2e-16

``` r
library(ggplot2)
??glm
ggplot(datait, aes(loginfant, loglife)) +
  geom_point(size=2, aplha= 1) +
 geom_smooth(method = "lm", se= TRUE) +
    xlab(label= " Log Life Expectancy")+
  ylab(label= "Log Infant Mortality") +
  ggtitle(label=" Plot Log Life Expectancy vs Log Infant Mortality ") +
 theme_classic()
```

![](READMEEE_files/figure-gfm/logmodel-1.png)<!-- --> As expected now
the relation seem to be more linear compared to the original variables.

## Checking assumptions

-   Linearity of Data
-   Homogeneity of variance
-   Normality in residuals

### Linearity of Data

``` r
plot(logmodel, 1)
```

![](READMEEE_files/figure-gfm/linearityassump-1.png)<!-- -->

Seem from this plot that there is no linear relation between the
variables

### Homogeneity of variance

``` r
plot(logmodel, 3)
```

![](READMEEE_files/figure-gfm/assumption-1.png)<!-- -->

``` r
library(lmtest)
library(zoo)
resbp<-bptest(logmodel)
resbp
```

    ## 
    ##  studentized Breusch-Pagan test
    ## 
    ## data:  logmodel
    ## BP = 7.1969, df = 1, p-value = 0.007303

The results from the *Breusch-Pagan test* indicates that the P value is
very small (0.007302867) ,it tests whether the variance of the errors
from a regression is dependent on the values of the independent
variables. In that case, heteroskedasticity is present. since one
assumption of linear model is that heteroskedasticity must be absent. we
can conclude that the assumption of homoskedasticity is violated.

### Normality of the residuals

``` r
plot(model, 2)
```

![](READMEEE_files/figure-gfm/assumptionnorm-1.png)<!-- -->

In this case , all the points fall approximately along this reference
line, so we can assume normality.
