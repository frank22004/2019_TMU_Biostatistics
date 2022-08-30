The Thickness of Collagen Membrane
================
Frank (Bo-Jiang Lin)
2022-08-28

## GitHub Documents

This is an R Markdown format used for publishing markdown documents to
GitHub. When you click the **Knit** button all R code chunks are run and
a markdown file (.md) suitable for publishing to GitHub is generated.

## Including Code

### 1. Configure the necessary environment and packages

``` r
version[['version.string']]
```

    ## [1] "R version 4.2.1 (2022-06-23 ucrt)"

``` r
library(readxl)
library(UsingR)
```

    ## Loading required package: MASS

    ## Loading required package: HistData

    ## Loading required package: Hmisc

    ## Loading required package: lattice

    ## Loading required package: survival

    ## Loading required package: Formula

    ## Loading required package: ggplot2

    ## 
    ## Attaching package: 'Hmisc'

    ## The following objects are masked from 'package:base':
    ## 
    ##     format.pval, units

    ## 
    ## Attaching package: 'UsingR'

    ## The following object is masked from 'package:survival':
    ## 
    ##     cancer

``` r
library(lessR)
```

    ## 
    ## lessR 4.2.2                         feedback: gerbing@pdx.edu 
    ## --------------------------------------------------------------
    ## > d <- Read("")   Read text, Excel, SPSS, SAS, or R data file
    ##   d is default data frame, data= in analysis routines optional
    ## 
    ## Learn about reading, writing, and manipulating data, graphics,
    ## testing means and proportions, regression, factor analysis,
    ## customization, and descriptive statistics from pivot tables.
    ##   Enter:  browseVignettes("lessR")
    ## 
    ## View changes in this or recent versions of lessR.
    ##   Enter: help(package=lessR)  Click: Package NEWS
    ##   Enter: interact()  for access to interactive graphics
    ##   New function: reshape_long() to move data from wide to long

    ## 
    ## Attaching package: 'lessR'

    ## The following objects are masked from 'package:Hmisc':
    ## 
    ##     label, Merge

### 2. Read Data

    ## # A tibble: 5 × 14
    ##   Date       Person 60 mm Dish…¹ Buffe…² Total…³ Centr…⁴ Uncom…⁵ 7days…⁶ 0 day…⁷
    ##   <date>     <chr>         <dbl>   <dbl>   <dbl>   <dbl>   <dbl>   <dbl>   <dbl>
    ## 1 2022-08-28 Frank         6262.      NA      NA      NA      NA      NA      NA
    ## 2 2022-08-28 Frank         6253.      NA      NA      NA      NA      NA      NA
    ## 3 2022-08-28 Frank         6248.      NA      NA      NA      NA      NA      NA
    ## 4 2022-08-28 Frank         6268.      NA      NA      NA      NA      NA      NA
    ## 5 2022-08-28 Frank         6263.      NA      NA      NA      NA      NA      NA
    ## # … with 5 more variables: `Compressed Thickness  (μm) after 7 days` <dbl>,
    ## #   `Compressed Thickness  (μm) after 0 days` <dbl>,
    ## #   UnCompressed_Thickness <dbl>, `7days Compression ratio` <dbl>,
    ## #   `0 days Compression ratio` <dbl>, and abbreviated variable names
    ## #   ¹​`60 mm Dish (μm)`, ²​`Buffer (pH)`, ³​Total_solution_quantity,
    ## #   ⁴​`Centrifuge time (min)`, ⁵​`Uncompressed Depth (μm)`,
    ## #   ⁶​`7days and Compressed Depth (μm)`, ⁷​`0 days and Compressed Depth (μm)`

### 3. Exploratory Data Analysis for 2022-08-28 data

#### Descriptive Statistics on the 2022-08-28 data

``` r
aggregate(collagen_Frank[c("Total_solution_quantity","UnCompressed_Thickness")],list(collagen_Frank$Total_solution_quantity),mean)
```

    ##   Group.1 Total_solution_quantity UnCompressed_Thickness
    ## 1     1.0                     1.0               471.7582
    ## 2     1.5                     1.5               627.5724

#### Check whether the 2022-08-28 data is normal distribution

``` r
summary(collagen$UnCompressed_Thickness)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.    NA's 
    ##   331.1   447.3   511.6   519.6   551.4   816.3      15

``` r
#Creat a table

normal <- shapiro.test(collagen$UnCompressed_Thickness)
normal
```

    ## 
    ##  Shapiro-Wilk normality test
    ## 
    ## data:  collagen$UnCompressed_Thickness
    ## W = 0.94094, p-value = 0.1556

##### The 2022-08-28 data shows p-value = 0.16 \>= 0.1. It represent that the data distrubute normally and ready for further test..

``` r
t.test(collagen_Frank$UnCompressed_Thickness ~ collagen_Frank$Total_solution_quantity)
```

    ## 
    ##  Welch Two Sample t-test
    ## 
    ## data:  collagen_Frank$UnCompressed_Thickness by collagen_Frank$Total_solution_quantity
    ## t = -1.937, df = 5.7962, p-value = 0.1026
    ## alternative hypothesis: true difference in means between group 1 and group 1.5 is not equal to 0
    ## 95 percent confidence interval:
    ##  -354.33488   42.70648
    ## sample estimates:
    ##   mean in group 1 mean in group 1.5 
    ##          471.7582          627.5724

### 4. Reproducibility

## Including Plots

### 1. the distribution of the 2022-08-28 data

![](Collagen-Membrane_files/figure-gfm/normal%20plot-1.png)<!-- -->

### 2. the comparison study on the 2022-08-28 data

Note that the `echo = FALSE` parameter was added to the code chunk to
prevent printing of the R code that generated the plot.
