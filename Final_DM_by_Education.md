Final Project
================
Bess Lenz
2025-06-27

## R Markdown

brief explanation: making modifications to update on github

# Load data

# Examine raw variables

``` r
names(demo)
```

    ##  [1] "SEQN"     "SDDSRVYR" "RIDSTATR" "RIAGENDR" "RIDAGEYR" "RIDAGEMN"
    ##  [7] "RIDRETH1" "RIDRETH3" "RIDEXMON" "RIDEXAGM" "DMQMILIZ" "DMDBORN4"
    ## [13] "DMDYRUSR" "DMDEDUC2" "DMDMARTZ" "RIDEXPRG" "DMDHHSIZ" "DMDHRGND"
    ## [19] "DMDHRAGZ" "DMDHREDZ" "DMDHRMAZ" "DMDHSEDZ" "WTINT2YR" "WTMEC2YR"
    ## [25] "SDMVSTRA" "SDMVPSU"  "INDFMPIR"

``` r
str(demo)
```

    ## tibble [11,933 × 27] (S3: tbl_df/tbl/data.frame)
    ##  $ SEQN    : num [1:11933] 130378 130379 130380 130381 130382 ...
    ##   ..- attr(*, "label")= chr "Respondent sequence number"
    ##  $ SDDSRVYR: num [1:11933] 12 12 12 12 12 12 12 12 12 12 ...
    ##   ..- attr(*, "label")= chr "Data release cycle"
    ##  $ RIDSTATR: num [1:11933] 2 2 2 2 2 1 1 1 2 2 ...
    ##   ..- attr(*, "label")= chr "Interview/Examination status"
    ##  $ RIAGENDR: num [1:11933] 1 1 2 2 1 2 1 2 1 2 ...
    ##   ..- attr(*, "label")= chr "Gender"
    ##  $ RIDAGEYR: num [1:11933] 43 66 44 5 2 3 43 65 34 68 ...
    ##   ..- attr(*, "label")= chr "Age in years at screening"
    ##  $ RIDAGEMN: num [1:11933] NA NA NA NA NA NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "Age in months at screening - 0 to 24 mos"
    ##  $ RIDRETH1: num [1:11933] 5 3 2 5 3 2 1 3 1 3 ...
    ##   ..- attr(*, "label")= chr "Race/Hispanic origin"
    ##  $ RIDRETH3: num [1:11933] 6 3 2 7 3 2 1 3 1 3 ...
    ##   ..- attr(*, "label")= chr "Race/Hispanic origin w/ NH Asian"
    ##  $ RIDEXMON: num [1:11933] 2 2 1 1 2 NA NA NA 1 2 ...
    ##   ..- attr(*, "label")= chr "Six-month time period"
    ##  $ RIDEXAGM: num [1:11933] NA NA NA 71 34 NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "Age in months at exam - 0 to 19 years"
    ##  $ DMQMILIZ: num [1:11933] 2 2 2 NA NA NA 2 2 2 2 ...
    ##   ..- attr(*, "label")= chr "Served active duty in US Armed Forces"
    ##  $ DMDBORN4: num [1:11933] 2 1 2 1 1 1 2 1 1 1 ...
    ##   ..- attr(*, "label")= chr "Country of birth"
    ##  $ DMDYRUSR: num [1:11933] 6 NA 6 NA NA NA 5 NA NA NA ...
    ##   ..- attr(*, "label")= chr "Length of time in US"
    ##  $ DMDEDUC2: num [1:11933] 5 5 3 NA NA NA 2 3 4 5 ...
    ##   ..- attr(*, "label")= chr "Education level - Adults 20+"
    ##  $ DMDMARTZ: num [1:11933] 1 1 1 NA NA NA 3 1 1 3 ...
    ##   ..- attr(*, "label")= chr "Marital status"
    ##  $ RIDEXPRG: num [1:11933] NA NA 2 NA NA NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "Pregnancy status at exam"
    ##  $ DMDHHSIZ: num [1:11933] 4 2 7 2 4 3 2 2 3 1 ...
    ##   ..- attr(*, "label")= chr "Total number of people in the Household"
    ##  $ DMDHRGND: num [1:11933] NA NA NA 2 2 2 NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "HH ref person\x92s gender"
    ##  $ DMDHRAGZ: num [1:11933] NA NA NA 2 2 2 NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "HH ref person\x92s age in years"
    ##  $ DMDHREDZ: num [1:11933] NA NA NA 2 3 NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "HH ref person\x92s education level"
    ##  $ DMDHRMAZ: num [1:11933] NA NA NA 3 1 1 NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "HH ref person\x92s marital status"
    ##  $ DMDHSEDZ: num [1:11933] NA NA NA NA 2 NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "HH ref person\x92s spouse\x92s education level"
    ##  $ WTINT2YR: num [1:11933] 50055 29087 80063 38807 30608 ...
    ##   ..- attr(*, "label")= chr "Full sample 2-year interview weight"
    ##   ..- attr(*, "format.sas")= chr "20.6"
    ##  $ WTMEC2YR: num [1:11933] 54374 34085 81196 55699 36434 ...
    ##   ..- attr(*, "label")= chr "Full sample 2-year MEC exam weight"
    ##   ..- attr(*, "format.sas")= chr "20.6"
    ##  $ SDMVSTRA: num [1:11933] 173 173 174 182 182 176 179 187 179 181 ...
    ##   ..- attr(*, "label")= chr "Masked variance pseudo-stratum"
    ##  $ SDMVPSU : num [1:11933] 2 2 1 2 2 2 2 2 1 1 ...
    ##   ..- attr(*, "label")= chr "Masked variance pseudo-PSU"
    ##  $ INDFMPIR: num [1:11933] 5 5 1.41 1.53 3.6 NA 0.63 5 1.33 1.32 ...
    ##   ..- attr(*, "label")= chr "Ratio of family income to poverty"
    ##  - attr(*, "label")= chr "Demographic Variables and Sample Weights"

``` r
summary(demo)
```

    ##       SEQN           SDDSRVYR     RIDSTATR        RIAGENDR        RIDAGEYR    
    ##  Min.   :130378   Min.   :12   Min.   :1.000   Min.   :1.000   Min.   : 0.00  
    ##  1st Qu.:133361   1st Qu.:12   1st Qu.:1.000   1st Qu.:1.000   1st Qu.:13.00  
    ##  Median :136344   Median :12   Median :2.000   Median :2.000   Median :37.00  
    ##  Mean   :136344   Mean   :12   Mean   :1.742   Mean   :1.533   Mean   :38.32  
    ##  3rd Qu.:139327   3rd Qu.:12   3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.:62.00  
    ##  Max.   :142310   Max.   :12   Max.   :2.000   Max.   :2.000   Max.   :80.00  
    ##                                                                               
    ##     RIDAGEMN        RIDRETH1        RIDRETH3        RIDEXMON       RIDEXAGM    
    ##  Min.   : 0.00   Min.   :1.000   Min.   :1.000   Min.   :1.00   Min.   :  0.0  
    ##  1st Qu.: 6.00   1st Qu.:3.000   1st Qu.:3.000   1st Qu.:1.00   1st Qu.: 66.0  
    ##  Median :11.00   Median :3.000   Median :3.000   Median :2.00   Median :122.0  
    ##  Mean   :11.63   Mean   :3.105   Mean   :3.321   Mean   :1.52   Mean   :121.9  
    ##  3rd Qu.:17.00   3rd Qu.:4.000   3rd Qu.:4.000   3rd Qu.:2.00   3rd Qu.:179.5  
    ##  Max.   :24.00   Max.   :5.000   Max.   :7.000   Max.   :2.00   Max.   :239.0  
    ##  NA's   :11556                                   NA's   :3073   NA's   :9146   
    ##     DMQMILIZ        DMDBORN4        DMDYRUSR         DMDEDUC2    
    ##  Min.   :1.000   Min.   :1.000   Min.   : 1.000   Min.   :1.000  
    ##  1st Qu.:2.000   1st Qu.:1.000   1st Qu.: 3.000   1st Qu.:3.000  
    ##  Median :2.000   Median :1.000   Median : 6.000   Median :4.000  
    ##  Mean   :1.917   Mean   :1.157   Mean   : 7.335   Mean   :3.805  
    ##  3rd Qu.:2.000   3rd Qu.:1.000   3rd Qu.: 6.000   3rd Qu.:5.000  
    ##  Max.   :7.000   Max.   :2.000   Max.   :99.000   Max.   :9.000  
    ##  NA's   :3632    NA's   :19      NA's   :10058    NA's   :4139   
    ##     DMDMARTZ         RIDEXPRG        DMDHHSIZ        DMDHRGND    
    ##  Min.   : 1.000   Min.   :1.000   Min.   :1.000   Min.   :1.000  
    ##  1st Qu.: 1.000   1st Qu.:2.000   1st Qu.:2.000   1st Qu.:1.000  
    ##  Median : 1.000   Median :2.000   Median :3.000   Median :2.000  
    ##  Mean   : 1.778   Mean   :2.237   Mean   :3.243   Mean   :1.564  
    ##  3rd Qu.: 2.000   3rd Qu.:3.000   3rd Qu.:4.000   3rd Qu.:2.000  
    ##  Max.   :99.000   Max.   :3.000   Max.   :7.000   Max.   :2.000  
    ##  NA's   :4141     NA's   :10430                   NA's   :7818   
    ##     DMDHRAGZ       DMDHREDZ        DMDHRMAZ        DMDHSEDZ    
    ##  Min.   :1.00   Min.   :1.000   Min.   :1.000   Min.   :1.000  
    ##  1st Qu.:2.00   1st Qu.:2.000   1st Qu.:1.000   1st Qu.:2.000  
    ##  Median :2.00   Median :2.000   Median :1.000   Median :2.000  
    ##  Mean   :2.54   Mean   :2.171   Mean   :1.381   Mean   :2.275  
    ##  3rd Qu.:3.00   3rd Qu.:3.000   3rd Qu.:2.000   3rd Qu.:3.000  
    ##  Max.   :4.00   Max.   :3.000   Max.   :3.000   Max.   :3.000  
    ##  NA's   :7809   NA's   :8187    NA's   :7913    NA's   :9806   
    ##     WTINT2YR         WTMEC2YR         SDMVSTRA        SDMVPSU     
    ##  Min.   :  4584   Min.   :     0   Min.   :173.0   Min.   :1.000  
    ##  1st Qu.: 14332   1st Qu.:     0   1st Qu.:176.0   1st Qu.:1.000  
    ##  Median : 21670   Median : 21718   Median :180.0   Median :1.000  
    ##  Mean   : 27404   Mean   : 27404   Mean   :179.9   Mean   :1.492  
    ##  3rd Qu.: 33831   3rd Qu.: 38341   3rd Qu.:184.0   3rd Qu.:2.000  
    ##  Max.   :170968   Max.   :227108   Max.   :187.0   Max.   :2.000  
    ##                                                                   
    ##     INDFMPIR    
    ##  Min.   :0.000  
    ##  1st Qu.:1.180  
    ##  Median :2.500  
    ##  Mean   :2.708  
    ##  3rd Qu.:4.500  
    ##  Max.   :5.000  
    ##  NA's   :2041

``` r
table(demo$DMDEDUC2)
```

    ## 
    ##    1    2    3    4    5    9 
    ##  373  666 1749 2370 2625   11

``` r
table(is.na(demo$DMDEDUC2))
```

    ## 
    ## FALSE  TRUE 
    ##  7794  4139

``` r
# age: put into categories
table(demo$RIDAGEYR)
```

    ## 
    ##   0   1   2   3   4   5   6   7   8   9  10  11  12  13  14  15  16  17  18  19 
    ## 189 179 193 201 229 246 205 204 257 223 219 200 228 223 218 218 184 164 184 160 
    ##  20  21  22  23  24  25  26  27  28  29  30  31  32  33  34  35  36  37  38  39 
    ##  71  84  85  82  85  96  85 106  96 114 121 124 120 139 126 109 102 112 107 120 
    ##  40  41  42  43  44  45  46  47  48  49  50  51  52  53  54  55  56  57  58  59 
    ## 124 114 102 120 120  95 105  76  93  93 100 115 108 114  90 122  95 134 149 152 
    ##  60  61  62  63  64  65  66  67  68  69  70  71  72  73  74  75  76  77  78  79 
    ## 189 193 188 174 174 179 145 181 193 149 187 159 145 154 103 123 104  84  73  82 
    ##  80 
    ## 525

``` r
table(is.na(demo$RIDAGEYR))
```

    ## 
    ## FALSE 
    ## 11933

``` r
hist(demo$RIDAGEYR)
```

![](Final_DM_by_Education_files/figure-gfm/variables-1.png)<!-- -->

``` r
describe(demo$RIDAGEYR)
```

    ## demo$RIDAGEYR : Age in years at screening 
    ##        n  missing distinct     Info     Mean  pMedian      Gmd      .05 
    ##    11933        0       81        1    38.32     38.5    29.43        3 
    ##      .10      .25      .50      .75      .90      .95 
    ##        5       13       37       62       73       79 
    ## 
    ## lowest :  0  1  2  3  4, highest: 76 77 78 79 80

``` r
# gender/sex
table(demo$RIAGENDR)
```

    ## 
    ##    1    2 
    ## 5575 6358

``` r
table(is.na(demo$RIAGENDR))
```

    ## 
    ## FALSE 
    ## 11933

``` r
hist(demo$RIAGENDR)
```

![](Final_DM_by_Education_files/figure-gfm/variables-2.png)<!-- -->

``` r
describe(demo$RIAGENDR)
```

    ## demo$RIAGENDR : Gender 
    ##        n  missing distinct     Info     Mean 
    ##    11933        0        2    0.747    1.533 
    ##                       
    ## Value          1     2
    ## Frequency   5575  6358
    ## Proportion 0.467 0.533

``` r
# race/eth = demo$RIDRETH1
table(demo$RIDRETH1)
```

    ## 
    ##    1    2    3    4    5 
    ## 1117 1373 6217 1597 1629

``` r
table(is.na(demo$RIDRETH1))
```

    ## 
    ## FALSE 
    ## 11933

``` r
hist(demo$RIDRETH1)
```

![](Final_DM_by_Education_files/figure-gfm/variables-3.png)<!-- -->

``` r
describe(demo$RIDRETH1)
```

    ## demo$RIDRETH1 : Race/Hispanic origin 
    ##        n  missing distinct     Info     Mean  pMedian      Gmd 
    ##    11933        0        5    0.851    3.105        3     1.13 
    ##                                         
    ## Value          1     2     3     4     5
    ## Frequency   1117  1373  6217  1597  1629
    ## Proportion 0.094 0.115 0.521 0.134 0.137
    ## 
    ## For the frequency table, variable is rounded to the nearest 0

``` r
# family income ratio = demo$INDFMPIR 
table(demo$INDFMPIR)
```

    ## 
    ##    0 0.01 0.02 0.03 0.04 0.05 0.06 0.07 0.08 0.09  0.1 0.11 0.12 0.13 0.14 0.15 
    ##  100   22   29   26   17   23   15   12    8   11   15   14    8    5    8    6 
    ## 0.16 0.17 0.18 0.19  0.2 0.21 0.22 0.23 0.24 0.25 0.26 0.27 0.28 0.29  0.3 0.31 
    ##   12    8    9    9    9    7    3   25   10   11    8   16    5    7   25    8 
    ## 0.32 0.33 0.34 0.35 0.36 0.37 0.38 0.39  0.4 0.41 0.42 0.43 0.44 0.45 0.46 0.47 
    ##   12   13   10   13   10   18   13    6   15   14    9   29    8   20   24    8 
    ## 0.48 0.49  0.5 0.51 0.52 0.53 0.54 0.55 0.56 0.57 0.58 0.59  0.6 0.61 0.62 0.63 
    ##   34   15    9    6   34    6    7   26    9   27   39    4    5   28   40   25 
    ## 0.64 0.65 0.66 0.67 0.68 0.69  0.7 0.71 0.72 0.73 0.74 0.75 0.76 0.77 0.78 0.79 
    ##    4   39   34   13   26   28   26   13   22   15   49   26   12   40    8   40 
    ##  0.8 0.81 0.82 0.83 0.84 0.85 0.86 0.87 0.88 0.89  0.9 0.91 0.92 0.93 0.94 0.95 
    ##   22   27   41   25   26   24   22   31   54   15    6   28   29   19   20    8 
    ## 0.96 0.97 0.98 0.99    1 1.01 1.02 1.03 1.04 1.05 1.06 1.07 1.08 1.09  1.1 1.11 
    ##   39   30   23   27   22   53   20   37   15   45   18   27   28   53   32    4 
    ## 1.12 1.13 1.14 1.15 1.16 1.17 1.18 1.19  1.2 1.21 1.22 1.23 1.24 1.25 1.26 1.27 
    ##   23   35   34   25   23   27   17   12   15   18   18   34   10   17   34   10 
    ## 1.28 1.29  1.3 1.31 1.32 1.33 1.34 1.35 1.36 1.37 1.38 1.39  1.4 1.41 1.42 1.43 
    ##    9   16   46   26   34   12   25    4    2   58    9   22   21   31   31    5 
    ## 1.44 1.46 1.47 1.48 1.49  1.5 1.51 1.52 1.53 1.54 1.55 1.56 1.57 1.58 1.59  1.6 
    ##   30   16   35   18   20    2   38   31   11   20   32    6   19   13   11   14 
    ## 1.61 1.62 1.63 1.64 1.65 1.66 1.67 1.68 1.69  1.7 1.71 1.72 1.73 1.74 1.75 1.76 
    ##   36   27    1   26   17    5   40   11   31   10   56   21    3   23   25    5 
    ## 1.77 1.78 1.79  1.8 1.81 1.82 1.83 1.84 1.85 1.86 1.87 1.88 1.89  1.9 1.91 1.92 
    ##   28   14    2   46   10   16   10   25   74   22    3    4   14    8   45   11 
    ## 1.93 1.94 1.95 1.96 1.97 1.98 1.99    2 2.01 2.02 2.03 2.04 2.05 2.06 2.07 2.08 
    ##   10   20   16    5   24   17   35   21    9   13   30    4   20   29    8   10 
    ## 2.09  2.1 2.11 2.12 2.13 2.14 2.15 2.16 2.17 2.18 2.19  2.2 2.21 2.22 2.23 2.24 
    ##   21   12   11    9   26    1   15   64   32   38   18    3   37    5    2    4 
    ## 2.25 2.26 2.27 2.28 2.29  2.3 2.31 2.32 2.33 2.34 2.35 2.36 2.37 2.38 2.39  2.4 
    ##    8   18    2   30   17   11   30   11   32   21    7    9    2    4   25   26 
    ## 2.41 2.42 2.43 2.44 2.45 2.46 2.47 2.48 2.49  2.5 2.51 2.52 2.53 2.54 2.55 2.56 
    ##   24   13   22    3    4   29   15   25    6   25    6   14    4   22    3   19 
    ## 2.57 2.58 2.59 2.61 2.62 2.63 2.64 2.65 2.66 2.67 2.68 2.69  2.7 2.71 2.72 2.73 
    ##   10   42    5   51   15    3    7    9    5   15    6   15   13    9    9   43 
    ## 2.74 2.75 2.76 2.77 2.78 2.79  2.8 2.81 2.82 2.83 2.84 2.85 2.86 2.87 2.88 2.89 
    ##   37    8    4   37   16   16   10   10   21   26    6   36   15   28   29    4 
    ##  2.9 2.91 2.92 2.93 2.94 2.95 2.96 2.98    3 3.01 3.02 3.03 3.04 3.06 3.07 3.08 
    ##    1    2   36    5   31   11   16   11   37    2   25    2   42   20    3   27 
    ## 3.09  3.1 3.11 3.12 3.13 3.14 3.15 3.16 3.17 3.18 3.19 3.21 3.22 3.23 3.24 3.25 
    ##   25    2   14    3   26   10    6   15   14    1   11    3   27   10   18    3 
    ## 3.26 3.27 3.28 3.29  3.3 3.31 3.32 3.33 3.34 3.35 3.36 3.37 3.38 3.39  3.4 3.41 
    ##   23    9   44    8   31   15    2   32    5    4    7    7   12    6    9   16 
    ## 3.42 3.43 3.44 3.45 3.46 3.47 3.49  3.5 3.52 3.53 3.54 3.55 3.56 3.57 3.58  3.6 
    ##   57   24   14    6    6   26   10    3    3   11    5   38    4   10   21   48 
    ## 3.61 3.62 3.64 3.65 3.66 3.67 3.68 3.69  3.7 3.71 3.72 3.73 3.74 3.75 3.76 3.77 
    ##    1    8    3    4    2    4   23   34   12    5    5    5    2    6    9   19 
    ## 3.78  3.8 3.82 3.83 3.84 3.85 3.86 3.87 3.88 3.89  3.9 3.91 3.92 3.93 3.94 3.96 
    ##    5   16   30    8    5    2    3   13    6    3    9   17    5    6    4   25 
    ## 3.97 3.98 3.99    4 4.01 4.02 4.03 4.04 4.05 4.06 4.08  4.1 4.11 4.12 4.13 4.14 
    ##   15    2    5   23    2   24    6    5   19   19    1   30    5   35    5    6 
    ## 4.15 4.16 4.17 4.18 4.19 4.21 4.22 4.23 4.25 4.26 4.27 4.28 4.29  4.3 4.31 4.32 
    ##    6    3   12    4    3    4   11    5    7    5   19    1    3    6   25   39 
    ## 4.33 4.34 4.35 4.36 4.37 4.38  4.4 4.41 4.42 4.43 4.44 4.45 4.46 4.48 4.49  4.5 
    ##   21   26    1    3   32    2    6    7   30   10    9    9   18    6    2   14 
    ## 4.51 4.53 4.54 4.55 4.56 4.57 4.59  4.6 4.61 4.62 4.63 4.64 4.66 4.67 4.68 4.69 
    ##    2   11    3    9   30    1   13    6    3    9    5   16    7   15   24    3 
    ##  4.7 4.71 4.72 4.73 4.75 4.78  4.8 4.81 4.82 4.83 4.86 4.87 4.88 4.89  4.9 4.91 
    ##    1    4    4    3    2   23   14    1   13   16    9    1    9    2    4    2 
    ## 4.92 4.93 4.94 4.95 4.97 4.99    5 
    ##   23   16    8    1    7    2 2149

``` r
table(is.na(demo$INDFMPIR))
```

    ## 
    ## FALSE  TRUE 
    ##  9892  2041

``` r
hist(demo$INDFMPIR)
```

![](Final_DM_by_Education_files/figure-gfm/variables-4.png)<!-- -->

``` r
describe(demo$INDFMPIR)
```

    ## demo$INDFMPIR : Ratio of family income to poverty 
    ##        n  missing distinct     Info     Mean  pMedian      Gmd      .05 
    ##     9892     2041      471     0.99    2.708     2.74    1.908     0.32 
    ##      .10      .25      .50      .75      .90      .95 
    ##     0.62     1.18     2.50     4.50     5.00     5.00 
    ## 
    ## lowest : 0    0.01 0.02 0.03 0.04, highest: 4.94 4.95 4.97 4.99 5

``` r
# physical activity
str(phys)
```

    ## tibble [8,153 × 8] (S3: tbl_df/tbl/data.frame)
    ##  $ SEQN   : num [1:8153] 130378 130379 130380 130384 130385 ...
    ##   ..- attr(*, "label")= chr "Respondent sequence number"
    ##  $ PAD790Q: num [1:8153] 3 4 1 0 1 1 0 5 3 1 ...
    ##   ..- attr(*, "label")= chr "Frequency of moderate LTPA"
    ##  $ PAD790U: chr [1:8153] "W" "W" "W" "" ...
    ##   ..- attr(*, "label")= chr "Moderate LTPA unit (day/week/month/year)"
    ##  $ PAD800 : num [1:8153] 45 45 20 NA 90 30 NA 180 45 60 ...
    ##   ..- attr(*, "label")= chr "Minutes moderate LTPA"
    ##  $ PAD810Q: num [1:8153] 3 3 0 0 1 1 0 0 2 0 ...
    ##   ..- attr(*, "label")= chr "Frequency of vigorous LTPA"
    ##  $ PAD810U: chr [1:8153] "W" "W" "" "" ...
    ##   ..- attr(*, "label")= chr "Vigorous LTPA unit (day/week/month/year)"
    ##  $ PAD820 : num [1:8153] 45 45 NA NA 60 30 NA NA 30 NA ...
    ##   ..- attr(*, "label")= chr "Minutes vigorous LTPA"
    ##  $ PAD680 : num [1:8153] 360 480 240 60 180 180 1200 360 720 300 ...
    ##   ..- attr(*, "label")= chr "Minutes sedentary activity"
    ##  - attr(*, "label")= chr "Physical Activity"

``` r
# frequency of moderate
table(phys$PAD790Q)
```

    ## 
    ##    0    1    2    3    4    5    6    7    8   10   12   14   15   20   21   22 
    ## 1696 1343 1356 1416  719  722  211  524   10   28   12    2   15   13    2    1 
    ##   24   25   28   29   30   40   50  104  180 7777 9999 
    ##    2    1    1    1    6    2    1    1    1   10   39

``` r
table(is.na(phys$PAD790Q))
```

    ## 
    ## FALSE  TRUE 
    ##  8135    18

``` r
hist(phys$PAD790Q)
```

![](Final_DM_by_Education_files/figure-gfm/variables-5.png)<!-- -->

``` r
describe(phys$PAD790Q)
```

    ## phys$PAD790Q : Frequency of moderate LTPA 
    ##        n  missing distinct     Info     Mean  pMedian      Gmd      .05 
    ##     8135       18       27    0.975    60.14      2.5    116.9        0 
    ##      .10      .25      .50      .75      .90      .95 
    ##        0        1        2        4        6        7 
    ## 
    ## lowest :    0    1    2    3    4, highest:   50  104  180 7777 9999

``` r
# minutes of moderate 
table(phys$PAD800)
```

    ## 
    ##    1    2    3    4    5    6    7    8   10   11   12   14   15   16   18   20 
    ##   20    8    8    2   52    4    3    1  119    2    2    1  250    2    1  378 
    ##   21   23   24   25   27   29   30   31   35   36   37   39   40   45   49   50 
    ##    1    2    1   50    1    1 1504    1   30    2    1    1  158  550    1   24 
    ##   55   60   65   70   75   80   90   95  100  105  110  115  120  150  180  240 
    ##    3 1797    3    6   30    5  285    1    3    4    2    1  663   10  172   96 
    ##  300  360  420  480  540  600  660  720 9999 
    ##   56   24    4   14    1    5    1    4   19

``` r
table(is.na(phys$PAD800))
```

    ## 
    ## FALSE  TRUE 
    ##  6390  1763

``` r
hist(phys$PAD800)
```

![](Final_DM_by_Education_files/figure-gfm/variables-6.png)<!-- -->

``` r
describe(phys$PAD800)
```

    ## phys$PAD800 : Minutes moderate LTPA 
    ##        n  missing distinct     Info     Mean  pMedian      Gmd      .05 
    ##     6390     1763       57    0.963    93.44     52.5    110.3       15 
    ##      .10      .25      .50      .75      .90      .95 
    ##       20       30       60       60      120      180 
    ## 
    ## lowest :    1    2    3    4    5, highest:  540  600  660  720 9999

``` r
# frequency of vigorous exercise 
table(phys$PAD810Q)
```

    ## 
    ##    0    1    2    3    4    5    6    7    8    9   10   12   15   20   22   23 
    ## 4413 1286 1054  641  294  209   83   87    4    2    9    1    4    2    1    1 
    ##   24   30   31   84   90  200 7777 9999 
    ##    2    2    1    1    1    1    4   36

``` r
table(is.na(phys$PAD810Q))
```

    ## 
    ## FALSE  TRUE 
    ##  8139    14

``` r
hist(phys$PAD810Q)
```

![](Final_DM_by_Education_files/figure-gfm/variables-7.png)<!-- -->

``` r
describe(phys$PAD810Q)
```

    ## phys$PAD810Q : Frequency of vigorous LTPA 
    ##        n  missing distinct     Info     Mean  pMedian      Gmd      .05 
    ##     8139       14       24    0.834    49.21        1    97.29        0 
    ##      .10      .25      .50      .75      .90      .95 
    ##        0        0        0        2        3        5 
    ## 
    ## lowest :    0    1    2    3    4, highest:   84   90  200 7777 9999

``` r
#minutes of vigorous ex
table(phys$PAD820)
```

    ## 
    ##    1    2    3    4    5    6    7    8   10   12   15   20   25   30   32   35 
    ##   12    3    6    2   36    2    1    2  108    5  190  212   30  909    1   12 
    ##   40   45   46   50   55   60   70   75   90  100  105  120  150  180  240  300 
    ##   70  262    1   19    3 1064    5   13  145    2    3  364    4   93   49   21 
    ##  360  420  480  540  600  660  900 7777 9999 
    ##   10    1    8    1    1    1    2    1   13

``` r
table(is.na(phys$PAD820))
```

    ## 
    ## FALSE  TRUE 
    ##  3687  4466

``` r
hist(phys$PAD820)
```

![](Final_DM_by_Education_files/figure-gfm/variables-8.png)<!-- -->

``` r
describe(phys$PAD820)
```

    ## phys$PAD820 : Minutes vigorous LTPA 
    ##        n  missing distinct     Info     Mean  pMedian      Gmd      .05 
    ##     3687     4466       41    0.959    97.57     46.5    122.5       15 
    ##      .10      .25      .50      .75      .90      .95 
    ##       20       30       45       60      120      180 
    ## 
    ## lowest :    1    2    3    4    5, highest:  600  660  900 7777 9999

``` r
#diabetes
str(diabetes)
```

    ## tibble [11,744 × 9] (S3: tbl_df/tbl/data.frame)
    ##  $ SEQN   : num [1:11744] 130378 130379 130380 130381 130382 ...
    ##   ..- attr(*, "label")= chr "Respondent sequence number"
    ##  $ DIQ010 : num [1:11744] 2 2 1 2 2 2 2 2 2 2 ...
    ##   ..- attr(*, "label")= chr "Doctor told you have diabetes"
    ##  $ DID040 : num [1:11744] NA NA 35 NA NA NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "Age when first told you had diabetes"
    ##  $ DIQ160 : num [1:11744] 2 2 NA NA NA NA 2 1 2 2 ...
    ##   ..- attr(*, "label")= chr "Ever told you have prediabetes"
    ##  $ DIQ180 : num [1:11744] 2 1 NA NA NA NA 2 1 2 2 ...
    ##   ..- attr(*, "label")= chr "Had blood tested past three years"
    ##  $ DIQ050 : num [1:11744] NA NA 2 NA NA NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "Taking insulin now"
    ##  $ DID060 : num [1:11744] NA NA NA NA NA NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "How long taking insulin"
    ##  $ DIQ060U: num [1:11744] NA NA NA NA NA NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "Unit of measure (month/year)"
    ##  $ DIQ070 : num [1:11744] NA NA 1 NA NA NA NA 2 NA NA ...
    ##   ..- attr(*, "label")= chr "Take diabetic pills to lower blood sugar"
    ##  - attr(*, "label")= chr "Diabetes"

``` r
table(diabetes$DIQ010)
```

    ## 
    ##     1     2     3     9 
    ##  1081 10371   284     4

``` r
table(is.na(diabetes$DIQ010))
```

    ## 
    ## FALSE  TRUE 
    ## 11740     4

``` r
hist(diabetes$DIQ010)
```

![](Final_DM_by_Education_files/figure-gfm/variables-9.png)<!-- -->

``` r
describe(diabetes$DIQ010)
```

    ## diabetes$DIQ010 : Doctor told you have diabetes 
    ##        n  missing distinct     Info     Mean  pMedian      Gmd 
    ##    11740        4        4     0.31    1.934        2   0.2192 
    ##                                   
    ## Value          1     2     3     9
    ## Frequency   1081 10371   284     4
    ## Proportion 0.092 0.883 0.024 0.000
    ## 
    ## For the frequency table, variable is rounded to the nearest 0

``` r
#-diabetes
table(diabetes$DIQ160)
```

    ## 
    ##    1    2    9 
    ##  918 7089   15

``` r
table(is.na(diabetes$DIQ160))
```

    ## 
    ## FALSE  TRUE 
    ##  8022  3722

``` r
hist(diabetes$DIQ160)
```

![](Final_DM_by_Education_files/figure-gfm/variables-10.png)<!-- -->

``` r
describe(diabetes$DIQ160)
```

    ## diabetes$DIQ160 : Ever told you have prediabetes 
    ##        n  missing distinct     Info     Mean  pMedian      Gmd 
    ##     8022     3722        3    0.308    1.899        2   0.2288 
    ##                             
    ## Value          1     2     9
    ## Frequency    918  7089    15
    ## Proportion 0.114 0.884 0.002
    ## 
    ## For the frequency table, variable is rounded to the nearest 0

# merge all files

\#cleaning missing for all

    ##  [1] "SEQN"     "SDDSRVYR" "RIDSTATR" "RIAGENDR" "RIDAGEYR" "RIDAGEMN"
    ##  [7] "RIDRETH1" "RIDRETH3" "RIDEXMON" "RIDEXAGM" "DMQMILIZ" "DMDBORN4"
    ## [13] "DMDYRUSR" "DMDEDUC2" "DMDMARTZ" "RIDEXPRG" "DMDHHSIZ" "DMDHRGND"
    ## [19] "DMDHRAGZ" "DMDHREDZ" "DMDHRMAZ" "DMDHSEDZ" "WTINT2YR" "WTMEC2YR"
    ## [25] "SDMVSTRA" "SDMVPSU"  "INDFMPIR"

    ##       SEQN           DMDEDUC2        RIDAGEYR        RIAGENDR    
    ##  Min.   :130378   Min.   :1.000   Min.   : 0.00   Min.   :1.000  
    ##  1st Qu.:133361   1st Qu.:3.000   1st Qu.:13.00   1st Qu.:1.000  
    ##  Median :136344   Median :4.000   Median :37.00   Median :2.000  
    ##  Mean   :136344   Mean   :3.805   Mean   :38.32   Mean   :1.533  
    ##  3rd Qu.:139327   3rd Qu.:5.000   3rd Qu.:62.00   3rd Qu.:2.000  
    ##  Max.   :142310   Max.   :9.000   Max.   :80.00   Max.   :2.000  
    ##                   NA's   :4139                                   
    ##     RIDRETH3        INDFMPIR        PAD790Q          PAD790U         
    ##  Min.   :1.000   Min.   :0.000   Min.   :   0.00   Length:11933      
    ##  1st Qu.:3.000   1st Qu.:1.180   1st Qu.:   1.00   Class :character  
    ##  Median :3.000   Median :2.500   Median :   2.00   Mode  :character  
    ##  Mean   :3.321   Mean   :2.708   Mean   :  60.14                     
    ##  3rd Qu.:4.000   3rd Qu.:4.500   3rd Qu.:   4.00                     
    ##  Max.   :7.000   Max.   :5.000   Max.   :9999.00                     
    ##                  NA's   :2041    NA's   :3798                        
    ##      PAD800           PAD810Q          PAD810U              PAD820       
    ##  Min.   :   1.00   Min.   :   0.00   Length:11933       Min.   :   1.00  
    ##  1st Qu.:  30.00   1st Qu.:   0.00   Class :character   1st Qu.:  30.00  
    ##  Median :  60.00   Median :   0.00   Mode  :character   Median :  45.00  
    ##  Mean   :  93.44   Mean   :  49.21                      Mean   :  97.57  
    ##  3rd Qu.:  60.00   3rd Qu.:   2.00                      3rd Qu.:  60.00  
    ##  Max.   :9999.00   Max.   :9999.00                      Max.   :9999.00  
    ##  NA's   :5543      NA's   :3794                         NA's   :8246     
    ##      PAD680    
    ##  Min.   :   0  
    ##  1st Qu.: 180  
    ##  Median : 300  
    ##  Mean   : 447  
    ##  3rd Qu.: 480  
    ##  Max.   :9999  
    ##  NA's   :3795

    ##  [1] "SEQN"     "DMDEDUC2" "RIDAGEYR" "RIAGENDR" "RIDRETH3" "INDFMPIR"
    ##  [7] "ALQ111"   "ALQ121"   "ALQ130"   "ALQ142"   "ALQ270"   "ALQ280"  
    ## [13] "ALQ151"   "ALQ170"

    ##       SEQN           DMDEDUC2        RIDAGEYR        RIAGENDR    
    ##  Min.   :130378   Min.   :1.000   Min.   : 0.00   Min.   :1.000  
    ##  1st Qu.:133361   1st Qu.:3.000   1st Qu.:13.00   1st Qu.:1.000  
    ##  Median :136344   Median :4.000   Median :37.00   Median :2.000  
    ##  Mean   :136344   Mean   :3.805   Mean   :38.32   Mean   :1.533  
    ##  3rd Qu.:139327   3rd Qu.:5.000   3rd Qu.:62.00   3rd Qu.:2.000  
    ##  Max.   :142310   Max.   :9.000   Max.   :80.00   Max.   :2.000  
    ##                   NA's   :4139                                   
    ##     RIDRETH3        INDFMPIR         ALQ111          ALQ121      
    ##  Min.   :1.000   Min.   :0.000   Min.   :1.000   Min.   : 0.000  
    ##  1st Qu.:3.000   1st Qu.:1.180   1st Qu.:1.000   1st Qu.: 2.000  
    ##  Median :3.000   Median :2.500   Median :1.000   Median : 5.000  
    ##  Mean   :3.321   Mean   :2.708   Mean   :1.109   Mean   : 5.031  
    ##  3rd Qu.:4.000   3rd Qu.:4.500   3rd Qu.:1.000   3rd Qu.: 8.000  
    ##  Max.   :7.000   Max.   :5.000   Max.   :9.000   Max.   :99.000  
    ##                  NA's   :2041    NA's   :6452    NA's   :7011    
    ##      ALQ130            ALQ142           ALQ270           ALQ280      
    ##  Min.   :  1.000   Min.   : 0.000   Min.   : 0.000   Min.   : 0.000  
    ##  1st Qu.:  1.000   1st Qu.: 0.000   1st Qu.: 0.000   1st Qu.: 0.000  
    ##  Median :  2.000   Median : 4.000   Median : 4.000   Median : 0.000  
    ##  Mean   :  5.843   Mean   : 4.742   Mean   : 4.838   Mean   : 3.545  
    ##  3rd Qu.:  3.000   3rd Qu.: 9.000   3rd Qu.: 9.000   3rd Qu.: 7.000  
    ##  Max.   :999.000   Max.   :99.000   Max.   :99.000   Max.   :99.000  
    ##  NA's   :7864      NA's   :7851     NA's   :9567     NA's   :9571    
    ##      ALQ151          ALQ170       
    ##  Min.   :1.000   Min.   :  0.000  
    ##  1st Qu.:2.000   1st Qu.:  0.000  
    ##  Median :2.000   Median :  1.000  
    ##  Mean   :1.821   Mean   :  4.396  
    ##  3rd Qu.:2.000   3rd Qu.:  2.000  
    ##  Max.   :9.000   Max.   :999.000  
    ##  NA's   :7032    NA's   :9575

    ##       SEQN           DMDEDUC2        RIDAGEYR        RIAGENDR    
    ##  Min.   :130378   Min.   :1.000   Min.   : 0.00   Min.   :1.000  
    ##  1st Qu.:133361   1st Qu.:3.000   1st Qu.:13.00   1st Qu.:1.000  
    ##  Median :136344   Median :4.000   Median :37.00   Median :2.000  
    ##  Mean   :136344   Mean   :3.805   Mean   :38.32   Mean   :1.533  
    ##  3rd Qu.:139327   3rd Qu.:5.000   3rd Qu.:62.00   3rd Qu.:2.000  
    ##  Max.   :142310   Max.   :9.000   Max.   :80.00   Max.   :2.000  
    ##                   NA's   :4139                                   
    ##     RIDRETH3        INDFMPIR         ALQ111          ALQ121      
    ##  Min.   :1.000   Min.   :0.000   Min.   :1.000   Min.   : 0.000  
    ##  1st Qu.:3.000   1st Qu.:1.180   1st Qu.:1.000   1st Qu.: 2.000  
    ##  Median :3.000   Median :2.500   Median :1.000   Median : 5.000  
    ##  Mean   :3.321   Mean   :2.708   Mean   :1.109   Mean   : 5.031  
    ##  3rd Qu.:4.000   3rd Qu.:4.500   3rd Qu.:1.000   3rd Qu.: 8.000  
    ##  Max.   :7.000   Max.   :5.000   Max.   :9.000   Max.   :99.000  
    ##                  NA's   :2041    NA's   :6452    NA's   :7011    
    ##      ALQ130            ALQ142           ALQ270           ALQ280      
    ##  Min.   :  1.000   Min.   : 0.000   Min.   : 0.000   Min.   : 0.000  
    ##  1st Qu.:  1.000   1st Qu.: 0.000   1st Qu.: 0.000   1st Qu.: 0.000  
    ##  Median :  2.000   Median : 4.000   Median : 4.000   Median : 0.000  
    ##  Mean   :  5.843   Mean   : 4.742   Mean   : 4.838   Mean   : 3.545  
    ##  3rd Qu.:  3.000   3rd Qu.: 9.000   3rd Qu.: 9.000   3rd Qu.: 7.000  
    ##  Max.   :999.000   Max.   :99.000   Max.   :99.000   Max.   :99.000  
    ##  NA's   :7864      NA's   :7851     NA's   :9567     NA's   :9571    
    ##      ALQ151          ALQ170            DIQ010          DID040      
    ##  Min.   :1.000   Min.   :  0.000   Min.   :1.000   Min.   :  1.00  
    ##  1st Qu.:2.000   1st Qu.:  0.000   1st Qu.:2.000   1st Qu.: 40.00  
    ##  Median :2.000   Median :  1.000   Median :2.000   Median : 50.00  
    ##  Mean   :1.821   Mean   :  4.396   Mean   :1.935   Mean   : 70.02  
    ##  3rd Qu.:2.000   3rd Qu.:  2.000   3rd Qu.:2.000   3rd Qu.: 60.00  
    ##  Max.   :9.000   Max.   :999.000   Max.   :9.000   Max.   :999.00  
    ##  NA's   :7032    NA's   :9575      NA's   :193     NA's   :10852   
    ##      DIQ160          DIQ180          DIQ050          DID060      
    ##  Min.   :1.000   Min.   :1.000   Min.   :1.000   Min.   :  1.00  
    ##  1st Qu.:2.000   1st Qu.:1.000   1st Qu.:1.000   1st Qu.:  5.00  
    ##  Median :2.000   Median :2.000   Median :2.000   Median :  9.00  
    ##  Mean   :1.899   Mean   :1.819   Mean   :1.682   Mean   : 40.32  
    ##  3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.: 17.00  
    ##  Max.   :9.000   Max.   :9.000   Max.   :2.000   Max.   :999.00  
    ##  NA's   :3911    NA's   :3629    NA's   :10852   NA's   :11590   
    ##     DIQ060U          DIQ070     
    ##  Min.   :1.000   Min.   :1.000  
    ##  1st Qu.:2.000   1st Qu.:1.000  
    ##  Median :2.000   Median :2.000  
    ##  Mean   :1.895   Mean   :1.633  
    ##  3rd Qu.:2.000   3rd Qu.:2.000  
    ##  Max.   :2.000   Max.   :9.000  
    ##  NA's   :11601   NA's   :9652

    ##       SEQN           DMDEDUC2        RIDAGEYR        RIAGENDR    
    ##  Min.   :130378   Min.   :1.000   Min.   : 0.00   Min.   :1.000  
    ##  1st Qu.:133361   1st Qu.:3.000   1st Qu.:13.00   1st Qu.:1.000  
    ##  Median :136344   Median :4.000   Median :37.00   Median :2.000  
    ##  Mean   :136344   Mean   :3.805   Mean   :38.32   Mean   :1.533  
    ##  3rd Qu.:139327   3rd Qu.:5.000   3rd Qu.:62.00   3rd Qu.:2.000  
    ##  Max.   :142310   Max.   :9.000   Max.   :80.00   Max.   :2.000  
    ##                   NA's   :4139                                   
    ##     RIDRETH3        INDFMPIR         ALQ111          ALQ121      
    ##  Min.   :1.000   Min.   :0.000   Min.   :1.000   Min.   : 0.000  
    ##  1st Qu.:3.000   1st Qu.:1.180   1st Qu.:1.000   1st Qu.: 2.000  
    ##  Median :3.000   Median :2.500   Median :1.000   Median : 5.000  
    ##  Mean   :3.321   Mean   :2.708   Mean   :1.109   Mean   : 5.031  
    ##  3rd Qu.:4.000   3rd Qu.:4.500   3rd Qu.:1.000   3rd Qu.: 8.000  
    ##  Max.   :7.000   Max.   :5.000   Max.   :9.000   Max.   :99.000  
    ##                  NA's   :2041    NA's   :6452    NA's   :7011    
    ##      ALQ130            ALQ142           ALQ270           ALQ280      
    ##  Min.   :  1.000   Min.   : 0.000   Min.   : 0.000   Min.   : 0.000  
    ##  1st Qu.:  1.000   1st Qu.: 0.000   1st Qu.: 0.000   1st Qu.: 0.000  
    ##  Median :  2.000   Median : 4.000   Median : 4.000   Median : 0.000  
    ##  Mean   :  5.843   Mean   : 4.742   Mean   : 4.838   Mean   : 3.545  
    ##  3rd Qu.:  3.000   3rd Qu.: 9.000   3rd Qu.: 9.000   3rd Qu.: 7.000  
    ##  Max.   :999.000   Max.   :99.000   Max.   :99.000   Max.   :99.000  
    ##  NA's   :7864      NA's   :7851     NA's   :9567     NA's   :9571    
    ##      ALQ151          ALQ170            DIQ010          DID040      
    ##  Min.   :1.000   Min.   :  0.000   Min.   :1.000   Min.   :  1.00  
    ##  1st Qu.:2.000   1st Qu.:  0.000   1st Qu.:2.000   1st Qu.: 40.00  
    ##  Median :2.000   Median :  1.000   Median :2.000   Median : 50.00  
    ##  Mean   :1.821   Mean   :  4.396   Mean   :1.935   Mean   : 70.02  
    ##  3rd Qu.:2.000   3rd Qu.:  2.000   3rd Qu.:2.000   3rd Qu.: 60.00  
    ##  Max.   :9.000   Max.   :999.000   Max.   :9.000   Max.   :999.00  
    ##  NA's   :7032    NA's   :9575      NA's   :193     NA's   :10852   
    ##      DIQ160          DIQ180          DIQ050          DID060      
    ##  Min.   :1.000   Min.   :1.000   Min.   :1.000   Min.   :  1.00  
    ##  1st Qu.:2.000   1st Qu.:1.000   1st Qu.:1.000   1st Qu.:  5.00  
    ##  Median :2.000   Median :2.000   Median :2.000   Median :  9.00  
    ##  Mean   :1.899   Mean   :1.819   Mean   :1.682   Mean   : 40.32  
    ##  3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.: 17.00  
    ##  Max.   :9.000   Max.   :9.000   Max.   :2.000   Max.   :999.00  
    ##  NA's   :3911    NA's   :3629    NA's   :10852   NA's   :11590   
    ##     DIQ060U          DIQ070         PAD790Q          PAD790U         
    ##  Min.   :1.000   Min.   :1.000   Min.   :   0.00   Length:11933      
    ##  1st Qu.:2.000   1st Qu.:1.000   1st Qu.:   1.00   Class :character  
    ##  Median :2.000   Median :2.000   Median :   2.00   Mode  :character  
    ##  Mean   :1.895   Mean   :1.633   Mean   :  60.14                     
    ##  3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.:   4.00                     
    ##  Max.   :2.000   Max.   :9.000   Max.   :9999.00                     
    ##  NA's   :11601   NA's   :9652    NA's   :3798                        
    ##      PAD800           PAD810Q          PAD810U              PAD820       
    ##  Min.   :   1.00   Min.   :   0.00   Length:11933       Min.   :   1.00  
    ##  1st Qu.:  30.00   1st Qu.:   0.00   Class :character   1st Qu.:  30.00  
    ##  Median :  60.00   Median :   0.00   Mode  :character   Median :  45.00  
    ##  Mean   :  93.44   Mean   :  49.21                      Mean   :  97.57  
    ##  3rd Qu.:  60.00   3rd Qu.:   2.00                      3rd Qu.:  60.00  
    ##  Max.   :9999.00   Max.   :9999.00                      Max.   :9999.00  
    ##  NA's   :5543      NA's   :3794                         NA's   :8246     
    ##      PAD680    
    ##  Min.   :   0  
    ##  1st Qu.: 180  
    ##  Median : 300  
    ##  Mean   : 447  
    ##  3rd Qu.: 480  
    ##  Max.   :9999  
    ##  NA's   :3795

    ## tibble [11,933 × 29] (S3: tbl_df/tbl/data.frame)
    ##  $ SEQN    : num [1:11933] 130378 130379 130380 130381 130382 ...
    ##   ..- attr(*, "label")= chr "Respondent sequence number"
    ##  $ DMDEDUC2: num [1:11933] 5 5 3 NA NA NA 2 3 4 5 ...
    ##   ..- attr(*, "label")= chr "Education level - Adults 20+"
    ##  $ RIDAGEYR: num [1:11933] 43 66 44 5 2 3 43 65 34 68 ...
    ##   ..- attr(*, "label")= chr "Age in years at screening"
    ##  $ RIAGENDR: num [1:11933] 1 1 2 2 1 2 1 2 1 2 ...
    ##   ..- attr(*, "label")= chr "Gender"
    ##  $ RIDRETH3: num [1:11933] 6 3 2 7 3 2 1 3 1 3 ...
    ##   ..- attr(*, "label")= chr "Race/Hispanic origin w/ NH Asian"
    ##  $ INDFMPIR: num [1:11933] 5 5 1.41 1.53 3.6 NA 0.63 5 1.33 1.32 ...
    ##   ..- attr(*, "label")= chr "Ratio of family income to poverty"
    ##  $ ALQ111  : num [1:11933] NA 1 1 NA NA NA NA NA 1 1 ...
    ##   ..- attr(*, "label")= chr "Ever had a drink of any kind of alcohol"
    ##  $ ALQ121  : num [1:11933] NA 2 10 NA NA NA NA NA 4 0 ...
    ##   ..- attr(*, "label")= chr "Past 12 mos how often drink alc bev"
    ##  $ ALQ130  : num [1:11933] NA 3 1 NA NA NA NA NA 2 NA ...
    ##   ..- attr(*, "label")= chr "Avg # alcoholic drinks/day/past 12 mos"
    ##  $ ALQ142  : num [1:11933] NA 0 0 NA NA NA NA NA 10 NA ...
    ##   ..- attr(*, "label")= chr "# days have 4/5 drinks/past 12 mos"
    ##  $ ALQ270  : num [1:11933] NA NA NA NA NA NA NA NA 0 NA ...
    ##   ..- attr(*, "label")= chr "# times 4/5 drinks in 2hrs/past 12 mos"
    ##  $ ALQ280  : num [1:11933] NA NA NA NA NA NA NA NA 10 NA ...
    ##   ..- attr(*, "label")= chr "# times 8+ drinks in 1 day/past 12 mos"
    ##  $ ALQ151  : num [1:11933] NA 2 2 NA NA NA NA NA 2 2 ...
    ##   ..- attr(*, "label")= chr "Ever have 4/5 or more drinks every day"
    ##  $ ALQ170  : num [1:11933] NA NA NA NA NA NA NA NA 0 NA ...
    ##   ..- attr(*, "label")= chr "# times 4/5 drinks on occasion/past mo"
    ##  $ DIQ010  : num [1:11933] 2 2 1 2 2 2 2 2 2 2 ...
    ##   ..- attr(*, "label")= chr "Doctor told you have diabetes"
    ##  $ DID040  : num [1:11933] NA NA 35 NA NA NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "Age when first told you had diabetes"
    ##  $ DIQ160  : num [1:11933] 2 2 NA NA NA NA 2 1 2 2 ...
    ##   ..- attr(*, "label")= chr "Ever told you have prediabetes"
    ##  $ DIQ180  : num [1:11933] 2 1 NA NA NA NA 2 1 2 2 ...
    ##   ..- attr(*, "label")= chr "Had blood tested past three years"
    ##  $ DIQ050  : num [1:11933] NA NA 2 NA NA NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "Taking insulin now"
    ##  $ DID060  : num [1:11933] NA NA NA NA NA NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "How long taking insulin"
    ##  $ DIQ060U : num [1:11933] NA NA NA NA NA NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "Unit of measure (month/year)"
    ##  $ DIQ070  : num [1:11933] NA NA 1 NA NA NA NA 2 NA NA ...
    ##   ..- attr(*, "label")= chr "Take diabetic pills to lower blood sugar"
    ##  $ PAD790Q : num [1:11933] 3 4 1 NA NA NA 0 1 1 0 ...
    ##   ..- attr(*, "label")= chr "Frequency of moderate LTPA"
    ##  $ PAD790U : chr [1:11933] "W" "W" "W" NA ...
    ##   ..- attr(*, "label")= chr "Moderate LTPA unit (day/week/month/year)"
    ##  $ PAD800  : num [1:11933] 45 45 20 NA NA NA NA 90 30 NA ...
    ##   ..- attr(*, "label")= chr "Minutes moderate LTPA"
    ##  $ PAD810Q : num [1:11933] 3 3 0 NA NA NA 0 1 1 0 ...
    ##   ..- attr(*, "label")= chr "Frequency of vigorous LTPA"
    ##  $ PAD810U : chr [1:11933] "W" "W" "" NA ...
    ##   ..- attr(*, "label")= chr "Vigorous LTPA unit (day/week/month/year)"
    ##  $ PAD820  : num [1:11933] 45 45 NA NA NA NA NA 60 30 NA ...
    ##   ..- attr(*, "label")= chr "Minutes vigorous LTPA"
    ##  $ PAD680  : num [1:11933] 360 480 240 NA NA NA 60 180 180 1200 ...
    ##   ..- attr(*, "label")= chr "Minutes sedentary activity"
    ##  - attr(*, "label")= chr "Demographic Variables and Sample Weights"

    ##  [1] "SEQN"     "DMDEDUC2" "RIDAGEYR" "RIAGENDR" "RIDRETH3" "INDFMPIR"
    ##  [7] "ALQ111"   "ALQ121"   "ALQ130"   "ALQ142"   "ALQ270"   "ALQ280"  
    ## [13] "ALQ151"   "ALQ170"   "DIQ010"   "DID040"   "DIQ160"   "DIQ180"  
    ## [19] "DIQ050"   "DID060"   "DIQ060U"  "DIQ070"   "PAD790Q"  "PAD790U" 
    ## [25] "PAD800"   "PAD810Q"  "PAD810U"  "PAD820"   "PAD680"

    ## 
    ##     0     1  <NA> 
    ## 10371  1081   481

    ## 
    ##     0     1  <NA> 
    ## 10371  1081   481

    ## 
    ##    0    1    2    3    4    5    6    7    8   10   12   14   15   20   21   22 
    ## 1696 1343 1356 1416  719  722  211  524   10   28   12    2   15   13    2    1 
    ##   24   25   28   29   30   40   50  104  180 <NA> 
    ##    2    1    1    1    6    2    1    1    1 3847

    ## 
    ##    1    2    3    4    5    6    7    8   10   11   12   14   15   16   18   20 
    ##   20    8    8    2   52    4    3    1  119    2    2    1  250    2    1  378 
    ##   21   23   24   25   27   29   30   31   35   36   37   39   40   45   49   50 
    ##    1    2    1   50    1    1 1504    1   30    2    1    1  158  550    1   24 
    ##   55   60   65   70   75   80   90   95  100  105  110  115  120  150  180  240 
    ##    3 1797    3    6   30    5  285    1    3    4    2    1  663   10  172   96 
    ##  300  360  420  480  540  600  660  720 <NA> 
    ##   56   24    4   14    1    5    1    4 5562

    ## 
    ##    0    1    2    3    4    5    6    7    8    9   10   12   15   20   22   23 
    ## 4413 1286 1054  641  294  209   83   87    4    2    9    1    4    2    1    1 
    ##   24   30   31   84   90  200 <NA> 
    ##    2    2    1    1    1    1 3834

    ## 
    ##    1    2    3    4    5    6    7    8   10   12   15   20   25   30   32   35 
    ##   12    3    6    2   36    2    1    2  108    5  190  212   30  909    1   12 
    ##   40   45   46   50   55   60   70   75   90  100  105  120  150  180  240  300 
    ##   70  262    1   19    3 1064    5   13  145    2    3  364    4   93   49   21 
    ##  360  420  480  540  600  660  900 <NA> 
    ##   10    1    8    1    1    1    2 8260

    ## 
    ##         D    M    W    Y 
    ## 1763  985  472 4851   82

    ## 
    ## 0.0273972602739726 0.0333333333333333 0.0666666666666667 0.0821917808219178 
    ##                  2                  1                  1                  5 
    ##                0.1   0.10958904109589  0.123287671232877  0.164383561643836 
    ##                  1                  1                  1                  7 
    ##  0.166666666666667  0.205479452054795  0.219178082191781  0.246575342465753 
    ##                  5                  1                  1                  3 
    ##  0.285714285714286  0.328767123287671  0.333333333333333  0.410958904109589 
    ##                  2                  9                  5                  1 
    ##  0.428571428571429  0.466666666666667  0.493150684931507                0.5 
    ##                  8                  1                  7                  6 
    ##  0.547945205479452  0.571428571428571  0.616438356164384  0.657534246575342 
    ##                  2                  2                  2                  6 
    ##  0.666666666666667  0.714285714285714   0.73972602739726  0.821917808219178 
    ##                 12                  9                  2                  1 
    ##  0.833333333333333  0.857142857142857  0.933333333333333  0.986301369863014 
    ##                  1                  1                  1                  6 
    ##                  1                1.2   1.23287671232877   1.28571428571429 
    ##                 54                  1                  1                  4 
    ##   1.31506849315068   1.33333333333333   1.42857142857143                1.5 
    ##                  1                 14                 22                  4 
    ##   1.64383561643836   1.66666666666667   1.71428571428571   1.97260273972603 
    ##                  4                  4                  1                  1 
    ##                  2   2.14285714285714   2.33333333333333   2.46575342465753 
    ##                 71                 32                  1                  3 
    ##   2.46666666666667   2.57142857142857   2.66666666666667   2.85714285714286 
    ##                  1                  1                  3                 48 
    ##   2.95890410958904                  3   3.28767123287671   3.33333333333333 
    ##                  1                 32                  4                  2 
    ##                3.5   3.57142857142857   3.94520547945205                  4 
    ##                  1                  5                  1                 86 
    ##   4.10958904109589   4.28571428571429                4.5   4.57142857142857 
    ##                  1                220                  4                  1 
    ##   4.93150684931507                  5   5.14285714285714   5.71428571428571 
    ##                  1                 23                  2                 78 
    ##   5.83333333333333   5.91780821917808                  6   6.42857142857143 
    ##                  1                  1                 37                 77 
    ##   6.57534246575342                  7   7.14285714285714    7.3972602739726 
    ##                  1                  4                 17                  1 
    ##                7.5                  8   8.28571428571429   8.57142857142857 
    ##                  3                 28                  1                512 
    ##                  9   9.42857142857143   9.85714285714286   9.86301369863014 
    ##                  5                  1                  1                  1 
    ##                 10               10.5   10.7142857142857                 11 
    ##                 44                  2                 25                  1 
    ##   11.4285714285714                 12   12.8571428571429   14.2857142857143 
    ##                 50                 17                422                 42 
    ##                 15   15.7142857142857                 16   16.4285714285714 
    ##                 71                  1                 13                  1 
    ##   17.1428571428571   17.8571428571429                 18   19.2857142857143 
    ##                505                  9                  4                109 
    ##                 20                 21   21.4285714285714               22.5 
    ##                100                  2                139                  1 
    ##   22.8571428571429                 23                 24                 25 
    ##                 28                  1                  5                 15 
    ##   25.7142857142857   28.5714285714286   29.5890410958904                 30 
    ##                549                 24                  1                282 
    ##                 31   31.4285714285714                 32   32.1428571428571 
    ##                  1                  1                  3                 65 
    ##   34.2857142857143                 35   35.7142857142857                 36 
    ##                313                  5                  5                  1 
    ##   38.5714285714286                 40   42.8571428571429                 45 
    ##                 77                 49                214                116 
    ##   45.7142857142857   46.4285714285714                 48                 50 
    ##                  1                  1                  1                 17 
    ##   51.2876712328767   51.4285714285714   53.5714285714286                 55 
    ##                  1                249                  6                  1 
    ##                 56   57.1428571428571                 60   64.2857142857143 
    ##                  1                  2                298                 55 
    ##                 65   68.5714285714286                 70                 72 
    ##                  2                 95                  6                  1 
    ##                 75   77.1428571428571                 78                 80 
    ##                 11                 41                  1                  8 
    ##   85.7142857142857                 87                 90   94.2857142857143 
    ##                 66                  1                 74                  1 
    ##                 95                100   102.857142857143                105 
    ##                  1                 11                 59                  3 
    ##   107.142857142857   114.285714285714                120                125 
    ##                  2                  1                183                  1 
    ##   128.571428571429                135   137.142857142857                140 
    ##                 24                  5                 15                  1 
    ##                150   154.285714285714   157.142857142857                160 
    ##                  5                  9                  1                  1 
    ##   171.428571428571                175                180                200 
    ##                 20                  1                 80                  1 
    ##   205.714285714286                210   214.285714285714                220 
    ##                  6                  5                  7                  1 
    ##                225                240   257.142857142857                270 
    ##                  1                 36                 10                  1 
    ##   274.285714285714                300   308.571428571429                315 
    ##                  1                 20                  2                  1 
    ##   342.857142857143                350                360   377.142857142857 
    ##                  3                  1                 18                  1 
    ##   411.428571428571                420   428.571428571429                450 
    ##                  3                  5                  1                  1 
    ##   457.142857142857                480                540                600 
    ##                  1                 12                  2                  4 
    ##   617.142857142857                630   685.714285714286                720 
    ##                  1                  1                  1                  4 
    ##                840                900               <NA> 
    ##                  2                  5               5562

    ## 
    ## 0.0273972602739726 0.0328767123287671 0.0333333333333333 0.0410958904109589 
    ##                  1                  1                  1                  6 
    ## 0.0547945205479452 0.0657534246575342 0.0666666666666667 0.0821917808219178 
    ##                  2                  1                  1                 12 
    ##                0.1   0.10958904109589  0.123287671232877  0.136986301369863 
    ##                  2                  2                  3                  1 
    ##  0.142857142857143  0.164383561643836  0.166666666666667  0.219178082191781 
    ##                  4                 21                  7                  1 
    ##  0.246575342465753  0.266666666666667  0.273972602739726  0.285714285714286 
    ##                  4                  1                  1                  1 
    ##  0.328767123287671  0.333333333333333   0.36986301369863                0.4 
    ##                 12                 18                  1                  1 
    ##  0.410958904109589  0.466666666666667  0.493150684931507                0.5 
    ##                  3                  1                 14                 17 
    ##  0.657534246575342  0.666666666666667  0.714285714285714   0.73972602739726 
    ##                 11                 23                  9                  4 
    ##  0.821917808219178  0.833333333333333  0.986301369863014                  1 
    ##                  7                  2                  8                130 
    ##   1.23287671232877   1.28571428571429   1.31506849315068   1.33333333333333 
    ##                  1                  1                  3                 16 
    ##   1.42857142857143   1.47945205479452                1.5   1.64383561643836 
    ##                 28                  2                 16                  3 
    ##   1.66666666666667   1.71428571428571   1.89041095890411   1.97260273972603 
    ##                  1                  2                  1                  6 
    ##                  2   2.14285714285714    2.3013698630137   2.33333333333333 
    ##                148                 49                  1                  2 
    ##   2.46575342465753   2.63013698630137   2.66666666666667   2.85714285714286 
    ##                  1                  2                  8                 57 
    ##   2.95890410958904                  3   3.08219178082192   3.33333333333333 
    ##                  2                 40                  1                  3 
    ##   3.42857142857143   3.57142857142857   3.94520547945205                  4 
    ##                  3                  7                  1                117 
    ##   4.28571428571429                4.5   4.57142857142857                  5 
    ##                266                  1                  1                 12 
    ##   5.14285714285714   5.71428571428571                  6   6.42857142857143 
    ##                  1                 65                 32                 74 
    ##   6.57534246575342   7.14285714285714                7.5   7.85714285714286 
    ##                  1                 18                  1                  1 
    ##                  8   8.57142857142857                  9   9.86301369863014 
    ##                 49                485                  4                  1 
    ##                 10   10.7142857142857   11.0958904109589   11.4285714285714 
    ##                 20                 13                  1                 22 
    ##                 12   12.8571428571429   13.7142857142857   13.8082191780822 
    ##                 22                204                  1                  1 
    ##                 14   14.2857142857143   14.7945205479452                 15 
    ##                  2                 12                  1                 18 
    ##   15.7142857142857                 16   16.4383561643836   17.1428571428571 
    ##                  1                  7                  1                339 
    ##   17.8571428571429                 18   19.2857142857143                 20 
    ##                  1                  3                 50                 30 
    ##   21.4285714285714   22.8571428571429   23.5714285714286                 24 
    ##                 36                  5                  1                  7 
    ##                 25   25.7142857142857                 28   28.5714285714286 
    ##                  2                227                  2                  7 
    ##                 30                 32   32.1428571428571   32.8571428571429 
    ##                 51                  2                 20                  1 
    ##   34.2857142857143                 35   35.7142857142857   38.5714285714286 
    ##                153                  1                  2                 36 
    ##                 40   42.8571428571429                 44                 45 
    ##                 10                 54                  1                 15 
    ##                 48                 50   51.4285714285714   53.5714285714286 
    ##                  1                  2                 88                  5 
    ##                 60                 62   64.2857142857143   68.5714285714286 
    ##                 84                  1                 20                 41 
    ##                 70   71.4285714285714                 75   77.1428571428571 
    ##                  1                  1                  1                 10 
    ##                 80   85.7142857142857                 90                100 
    ##                  1                 21                 16                  2 
    ##   102.857142857143                120   128.571428571429                135 
    ##                 23                 26                  9                  2 
    ##   137.142857142857   154.285714285714   171.428571428571                180 
    ##                  2                  2                  1                 16 
    ##                225                240                250   257.142857142857 
    ##                  1                 14                  1                  2 
    ##   274.285714285714   282.857142857143                300                315 
    ##                  2                  1                  4                  1 
    ##   342.857142857143                360   385.714285714286   411.428571428571 
    ##                  1                  7                  1                  1 
    ##                420                480   642.857142857143                720 
    ##                  3                  1                  1                  4 
    ##                960               <NA> 
    ##                  1               8261

    ## 
    ## 0.0547945205479452 0.0657534246575342 0.0666666666666667 0.0821917808219178 
    ##                  1                  1                  1                  6 
    ##   0.10958904109589  0.131506849315068  0.133333333333333  0.164383561643836 
    ##                  2                  1                  1                 12 
    ##                0.2  0.219178082191781  0.246575342465753  0.273972602739726 
    ##                  2                  2                  3                  1 
    ##  0.285714285714286  0.328767123287671  0.333333333333333  0.438356164383562 
    ##                  4                 21                  7                  1 
    ##  0.493150684931507  0.533333333333333  0.547945205479452  0.571428571428571 
    ##                  4                  1                  1                  1 
    ##  0.657534246575342  0.666666666666667   0.73972602739726                0.8 
    ##                 12                 18                  1                  1 
    ##  0.821917808219178  0.933333333333333  0.986301369863014                  1 
    ##                  3                  1                 14                 17 
    ##   1.31506849315068   1.33333333333333   1.42857142857143   1.47945205479452 
    ##                 11                 23                  9                  4 
    ##   1.64383561643836   1.66666666666667   1.97260273972603                  2 
    ##                  7                  2                  8                130 
    ##   2.46575342465753   2.57142857142857   2.63013698630137   2.66666666666667 
    ##                  1                  1                  3                 16 
    ##   2.85714285714286   2.95890410958904                  3   3.28767123287671 
    ##                 28                  2                 16                  3 
    ##   3.33333333333333   3.42857142857143   3.78082191780822   3.94520547945205 
    ##                  1                  2                  1                  6 
    ##                  4   4.28571428571429    4.6027397260274   4.66666666666667 
    ##                148                 49                  1                  2 
    ##   4.93150684931507   5.26027397260274   5.33333333333333   5.71428571428571 
    ##                  1                  2                  8                 57 
    ##   5.91780821917808                  6   6.16438356164384   6.66666666666667 
    ##                  2                 40                  1                  3 
    ##   6.85714285714286   7.14285714285714   7.89041095890411                  8 
    ##                  3                  7                  1                117 
    ##   8.57142857142857                  9   9.14285714285714                 10 
    ##                266                  1                  1                 12 
    ##   10.2857142857143   11.4285714285714                 12   12.8571428571429 
    ##                  1                 65                 32                 74 
    ##   13.1506849315068   14.2857142857143                 15   15.7142857142857 
    ##                  1                 18                  1                  1 
    ##                 16   17.1428571428571                 18   19.7260273972603 
    ##                 49                485                  4                  1 
    ##                 20   21.4285714285714   22.1917808219178   22.8571428571429 
    ##                 20                 13                  1                 22 
    ##                 24   25.7142857142857   27.4285714285714   27.6164383561644 
    ##                 22                204                  1                  1 
    ##                 28   28.5714285714286   29.5890410958904                 30 
    ##                  2                 12                  1                 18 
    ##   31.4285714285714                 32   32.8767123287671   34.2857142857143 
    ##                  1                  7                  1                339 
    ##   35.7142857142857                 36   38.5714285714286                 40 
    ##                  1                  3                 50                 30 
    ##   42.8571428571429   45.7142857142857   47.1428571428571                 48 
    ##                 36                  5                  1                  7 
    ##                 50   51.4285714285714                 56   57.1428571428571 
    ##                  2                227                  2                  7 
    ##                 60                 64   64.2857142857143   65.7142857142857 
    ##                 51                  2                 20                  1 
    ##   68.5714285714286                 70   71.4285714285714   77.1428571428571 
    ##                153                  1                  2                 36 
    ##                 80   85.7142857142857                 88                 90 
    ##                 10                 54                  1                 15 
    ##                 96                100   102.857142857143   107.142857142857 
    ##                  1                  2                 88                  5 
    ##                120                124   128.571428571429   137.142857142857 
    ##                 84                  1                 20                 41 
    ##                140   142.857142857143                150   154.285714285714 
    ##                  1                  1                  1                 10 
    ##                160   171.428571428571                180                200 
    ##                  1                 21                 16                  2 
    ##   205.714285714286                240   257.142857142857                270 
    ##                 23                 26                  9                  2 
    ##   274.285714285714   308.571428571429   342.857142857143                360 
    ##                  2                  2                  1                 16 
    ##                450                480                500   514.285714285714 
    ##                  1                 14                  1                  2 
    ##   548.571428571429   565.714285714286                600                630 
    ##                  2                  1                  4                  1 
    ##   685.714285714286                720   771.428571428571   822.857142857143 
    ##                  1                  7                  1                  1 
    ##                840                960   1285.71428571429               1440 
    ##                  3                  1                  1                  4 
    ##               1920               <NA> 
    ##                  1               8261

    ## 
    ##                  0 0.0273972602739726 0.0666666666666667 0.0821917808219178 
    ##               5458                  2                  1                  4 
    ##                0.1  0.123287671232877  0.164383561643836  0.166666666666667 
    ##                  1                  1                  6                  3 
    ##  0.219178082191781  0.246575342465753   0.26027397260274  0.328767123287671 
    ##                  1                  2                  1                  7 
    ##  0.333333333333333  0.410958904109589  0.428571428571429  0.438356164383562 
    ##                  4                  2                  4                  1 
    ##  0.493150684931507                0.5  0.547945205479452  0.582191780821918 
    ##                  5                  7                  1                  1 
    ##  0.616438356164384   0.63013698630137  0.657534246575342  0.666666666666667 
    ##                  1                  1                  3                 13 
    ##  0.714285714285714   0.73972602739726  0.780821917808219  0.833333333333333 
    ##                  8                  2                  1                  1 
    ##  0.857142857142857  0.904109589041096   0.90958904109589  0.986301369863014 
    ##                  1                  1                  1                  6 
    ##                  1   1.13333333333333   1.16438356164384                1.2 
    ##                 38                  1                  1                  1 
    ##   1.23287671232877   1.28571428571429   1.33333333333333   1.41552511415525 
    ##                  1                  4                 12                  1 
    ##   1.42857142857143   1.47945205479452                1.5   1.53816046966732 
    ##                 20                  2                  3                  1 
    ##   1.64383561643836   1.66666666666667   1.86301369863014   1.96190476190476 
    ##                  3                  5                  1                  1 
    ##   1.97260273972603   1.98630136986301                  2   2.14285714285714 
    ##                  2                  1                 47                 20 
    ##   2.16438356164384   2.32876712328767   2.33333333333333   2.46575342465753 
    ##                  2                  1                  1                  3 
    ##   2.64840182648402   2.66666666666667   2.73972602739726   2.85714285714286 
    ##                  1                  5                  1                 34 
    ##   2.92289628180039   2.93333333333333   2.95890410958904                  3 
    ##                  1                  1                  1                 29 
    ##   3.02152641878669   3.14285714285714   3.28767123287671   3.32876712328767 
    ##                  1                  2                  2                  1 
    ##   3.33333333333333                3.5   3.52380952380952   3.57142857142857 
    ##                  2                  1                  1                  4 
    ##   3.84344422700587                  4   4.10958904109589   4.14285714285714 
    ##                  1                 59                  1                  3 
    ##   4.16438356164384   4.27397260273973   4.28571428571429   4.32876712328767 
    ##                  1                  1                139                  3 
    ##   4.33333333333333   4.35238095238095   4.49315068493151                4.5 
    ##                  1                  1                  1                  2 
    ##   4.57142857142857   4.61448140900196   4.61904761904762   4.65753424657534 
    ##                  2                  1                  1                  1 
    ##   4.76712328767123   4.85714285714286                  5    5.0958904109589 
    ##                  1                  5                 18                  1 
    ##   5.14285714285714    5.2720156555773   5.28571428571429   5.31506849315068 
    ##                  2                  1                  1                  1 
    ##   5.33333333333333   5.61904761904762   5.71428571428571    5.8238747553816 
    ##                  1                  4                 51                  1 
    ##                  6   6.04761904761905   6.08219178082192   6.25831702544031 
    ##                 37                  1                  1                  1 
    ##   6.28571428571429   6.38095238095238   6.42857142857143   6.71428571428571 
    ##                 10                  1                 54                  1 
    ##   6.85714285714286   6.98630136986301                  7   7.08610567514677 
    ##                  1                  2                  6                  1 
    ##   7.14285714285714   7.28571428571429   7.33333333333333   7.38095238095238 
    ##                 13                  1                  1                  1 
    ##   7.42857142857143                7.5   7.71428571428571   7.85714285714286 
    ##                  1                  1                  3                  1 
    ##   7.89041095890411                  8   8.09523809523809   8.28571428571428 
    ##                  1                 24                  1                  5 
    ##   8.28571428571429   8.32876712328767   8.38095238095238   8.42857142857143 
    ##                  1                  2                  3                  2 
    ##   8.57142857142857   8.66666666666667   8.73581213307241   8.85714285714286 
    ##                286                  1                  2                  2 
    ##   8.93150684931507   8.98630136986301                  9   9.06457925636008 
    ##                  1                  1                  7                  1 
    ##   9.14383561643836   9.22896281800391   9.28571428571429   9.39334637964775 
    ##                  1                  2                  1                  1 
    ##   9.42857142857143    9.5047619047619   9.53424657534246   9.54598825831702 
    ##                  1                  1                  1                  1 
    ##   9.55772994129159   9.57142857142857   9.64383561643836   9.71428571428572 
    ##                  4                  3                  1                  3 
    ##   9.85714285714286   9.86301369863014   9.88649706457926   9.90476190476191 
    ##                  1                  1                  1                  3 
    ##   9.97260273972603                 10   10.1666666666667   10.1917808219178 
    ##                  1                 39                  1                  1 
    ##   10.2152641878669   10.2857142857143   10.4285714285714               10.5 
    ##                  3                  1                  2                  2 
    ##   10.5714285714286   10.6575342465753   10.7142857142857   11.1428571428571 
    ##                 17                  1                 19                  1 
    ##   11.2015655577299   11.2380952380952   11.2876712328767   11.4285714285714 
    ##                  1                  3                  1                 36 
    ##   11.7142857142857   11.7573385518591   11.8095238095238   11.8333333333333 
    ##                  2                  1                  1                  1 
    ##   11.9452054794521                 12    12.047619047619   12.1428571428571 
    ##                  1                 13                  1                  1 
    ##   12.2857142857143   12.3522504892368   12.4285714285714   12.5714285714286 
    ##                  1                  1                  1                 18 
    ##   12.7142857142857   12.8571428571429   13.1037181996086   13.1859099804305 
    ##                  1                197                  2                  1 
    ##   13.1904761904762   13.3333333333333   13.4285714285714   13.5714285714286 
    ##                  1                  1                  1                  2 
    ##   13.8317025440313   13.9047619047619    13.972602739726                 14 
    ##                  1                  1                  1                  2 
    ##   14.0952380952381   14.1428571428571   14.1904761904762   14.2857142857143 
    ##                  1                  1                  3                 36 
    ##   14.3365949119374   14.5009784735812   14.5714285714286   14.8297455968689 
    ##                  1                  1                  5                  1 
    ##   14.8571428571429                 15   15.2191780821918   15.3287671232877 
    ##                 12                 45                  1                  1 
    ##   15.3333333333333   15.4285714285714   15.5238095238095   15.7142857142857 
    ##                  2                  4                  1                  6 
    ##   15.8571428571429                 16   16.1448140900196   16.1643835616438 
    ##                  3                 13                  1                  1 
    ##   16.2857142857143   16.3571428571429   16.4285714285714   16.4618395303327 
    ##                  1                  1                  1                  1 
    ##   16.5714285714286   16.8571428571429    16.972602739726   17.1428571428571 
    ##                 15                 13                  1                274 
    ##   17.3150684931507   17.3333333333333   17.5714285714286   17.6908023483366 
    ##                  1                  1                  1                  1 
    ##   17.8003913894325   17.8095238095238   17.8571428571429                 18 
    ##                  2                  5                  3                  4 
    ##   18.1428571428571   18.2857142857143   18.4285714285714   18.4579256360078 
    ##                  4                  3                  1                  4 
    ##   18.4931506849315   18.5714285714286   18.8571428571429   19.1428571428571 
    ##                  1                  7                  8                  9 
    ##   19.2857142857143   19.4285714285714   19.5238095238095   19.7260273972603 
    ##                 47                  2                  1                  1 
    ##   19.7729941291585   19.7788649706458   19.8095238095238   19.8571428571429 
    ##                  1                  1                  1                  2 
    ##                 20   20.1428571428571   20.2857142857143   20.3333333333333 
    ##                 69                  2                  2                  1 
    ##   20.4931506849315   20.5714285714286   20.6190476190476   20.6575342465753 
    ##                  1                  2                  3                  1 
    ##   20.6666666666667   20.7142857142857   20.8571428571429                 21 
    ##                  1                  1                  8                  1 
    ##   21.0880626223092   21.1428571428571   21.2857142857143   21.4285714285714 
    ##                  1                 15                  3                104 
    ##   21.6751467710372   21.7142857142857   21.8095238095238                 22 
    ##                  1                  1                  1                  2 
    ##   22.0952380952381   22.1428571428571   22.2857142857143   22.5714285714286 
    ##                  1                  3                  1                  1 
    ##   22.6666666666667   22.8571428571429   23.1428571428571   23.2857142857143 
    ##                  1                 25                  9                  5 
    ##   23.4285714285714   23.5714285714286                 24   24.1904761904762 
    ##                  3                  5                 10                  1 
    ##   24.2857142857143   24.5238095238095   24.5714285714286   24.8571428571429 
    ##                 10                  1                  5                  1 
    ##                 25   25.1428571428571   25.3737769080235   25.4285714285714 
    ##                 10                 15                  1                  6 
    ##   25.7142857142857   25.7964774951076   25.8571428571429                 26 
    ##                283                  1                  1                  1 
    ##   26.0430528375734   26.1428571428571   26.2857142857143   26.3718199608611 
    ##                  1                  2                  1                  1 
    ##   26.4285714285714   26.5362035225049   26.7005870841487   26.7142857142857 
    ##                  2                  1                  2                  1 
    ##   26.8571428571429                 27   27.1428571428571   27.2857142857143 
    ##                  1                  1                  3                  2 
    ##   27.3581213307241   27.4285714285714   27.6164383561644   27.7142857142857 
    ##                  1                  2                  1                  5 
    ##   27.8571428571429                 28   28.0952380952381   28.1428571428571 
    ##                 10                  3                  1                  1 
    ##   28.1800391389433   28.3333333333333   28.5714285714286   28.7142857142857 
    ##                  1                  1                 29                  1 
    ##   29.1428571428571   29.4285714285714   29.6594911937378   29.6917808219178 
    ##                  4                  2                  1                  1 
    ##   29.7142857142857   29.8571428571429                 30               30.2 
    ##                 13                  1                179                  1 
    ##   30.3287671232877   30.3333333333333   30.4666666666667   30.7142857142857 
    ##                  1                  1                  1                  1 
    ##   30.8571428571429                 31    31.047619047619   31.2857142857143 
    ##                  2                  1                  2                  1 
    ##   31.3333333333333   31.4285714285714   31.5714285714286   31.7142857142857 
    ##                  1                 15                  1                  4 
    ##                 32   32.1428571428571   32.6666666666667   32.8571428571429 
    ##                  9                 37                  4                 11 
    ##   33.1428571428571   33.2876712328767   33.4285714285714   33.7142857142857 
    ##                  1                  1                  1                 14 
    ##                 34   34.2857142857143   34.4500978473581    34.614481409002 
    ##                  7                217                  1                  1 
    ##   34.7142857142857   34.8571428571429   34.9523809523809                 35 
    ##                  3                  1                  1                  4 
    ##    35.600782778865   35.6190476190476   35.7142857142857   35.7651663405088 
    ##                  1                  1                  7                  1 
    ##   35.9295499021526    35.986301369863                 36   36.1428571428571 
    ##                  1                  1                  3                  2 
    ##   36.2857142857143   36.4285714285714   36.9158512720157   37.1428571428571 
    ##                  3                 14                  1                 19 
    ##   37.2446183953033   37.2857142857143   37.4285714285714   37.5890410958904 
    ##                  1                  2                  1                  1 
    ##   37.7142857142857   37.8571428571429                 38   38.1428571428571 
    ##                  3                  1                  6                  1 
    ##   38.2857142857143   38.5714285714286   39.1428571428571                 40 
    ##                  6                100                  1                 30 
    ##   40.0508806262231   40.2857142857143   40.5714285714286   40.6666666666667 
    ##                  1                  3                  1                  1 
    ##   40.7142857142857   41.1428571428571   41.4285714285714   41.7142857142857 
    ##                  7                  2                  4                  4 
    ##                 42   42.1428571428571   42.2857142857143   42.8571428571429 
    ##                  7                  2                  8                175 
    ##   43.5714285714286   43.7142857142857   44.2857142857143   44.5714285714286 
    ##                  1                  1                  3                  1 
    ##   44.8571428571429                 45   45.0821917808219   45.1333333333333 
    ##                  2                 60                  1                  1 
    ##   45.3287671232877   45.7142857142857                 46   46.1643835616438 
    ##                  1                  6                  2                  1 
    ##   46.2857142857143   46.5714285714286   46.8571428571429                 47 
    ##                  5                  2                  1                  1 
    ##   47.1428571428571   47.7142857142857   47.8571428571429                 48 
    ##                 49                  1                  1                  3 
    ##   48.2142857142857   48.5714285714286   48.8571428571429                 49 
    ##                  1                 17                  3                  3 
    ##   49.2857142857143   49.4285714285714   49.7142857142857                 50 
    ##                 11                  1                  2                 11 
    ##   50.2857142857143   50.8571428571429   50.9178082191781   51.2876712328767 
    ##                  7                  2                  1                  1 
    ##   51.4285714285714   51.7573385518591   52.4285714285714   52.7619047619048 
    ##                218                  1                  1                  2 
    ##   52.8571428571429   53.4011741682975   53.4285714285714   53.5714285714286 
    ##                  1                  1                  3                  7 
    ##   53.7142857142857                 54   54.2857142857143   54.5714285714286 
    ##                  1                  1                  8                  2 
    ##   54.8571428571429                 55   55.2857142857143   55.4285714285714 
    ##                  1                  3                  1                  6 
    ##   55.7142857142857   55.9285714285714                 56   56.4285714285714 
    ##                 37                  1                  1                  1 
    ##   57.1428571428571   57.7142857142857   57.8571428571429   58.2857142857143 
    ##                 11                  2                  9                  1 
    ##   58.5714285714286   58.6223091976517    58.825831702544   59.2857142857143 
    ##                  3                  1                  1                  1 
    ##   59.4285714285714                 60   60.3287671232877                 61 
    ##                  6                211                  2                  4 
    ##   61.4285714285714   61.7142857142857                 62   62.1428571428571 
    ##                  3                  2                  4                  8 
    ##   62.5714285714286   62.8571428571429                 63   63.2876712328767 
    ##                  1                 10                  1                  1 
    ##   63.4285714285714   63.5714285714286   63.9452054794521                 64 
    ##                  2                  1                  1                  6 
    ##   64.2857142857143                 65   65.1428571428571   65.7142857142857 
    ##                 68                  2                  1                  7 
    ##   66.4285714285714   67.1428571428571   67.4285714285714   67.8571428571429 
    ##                  6                  1                  2                  1 
    ##                 68    68.160469667319   68.2309197651663   68.5714285714286 
    ##                  3                  1                  1                124 
    ##   68.6047619047619   68.8571428571429   69.2857142857143   69.5714285714286 
    ##                  1                  1                  1                  2 
    ##   69.6190476190476                 70   70.2857142857143   70.7142857142857 
    ##                  1                  6                  1                  3 
    ##   71.4285714285714   71.8590998043053   72.3287671232877   72.5714285714286 
    ##                  8                  1                  1                  1 
    ##   72.8571428571429   73.1428571428571   73.5714285714286   74.2857142857143 
    ##                 18                  1                  2                  8 
    ##                 75   75.4285714285714   75.7142857142857                 76 
    ##                  7                  3                  1                  1 
    ##   76.4285714285714   76.5714285714286   77.1428571428571   77.1428571428572 
    ##                  1                  7                109                  1 
    ##                 78   78.5714285714286   79.1154598825832   79.2857142857143 
    ##                  1                  2                  1                  8 
    ##                 80   81.1428571428571   81.4285714285714   82.8571428571429 
    ##                  9                  1                 39                  1 
    ##   83.3333333333333   83.5714285714286                 84   84.2857142857143 
    ##                  1                  5                  1                  1 
    ##   84.5714285714286                 85   85.1428571428571   85.7142857142857 
    ##                  1                  5                  2                105 
    ##   86.4285714285714   87.1428571428571               87.2   87.8571428571429 
    ##                  3                  1                  1                  4 
    ##   88.2857142857143   88.5714285714286   89.7142857142857                 90 
    ##                  1                  3                  2                 56 
    ##                 91   91.4285714285714                 92   92.1428571428571 
    ##                  1                  7                  2                  2 
    ##   92.5714285714286   92.8571428571429   92.8767123287671   93.7142857142857 
    ##                  3                  2                  1                  1 
    ##   94.2857142857143                 95   96.4285714285714   97.1428571428571 
    ##                 60                  2                  6                  3 
    ##   97.8571428571429   98.5714285714286   99.2857142857143   99.4285714285714 
    ##                  1                 18                  1                  1 
    ##                100   100.714285714286   101.428571428571   101.714285714286 
    ##                  9                  3                  4                  1 
    ##   102.857142857143   103.857142857143                104   104.285714285714 
    ##                 97                  1                  1                  1 
    ##                105   105.714285714286   106.857142857143   107.142857142857 
    ##                  5                  2                  1                 17 
    ##   107.714285714286   108.571428571429                109   109.285714285714 
    ##                  1                  2                  1                  2 
    ##                110   111.428571428571   112.857142857143   113.571428571429 
    ##                  3                 40                  1                  5 
    ##   114.857142857143   115.714285714286   116.428571428571   117.142857142857 
    ##                  2                 16                  1                  1 
    ##   117.857142857143   118.857142857143                120   120.657534246575 
    ##                  1                  1                 98                  1 
    ##   120.857142857143   121.714285714286                122   122.142857142857 
    ##                  1                  1                  2                  2 
    ##   122.857142857143                124   124.285714285714   125.142857142857 
    ##                  1                  7                  5                  1 
    ##   125.714285714286   126.428571428571   126.857142857143                128 
    ##                  2                  1                  1                  2 
    ##   128.571428571429   129.571428571429                130   131.428571428571 
    ##                 57                  1                  6                  2 
    ##                132   132.857142857143   134.857142857143                135 
    ##                  3                  6                  1                 10 
    ##                136   137.142857142857                138   139.142857142857 
    ##                  1                 58                  1                  2 
    ##   139.285714285714                140   140.714285714286   141.428571428571 
    ##                  1                  4                  1                  8 
    ##   142.857142857143   143.571428571429                144   145.714285714286 
    ##                  1                  1                  3                 16 
    ##   147.142857142857                150   152.142857142857   153.142857142857 
    ##                  1                 16                  1                  1 
    ##   154.285714285714   157.142857142857   158.571428571429                160 
    ##                 51                  2                  6                  4 
    ##   160.714285714286   162.857142857143                165   167.142857142857 
    ##                  2                  7                  1                  3 
    ##   168.571428571429                170   171.428571428571                175 
    ##                  1                  1                 34                  1 
    ##   175.714285714286                180   182.142857142857   182.666666666667 
    ##                  1                 59                  1                  1 
    ##   184.285714285714   185.714285714286   186.428571428571                188 
    ##                  2                  1                  1                  2 
    ##   188.571428571429                190   191.428571428571   192.857142857143 
    ##                 22                  1                  1                  8 
    ##   193.150684931507                196   197.142857142857   199.285714285714 
    ##                  1                  2                 13                  1 
    ##   200.821917808219   202.285714285714   205.714285714286   207.857142857143 
    ##                  1                  1                 30                  1 
    ##   208.673189823875                210   214.285714285714   216.428571428571 
    ##                  1                 10                 13                  1 
    ##   218.571428571429   219.428571428571                220   222.285714285714 
    ##                  1                  1                  5                  1 
    ##   222.857142857143                225   225.714285714286   227.142857142857 
    ##                 12                  1                  1                  2 
    ##   228.571428571429   234.285714285714   238.571428571429                240 
    ##                  1                  1                  1                 33 
    ##   240.164383561644                242   244.285714285714   248.571428571429 
    ##                  1                  1                  2                  7 
    ##   252.857142857143                256   257.142857142857                260 
    ##                  1                  1                 19                  2 
    ##   261.428571428571   265.714285714286                270   274.285714285714 
    ##                  1                  3                  2                  7 
    ##                275   282.857142857143   287.142857142857                290 
    ##                  1                  4                  1                  1 
    ##   291.428571428571                300   304.285714285714   308.571428571429 
    ##                  7                 20                  1                  7 
    ##                310   317.142857142857   325.714285714286   328.571428571429 
    ##                  1                  5                  1                  1 
    ##                330   334.285714285714   338.571428571429   342.857142857143 
    ##                  2                  4                  1                  4 
    ##                350                360   368.571428571429   377.142857142857 
    ##                  1                 19                  1                  8 
    ##                380   385.714285714286                390                392 
    ##                  1                  4                  1                  1 
    ##   394.285714285714                400   402.857142857143   411.428571428571 
    ##                  2                  1                  2                  1 
    ##                420   428.571428571429   437.142857142857   445.714285714286 
    ##                  8                  1                  1                  3 
    ##                450   462.857142857143   475.714285714286                480 
    ##                  1                  1                  1                  7 
    ##                484   488.571428571429   494.285714285714   497.142857142857 
    ##                  1                  1                  1                  1 
    ##   505.714285714286   514.285714285714   527.142857142857                540 
    ##                  1                  2                  1                  5 
    ##   548.571428571429   565.714285714286                570   574.285714285714 
    ##                  5                  2                  1                  1 
    ##   582.857142857143                600   617.142857142857                636 
    ##                  1                  6                  1                  1 
    ##                638                660                675   677.142857142857 
    ##                  1                  3                  1                  2 
    ##                720   741.714285714286                744   745.714285714286 
    ##                  3                  1                  1                  1 
    ##                780                810   822.857142857143                840 
    ##                  2                  2                  1                  5 
    ##   842.857142857143                900   900.131506849315   905.714285714286 
    ##                  2                  6                  1                  1 
    ##   925.714285714286   937.142857142857   942.857142857143                945 
    ##                  1                  1                  2                  1 
    ##                960               1050               1080   1114.28571428571 
    ##                  1                  1                  3                  1 
    ##               1140               1200   1234.28571428571   1285.71428571429 
    ##                  1                  1                  1                  1 
    ##               1380               1440               1464               1680 
    ##                  1                  2                  1                  1 
    ##               1800   1988.57142857143               <NA> 
    ##                  1                  1                  0

    ## 
    ##          150+ Less than 150          <NA> 
    ##           625         11308             0

    ## [1] "Male"   "Female"

    ## 
    ##   Male Female 
    ##   5575   6358

    ##       SEQN           DMDEDUC2        RIDAGEYR       RIAGENDR       RIDRETH3    
    ##  Min.   :130378   Min.   :1.000   Min.   : 0.00   Male  :5575   Min.   :1.000  
    ##  1st Qu.:133361   1st Qu.:3.000   1st Qu.:13.00   Female:6358   1st Qu.:3.000  
    ##  Median :136344   Median :4.000   Median :37.00                 Median :3.000  
    ##  Mean   :136344   Mean   :3.805   Mean   :38.32                 Mean   :3.321  
    ##  3rd Qu.:139327   3rd Qu.:5.000   3rd Qu.:62.00                 3rd Qu.:4.000  
    ##  Max.   :142310   Max.   :9.000   Max.   :80.00                 Max.   :7.000  
    ##                   NA's   :4139                                                 
    ##     INDFMPIR         ALQ111          ALQ121           ALQ130       
    ##  Min.   :0.000   Min.   :1.000   Min.   : 0.000   Min.   :  1.000  
    ##  1st Qu.:1.180   1st Qu.:1.000   1st Qu.: 2.000   1st Qu.:  1.000  
    ##  Median :2.500   Median :1.000   Median : 5.000   Median :  2.000  
    ##  Mean   :2.708   Mean   :1.109   Mean   : 5.031   Mean   :  5.843  
    ##  3rd Qu.:4.500   3rd Qu.:1.000   3rd Qu.: 8.000   3rd Qu.:  3.000  
    ##  Max.   :5.000   Max.   :9.000   Max.   :99.000   Max.   :999.000  
    ##  NA's   :2041    NA's   :6452    NA's   :7011     NA's   :7864     
    ##      ALQ142           ALQ270           ALQ280           ALQ151     
    ##  Min.   : 0.000   Min.   : 0.000   Min.   : 0.000   Min.   :1.000  
    ##  1st Qu.: 0.000   1st Qu.: 0.000   1st Qu.: 0.000   1st Qu.:2.000  
    ##  Median : 4.000   Median : 4.000   Median : 0.000   Median :2.000  
    ##  Mean   : 4.742   Mean   : 4.838   Mean   : 3.545   Mean   :1.821  
    ##  3rd Qu.: 9.000   3rd Qu.: 9.000   3rd Qu.: 7.000   3rd Qu.:2.000  
    ##  Max.   :99.000   Max.   :99.000   Max.   :99.000   Max.   :9.000  
    ##  NA's   :7851     NA's   :9567     NA's   :9571     NA's   :7032   
    ##      ALQ170            DIQ010          DID040           DIQ160     
    ##  Min.   :  0.000   Min.   :1.000   Min.   :  1.00   Min.   :1.000  
    ##  1st Qu.:  0.000   1st Qu.:2.000   1st Qu.: 40.00   1st Qu.:2.000  
    ##  Median :  1.000   Median :2.000   Median : 50.00   Median :2.000  
    ##  Mean   :  4.396   Mean   :1.935   Mean   : 70.02   Mean   :1.899  
    ##  3rd Qu.:  2.000   3rd Qu.:2.000   3rd Qu.: 60.00   3rd Qu.:2.000  
    ##  Max.   :999.000   Max.   :9.000   Max.   :999.00   Max.   :9.000  
    ##  NA's   :9575      NA's   :193     NA's   :10852    NA's   :3911   
    ##      DIQ180          DIQ050          DID060          DIQ060U     
    ##  Min.   :1.000   Min.   :1.000   Min.   :  1.00   Min.   :1.000  
    ##  1st Qu.:1.000   1st Qu.:1.000   1st Qu.:  5.00   1st Qu.:2.000  
    ##  Median :2.000   Median :2.000   Median :  9.00   Median :2.000  
    ##  Mean   :1.819   Mean   :1.682   Mean   : 40.32   Mean   :1.895  
    ##  3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.: 17.00   3rd Qu.:2.000  
    ##  Max.   :9.000   Max.   :2.000   Max.   :999.00   Max.   :2.000  
    ##  NA's   :3629    NA's   :10852   NA's   :11590    NA's   :11601  
    ##      DIQ070         PAD790Q          PAD790U              PAD800       
    ##  Min.   :1.000   Min.   :   0.00   Length:11933       Min.   :   1.00  
    ##  1st Qu.:1.000   1st Qu.:   1.00   Class :character   1st Qu.:  30.00  
    ##  Median :2.000   Median :   2.00   Mode  :character   Median :  60.00  
    ##  Mean   :1.633   Mean   :  60.14                      Mean   :  93.44  
    ##  3rd Qu.:2.000   3rd Qu.:   4.00                      3rd Qu.:  60.00  
    ##  Max.   :9.000   Max.   :9999.00                      Max.   :9999.00  
    ##  NA's   :9652    NA's   :3798                         NA's   :5543     
    ##     PAD810Q          PAD810U              PAD820            PAD680    
    ##  Min.   :   0.00   Length:11933       Min.   :   1.00   Min.   :   0  
    ##  1st Qu.:   0.00   Class :character   1st Qu.:  30.00   1st Qu.: 180  
    ##  Median :   0.00   Mode  :character   Median :  45.00   Median : 300  
    ##  Mean   :  49.21                      Mean   :  97.57   Mean   : 447  
    ##  3rd Qu.:   2.00                      3rd Qu.:  60.00   3rd Qu.: 480  
    ##  Max.   :9999.00                      Max.   :9999.00   Max.   :9999  
    ##  NA's   :3794                         NA's   :8246      NA's   :3795  
    ##   told_pre_dm       told_dm       freq_moderate      min_moderate  
    ##  Min.   :0.000   Min.   :0.0000   Min.   :  0.000   Min.   :  1.0  
    ##  1st Qu.:0.000   1st Qu.:0.0000   1st Qu.:  1.000   1st Qu.: 30.0  
    ##  Median :0.000   Median :0.0000   Median :  2.000   Median : 60.0  
    ##  Mean   :0.115   Mean   :0.0944   Mean   :  2.662   Mean   : 63.9  
    ##  3rd Qu.:0.000   3rd Qu.:0.0000   3rd Qu.:  4.000   3rd Qu.: 60.0  
    ##  Max.   :1.000   Max.   :1.0000   Max.   :180.000   Max.   :720.0  
    ##  NA's   :3926    NA's   :481      NA's   :3847      NA's   :5562   
    ##  freq_vigorous      min_vigorous      total_mod         total_vig      
    ##  Min.   :  0.000   Min.   :  1.00   Min.   :  0.027   Min.   :  0.027  
    ##  1st Qu.:  0.000   1st Qu.: 30.00   1st Qu.: 10.714   1st Qu.:  4.286  
    ##  Median :  0.000   Median : 45.00   Median : 25.714   Median :  8.571  
    ##  Mean   :  1.167   Mean   : 60.44   Mean   : 41.287   Mean   : 23.314  
    ##  3rd Qu.:  2.000   3rd Qu.: 60.00   3rd Qu.: 45.000   3rd Qu.: 25.714  
    ##  Max.   :200.000   Max.   :900.00   Max.   :900.000   Max.   :960.000  
    ##  NA's   :3834      NA's   :8260     NA's   :5562      NA's   :8261     
    ##     adj_vig          sum_mod_vig         sum_cat         
    ##  Min.   :   0.055   Min.   :   0.000   Length:11933      
    ##  1st Qu.:   8.571   1st Qu.:   0.000   Class :character  
    ##  Median :  17.143   Median :   4.286   Mode  :character  
    ##  Mean   :  46.628   Mean   :  36.391                     
    ##  3rd Qu.:  51.429   3rd Qu.:  38.571                     
    ##  Max.   :1920.000   Max.   :1988.571                     
    ##  NA's   :8261

    ## [1] "Hispanic/Latino"    "Non-Hispanic White" "Non-Hispanic Black"
    ## [4] "Non-Hispanic Asian" "Other race"         "NA"

    ## 
    ##    Hispanic/Latino Non-Hispanic White Non-Hispanic Black Non-Hispanic Asian 
    ##               2490               6217               1597                681 
    ##         Other race                 NA 
    ##                948                  0

    ##       SEQN           DMDEDUC2        RIDAGEYR       RIAGENDR   
    ##  Min.   :130378   Min.   :1.000   Min.   : 0.00   Male  :5575  
    ##  1st Qu.:133361   1st Qu.:3.000   1st Qu.:13.00   Female:6358  
    ##  Median :136344   Median :4.000   Median :37.00                
    ##  Mean   :136344   Mean   :3.805   Mean   :38.32                
    ##  3rd Qu.:139327   3rd Qu.:5.000   3rd Qu.:62.00                
    ##  Max.   :142310   Max.   :9.000   Max.   :80.00                
    ##                   NA's   :4139                                 
    ##                RIDRETH3       INDFMPIR         ALQ111          ALQ121      
    ##  Hispanic/Latino   :2490   Min.   :0.000   Min.   :1.000   Min.   : 0.000  
    ##  Non-Hispanic White:6217   1st Qu.:1.180   1st Qu.:1.000   1st Qu.: 2.000  
    ##  Non-Hispanic Black:1597   Median :2.500   Median :1.000   Median : 5.000  
    ##  Non-Hispanic Asian: 681   Mean   :2.708   Mean   :1.109   Mean   : 5.031  
    ##  Other race        : 948   3rd Qu.:4.500   3rd Qu.:1.000   3rd Qu.: 8.000  
    ##  NA                :   0   Max.   :5.000   Max.   :9.000   Max.   :99.000  
    ##                            NA's   :2041    NA's   :6452    NA's   :7011    
    ##      ALQ130            ALQ142           ALQ270           ALQ280      
    ##  Min.   :  1.000   Min.   : 0.000   Min.   : 0.000   Min.   : 0.000  
    ##  1st Qu.:  1.000   1st Qu.: 0.000   1st Qu.: 0.000   1st Qu.: 0.000  
    ##  Median :  2.000   Median : 4.000   Median : 4.000   Median : 0.000  
    ##  Mean   :  5.843   Mean   : 4.742   Mean   : 4.838   Mean   : 3.545  
    ##  3rd Qu.:  3.000   3rd Qu.: 9.000   3rd Qu.: 9.000   3rd Qu.: 7.000  
    ##  Max.   :999.000   Max.   :99.000   Max.   :99.000   Max.   :99.000  
    ##  NA's   :7864      NA's   :7851     NA's   :9567     NA's   :9571    
    ##      ALQ151          ALQ170            DIQ010          DID040      
    ##  Min.   :1.000   Min.   :  0.000   Min.   :1.000   Min.   :  1.00  
    ##  1st Qu.:2.000   1st Qu.:  0.000   1st Qu.:2.000   1st Qu.: 40.00  
    ##  Median :2.000   Median :  1.000   Median :2.000   Median : 50.00  
    ##  Mean   :1.821   Mean   :  4.396   Mean   :1.935   Mean   : 70.02  
    ##  3rd Qu.:2.000   3rd Qu.:  2.000   3rd Qu.:2.000   3rd Qu.: 60.00  
    ##  Max.   :9.000   Max.   :999.000   Max.   :9.000   Max.   :999.00  
    ##  NA's   :7032    NA's   :9575      NA's   :193     NA's   :10852   
    ##      DIQ160          DIQ180          DIQ050          DID060      
    ##  Min.   :1.000   Min.   :1.000   Min.   :1.000   Min.   :  1.00  
    ##  1st Qu.:2.000   1st Qu.:1.000   1st Qu.:1.000   1st Qu.:  5.00  
    ##  Median :2.000   Median :2.000   Median :2.000   Median :  9.00  
    ##  Mean   :1.899   Mean   :1.819   Mean   :1.682   Mean   : 40.32  
    ##  3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.: 17.00  
    ##  Max.   :9.000   Max.   :9.000   Max.   :2.000   Max.   :999.00  
    ##  NA's   :3911    NA's   :3629    NA's   :10852   NA's   :11590   
    ##     DIQ060U          DIQ070         PAD790Q          PAD790U         
    ##  Min.   :1.000   Min.   :1.000   Min.   :   0.00   Length:11933      
    ##  1st Qu.:2.000   1st Qu.:1.000   1st Qu.:   1.00   Class :character  
    ##  Median :2.000   Median :2.000   Median :   2.00   Mode  :character  
    ##  Mean   :1.895   Mean   :1.633   Mean   :  60.14                     
    ##  3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.:   4.00                     
    ##  Max.   :2.000   Max.   :9.000   Max.   :9999.00                     
    ##  NA's   :11601   NA's   :9652    NA's   :3798                        
    ##      PAD800           PAD810Q          PAD810U              PAD820       
    ##  Min.   :   1.00   Min.   :   0.00   Length:11933       Min.   :   1.00  
    ##  1st Qu.:  30.00   1st Qu.:   0.00   Class :character   1st Qu.:  30.00  
    ##  Median :  60.00   Median :   0.00   Mode  :character   Median :  45.00  
    ##  Mean   :  93.44   Mean   :  49.21                      Mean   :  97.57  
    ##  3rd Qu.:  60.00   3rd Qu.:   2.00                      3rd Qu.:  60.00  
    ##  Max.   :9999.00   Max.   :9999.00                      Max.   :9999.00  
    ##  NA's   :5543      NA's   :3794                         NA's   :8246     
    ##      PAD680      told_pre_dm       told_dm       freq_moderate    
    ##  Min.   :   0   Min.   :0.000   Min.   :0.0000   Min.   :  0.000  
    ##  1st Qu.: 180   1st Qu.:0.000   1st Qu.:0.0000   1st Qu.:  1.000  
    ##  Median : 300   Median :0.000   Median :0.0000   Median :  2.000  
    ##  Mean   : 447   Mean   :0.115   Mean   :0.0944   Mean   :  2.662  
    ##  3rd Qu.: 480   3rd Qu.:0.000   3rd Qu.:0.0000   3rd Qu.:  4.000  
    ##  Max.   :9999   Max.   :1.000   Max.   :1.0000   Max.   :180.000  
    ##  NA's   :3795   NA's   :3926    NA's   :481      NA's   :3847     
    ##   min_moderate   freq_vigorous      min_vigorous      total_mod      
    ##  Min.   :  1.0   Min.   :  0.000   Min.   :  1.00   Min.   :  0.027  
    ##  1st Qu.: 30.0   1st Qu.:  0.000   1st Qu.: 30.00   1st Qu.: 10.714  
    ##  Median : 60.0   Median :  0.000   Median : 45.00   Median : 25.714  
    ##  Mean   : 63.9   Mean   :  1.167   Mean   : 60.44   Mean   : 41.287  
    ##  3rd Qu.: 60.0   3rd Qu.:  2.000   3rd Qu.: 60.00   3rd Qu.: 45.000  
    ##  Max.   :720.0   Max.   :200.000   Max.   :900.00   Max.   :900.000  
    ##  NA's   :5562    NA's   :3834      NA's   :8260     NA's   :5562     
    ##    total_vig          adj_vig          sum_mod_vig         sum_cat         
    ##  Min.   :  0.027   Min.   :   0.055   Min.   :   0.000   Length:11933      
    ##  1st Qu.:  4.286   1st Qu.:   8.571   1st Qu.:   0.000   Class :character  
    ##  Median :  8.571   Median :  17.143   Median :   4.286   Mode  :character  
    ##  Mean   : 23.314   Mean   :  46.628   Mean   :  36.391                     
    ##  3rd Qu.: 25.714   3rd Qu.:  51.429   3rd Qu.:  38.571                     
    ##  Max.   :960.000   Max.   :1920.000   Max.   :1988.571                     
    ##  NA's   :8261      NA's   :8261

    ## 
    ##    Low-income Middle-income   High-Income 
    ##             0          4955          2977

    ##       SEQN           DMDEDUC2        RIDAGEYR       RIAGENDR   
    ##  Min.   :130378   Min.   :1.000   Min.   : 0.00   Male  :5575  
    ##  1st Qu.:133361   1st Qu.:3.000   1st Qu.:13.00   Female:6358  
    ##  Median :136344   Median :4.000   Median :37.00                
    ##  Mean   :136344   Mean   :3.805   Mean   :38.32                
    ##  3rd Qu.:139327   3rd Qu.:5.000   3rd Qu.:62.00                
    ##  Max.   :142310   Max.   :9.000   Max.   :80.00                
    ##                   NA's   :4139                                 
    ##                RIDRETH3       INDFMPIR         ALQ111          ALQ121      
    ##  Hispanic/Latino   :2490   Min.   :0.000   Min.   :1.000   Min.   : 0.000  
    ##  Non-Hispanic White:6217   1st Qu.:1.180   1st Qu.:1.000   1st Qu.: 2.000  
    ##  Non-Hispanic Black:1597   Median :2.500   Median :1.000   Median : 5.000  
    ##  Non-Hispanic Asian: 681   Mean   :2.708   Mean   :1.109   Mean   : 5.031  
    ##  Other race        : 948   3rd Qu.:4.500   3rd Qu.:1.000   3rd Qu.: 8.000  
    ##  NA                :   0   Max.   :5.000   Max.   :9.000   Max.   :99.000  
    ##                            NA's   :2041    NA's   :6452    NA's   :7011    
    ##      ALQ130            ALQ142           ALQ270           ALQ280      
    ##  Min.   :  1.000   Min.   : 0.000   Min.   : 0.000   Min.   : 0.000  
    ##  1st Qu.:  1.000   1st Qu.: 0.000   1st Qu.: 0.000   1st Qu.: 0.000  
    ##  Median :  2.000   Median : 4.000   Median : 4.000   Median : 0.000  
    ##  Mean   :  5.843   Mean   : 4.742   Mean   : 4.838   Mean   : 3.545  
    ##  3rd Qu.:  3.000   3rd Qu.: 9.000   3rd Qu.: 9.000   3rd Qu.: 7.000  
    ##  Max.   :999.000   Max.   :99.000   Max.   :99.000   Max.   :99.000  
    ##  NA's   :7864      NA's   :7851     NA's   :9567     NA's   :9571    
    ##      ALQ151          ALQ170            DIQ010          DID040      
    ##  Min.   :1.000   Min.   :  0.000   Min.   :1.000   Min.   :  1.00  
    ##  1st Qu.:2.000   1st Qu.:  0.000   1st Qu.:2.000   1st Qu.: 40.00  
    ##  Median :2.000   Median :  1.000   Median :2.000   Median : 50.00  
    ##  Mean   :1.821   Mean   :  4.396   Mean   :1.935   Mean   : 70.02  
    ##  3rd Qu.:2.000   3rd Qu.:  2.000   3rd Qu.:2.000   3rd Qu.: 60.00  
    ##  Max.   :9.000   Max.   :999.000   Max.   :9.000   Max.   :999.00  
    ##  NA's   :7032    NA's   :9575      NA's   :193     NA's   :10852   
    ##      DIQ160          DIQ180          DIQ050          DID060      
    ##  Min.   :1.000   Min.   :1.000   Min.   :1.000   Min.   :  1.00  
    ##  1st Qu.:2.000   1st Qu.:1.000   1st Qu.:1.000   1st Qu.:  5.00  
    ##  Median :2.000   Median :2.000   Median :2.000   Median :  9.00  
    ##  Mean   :1.899   Mean   :1.819   Mean   :1.682   Mean   : 40.32  
    ##  3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.: 17.00  
    ##  Max.   :9.000   Max.   :9.000   Max.   :2.000   Max.   :999.00  
    ##  NA's   :3911    NA's   :3629    NA's   :10852   NA's   :11590   
    ##     DIQ060U          DIQ070         PAD790Q          PAD790U         
    ##  Min.   :1.000   Min.   :1.000   Min.   :   0.00   Length:11933      
    ##  1st Qu.:2.000   1st Qu.:1.000   1st Qu.:   1.00   Class :character  
    ##  Median :2.000   Median :2.000   Median :   2.00   Mode  :character  
    ##  Mean   :1.895   Mean   :1.633   Mean   :  60.14                     
    ##  3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.:   4.00                     
    ##  Max.   :2.000   Max.   :9.000   Max.   :9999.00                     
    ##  NA's   :11601   NA's   :9652    NA's   :3798                        
    ##      PAD800           PAD810Q          PAD810U              PAD820       
    ##  Min.   :   1.00   Min.   :   0.00   Length:11933       Min.   :   1.00  
    ##  1st Qu.:  30.00   1st Qu.:   0.00   Class :character   1st Qu.:  30.00  
    ##  Median :  60.00   Median :   0.00   Mode  :character   Median :  45.00  
    ##  Mean   :  93.44   Mean   :  49.21                      Mean   :  97.57  
    ##  3rd Qu.:  60.00   3rd Qu.:   2.00                      3rd Qu.:  60.00  
    ##  Max.   :9999.00   Max.   :9999.00                      Max.   :9999.00  
    ##  NA's   :5543      NA's   :3794                         NA's   :8246     
    ##      PAD680      told_pre_dm       told_dm       freq_moderate    
    ##  Min.   :   0   Min.   :0.000   Min.   :0.0000   Min.   :  0.000  
    ##  1st Qu.: 180   1st Qu.:0.000   1st Qu.:0.0000   1st Qu.:  1.000  
    ##  Median : 300   Median :0.000   Median :0.0000   Median :  2.000  
    ##  Mean   : 447   Mean   :0.115   Mean   :0.0944   Mean   :  2.662  
    ##  3rd Qu.: 480   3rd Qu.:0.000   3rd Qu.:0.0000   3rd Qu.:  4.000  
    ##  Max.   :9999   Max.   :1.000   Max.   :1.0000   Max.   :180.000  
    ##  NA's   :3795   NA's   :3926    NA's   :481      NA's   :3847     
    ##   min_moderate   freq_vigorous      min_vigorous      total_mod      
    ##  Min.   :  1.0   Min.   :  0.000   Min.   :  1.00   Min.   :  0.027  
    ##  1st Qu.: 30.0   1st Qu.:  0.000   1st Qu.: 30.00   1st Qu.: 10.714  
    ##  Median : 60.0   Median :  0.000   Median : 45.00   Median : 25.714  
    ##  Mean   : 63.9   Mean   :  1.167   Mean   : 60.44   Mean   : 41.287  
    ##  3rd Qu.: 60.0   3rd Qu.:  2.000   3rd Qu.: 60.00   3rd Qu.: 45.000  
    ##  Max.   :720.0   Max.   :200.000   Max.   :900.00   Max.   :900.000  
    ##  NA's   :5562    NA's   :3834      NA's   :8260     NA's   :5562     
    ##    total_vig          adj_vig          sum_mod_vig         sum_cat         
    ##  Min.   :  0.027   Min.   :   0.055   Min.   :   0.000   Length:11933      
    ##  1st Qu.:  4.286   1st Qu.:   8.571   1st Qu.:   0.000   Class :character  
    ##  Median :  8.571   Median :  17.143   Median :   4.286   Mode  :character  
    ##  Mean   : 23.314   Mean   :  46.628   Mean   :  36.391                     
    ##  3rd Qu.: 25.714   3rd Qu.:  51.429   3rd Qu.:  38.571                     
    ##  Max.   :960.000   Max.   :1920.000   Max.   :1988.571                     
    ##  NA's   :8261      NA's   :8261                                            
    ##        INDFMPIR_group
    ##  Low-income   :   0  
    ##  Middle-income:4955  
    ##  High-Income  :2977  
    ##  NA's         :4001  
    ##                      
    ##                      
    ## 

    ##  [1] "SEQN"           "DMDEDUC2"       "RIDAGEYR"       "RIAGENDR"      
    ##  [5] "RIDRETH3"       "INDFMPIR"       "ALQ111"         "ALQ121"        
    ##  [9] "ALQ130"         "ALQ142"         "ALQ270"         "ALQ280"        
    ## [13] "ALQ151"         "ALQ170"         "DIQ010"         "DID040"        
    ## [17] "DIQ160"         "DIQ180"         "DIQ050"         "DID060"        
    ## [21] "DIQ060U"        "DIQ070"         "PAD790Q"        "PAD790U"       
    ## [25] "PAD800"         "PAD810Q"        "PAD810U"        "PAD820"        
    ## [29] "PAD680"         "told_pre_dm"    "told_dm"        "freq_moderate" 
    ## [33] "min_moderate"   "freq_vigorous"  "min_vigorous"   "total_mod"     
    ## [37] "total_vig"      "adj_vig"        "sum_mod_vig"    "sum_cat"       
    ## [41] "INDFMPIR_group" "age_gp2"

    ##       SEQN           DMDEDUC2        RIDAGEYR       RIAGENDR   
    ##  Min.   :130378   Min.   :1.000   Min.   : 0.00   Male  :5575  
    ##  1st Qu.:133361   1st Qu.:3.000   1st Qu.:13.00   Female:6358  
    ##  Median :136344   Median :4.000   Median :37.00                
    ##  Mean   :136344   Mean   :3.805   Mean   :38.32                
    ##  3rd Qu.:139327   3rd Qu.:5.000   3rd Qu.:62.00                
    ##  Max.   :142310   Max.   :9.000   Max.   :80.00                
    ##                   NA's   :4139                                 
    ##                RIDRETH3       INDFMPIR         ALQ111          ALQ121      
    ##  Hispanic/Latino   :2490   Min.   :0.000   Min.   :1.000   Min.   : 0.000  
    ##  Non-Hispanic White:6217   1st Qu.:1.180   1st Qu.:1.000   1st Qu.: 2.000  
    ##  Non-Hispanic Black:1597   Median :2.500   Median :1.000   Median : 5.000  
    ##  Non-Hispanic Asian: 681   Mean   :2.708   Mean   :1.109   Mean   : 5.031  
    ##  Other race        : 948   3rd Qu.:4.500   3rd Qu.:1.000   3rd Qu.: 8.000  
    ##  NA                :   0   Max.   :5.000   Max.   :9.000   Max.   :99.000  
    ##                            NA's   :2041    NA's   :6452    NA's   :7011    
    ##      ALQ130            ALQ142           ALQ270           ALQ280      
    ##  Min.   :  1.000   Min.   : 0.000   Min.   : 0.000   Min.   : 0.000  
    ##  1st Qu.:  1.000   1st Qu.: 0.000   1st Qu.: 0.000   1st Qu.: 0.000  
    ##  Median :  2.000   Median : 4.000   Median : 4.000   Median : 0.000  
    ##  Mean   :  5.843   Mean   : 4.742   Mean   : 4.838   Mean   : 3.545  
    ##  3rd Qu.:  3.000   3rd Qu.: 9.000   3rd Qu.: 9.000   3rd Qu.: 7.000  
    ##  Max.   :999.000   Max.   :99.000   Max.   :99.000   Max.   :99.000  
    ##  NA's   :7864      NA's   :7851     NA's   :9567     NA's   :9571    
    ##      ALQ151          ALQ170            DIQ010          DID040      
    ##  Min.   :1.000   Min.   :  0.000   Min.   :1.000   Min.   :  1.00  
    ##  1st Qu.:2.000   1st Qu.:  0.000   1st Qu.:2.000   1st Qu.: 40.00  
    ##  Median :2.000   Median :  1.000   Median :2.000   Median : 50.00  
    ##  Mean   :1.821   Mean   :  4.396   Mean   :1.935   Mean   : 70.02  
    ##  3rd Qu.:2.000   3rd Qu.:  2.000   3rd Qu.:2.000   3rd Qu.: 60.00  
    ##  Max.   :9.000   Max.   :999.000   Max.   :9.000   Max.   :999.00  
    ##  NA's   :7032    NA's   :9575      NA's   :193     NA's   :10852   
    ##      DIQ160          DIQ180          DIQ050          DID060      
    ##  Min.   :1.000   Min.   :1.000   Min.   :1.000   Min.   :  1.00  
    ##  1st Qu.:2.000   1st Qu.:1.000   1st Qu.:1.000   1st Qu.:  5.00  
    ##  Median :2.000   Median :2.000   Median :2.000   Median :  9.00  
    ##  Mean   :1.899   Mean   :1.819   Mean   :1.682   Mean   : 40.32  
    ##  3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.: 17.00  
    ##  Max.   :9.000   Max.   :9.000   Max.   :2.000   Max.   :999.00  
    ##  NA's   :3911    NA's   :3629    NA's   :10852   NA's   :11590   
    ##     DIQ060U          DIQ070         PAD790Q          PAD790U         
    ##  Min.   :1.000   Min.   :1.000   Min.   :   0.00   Length:11933      
    ##  1st Qu.:2.000   1st Qu.:1.000   1st Qu.:   1.00   Class :character  
    ##  Median :2.000   Median :2.000   Median :   2.00   Mode  :character  
    ##  Mean   :1.895   Mean   :1.633   Mean   :  60.14                     
    ##  3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.:   4.00                     
    ##  Max.   :2.000   Max.   :9.000   Max.   :9999.00                     
    ##  NA's   :11601   NA's   :9652    NA's   :3798                        
    ##      PAD800           PAD810Q          PAD810U              PAD820       
    ##  Min.   :   1.00   Min.   :   0.00   Length:11933       Min.   :   1.00  
    ##  1st Qu.:  30.00   1st Qu.:   0.00   Class :character   1st Qu.:  30.00  
    ##  Median :  60.00   Median :   0.00   Mode  :character   Median :  45.00  
    ##  Mean   :  93.44   Mean   :  49.21                      Mean   :  97.57  
    ##  3rd Qu.:  60.00   3rd Qu.:   2.00                      3rd Qu.:  60.00  
    ##  Max.   :9999.00   Max.   :9999.00                      Max.   :9999.00  
    ##  NA's   :5543      NA's   :3794                         NA's   :8246     
    ##      PAD680      told_pre_dm       told_dm       freq_moderate    
    ##  Min.   :   0   Min.   :0.000   Min.   :0.0000   Min.   :  0.000  
    ##  1st Qu.: 180   1st Qu.:0.000   1st Qu.:0.0000   1st Qu.:  1.000  
    ##  Median : 300   Median :0.000   Median :0.0000   Median :  2.000  
    ##  Mean   : 447   Mean   :0.115   Mean   :0.0944   Mean   :  2.662  
    ##  3rd Qu.: 480   3rd Qu.:0.000   3rd Qu.:0.0000   3rd Qu.:  4.000  
    ##  Max.   :9999   Max.   :1.000   Max.   :1.0000   Max.   :180.000  
    ##  NA's   :3795   NA's   :3926    NA's   :481      NA's   :3847     
    ##   min_moderate   freq_vigorous      min_vigorous      total_mod      
    ##  Min.   :  1.0   Min.   :  0.000   Min.   :  1.00   Min.   :  0.027  
    ##  1st Qu.: 30.0   1st Qu.:  0.000   1st Qu.: 30.00   1st Qu.: 10.714  
    ##  Median : 60.0   Median :  0.000   Median : 45.00   Median : 25.714  
    ##  Mean   : 63.9   Mean   :  1.167   Mean   : 60.44   Mean   : 41.287  
    ##  3rd Qu.: 60.0   3rd Qu.:  2.000   3rd Qu.: 60.00   3rd Qu.: 45.000  
    ##  Max.   :720.0   Max.   :200.000   Max.   :900.00   Max.   :900.000  
    ##  NA's   :5562    NA's   :3834      NA's   :8260     NA's   :5562     
    ##    total_vig          adj_vig          sum_mod_vig         sum_cat         
    ##  Min.   :  0.027   Min.   :   0.055   Min.   :   0.000   Length:11933      
    ##  1st Qu.:  4.286   1st Qu.:   8.571   1st Qu.:   0.000   Class :character  
    ##  Median :  8.571   Median :  17.143   Median :   4.286   Mode  :character  
    ##  Mean   : 23.314   Mean   :  46.628   Mean   :  36.391                     
    ##  3rd Qu.: 25.714   3rd Qu.:  51.429   3rd Qu.:  38.571                     
    ##  Max.   :960.000   Max.   :1920.000   Max.   :1988.571                     
    ##  NA's   :8261      NA's   :8261                                            
    ##        INDFMPIR_group   age_gp2         
    ##  Low-income   :   0   Length:11933      
    ##  Middle-income:4955   Class :character  
    ##  High-Income  :2977   Mode  :character  
    ##  NA's         :4001                     
    ##                                         
    ##                                         
    ## 

    ## 
    ##    1    2    3    4    5    9 <NA> 
    ##  373  666 1749 2370 2625   11 4139

    ## 
    ##    1    2    3    4    5 <NA> 
    ##  373  666 1749 2370 2625 4150

    ## 
    ##                   Less than 9th grade 9-11th grade (incl. 12th, no diploma) 
    ##                                   373                                   666 
    ##    High school grad/GED or equivalent             Some college or AA degree 
    ##                                  1749                                  2370 
    ##             College graduate or above                                  <NA> 
    ##                                  2625                                  4150

    ##       SEQN           DMDEDUC2        RIDAGEYR       RIAGENDR   
    ##  Min.   :130378   Min.   :1.000   Min.   : 0.00   Male  :5575  
    ##  1st Qu.:133361   1st Qu.:3.000   1st Qu.:13.00   Female:6358  
    ##  Median :136344   Median :4.000   Median :37.00                
    ##  Mean   :136344   Mean   :3.805   Mean   :38.32                
    ##  3rd Qu.:139327   3rd Qu.:5.000   3rd Qu.:62.00                
    ##  Max.   :142310   Max.   :9.000   Max.   :80.00                
    ##                   NA's   :4139                                 
    ##                RIDRETH3       INDFMPIR         ALQ111          ALQ121      
    ##  Hispanic/Latino   :2490   Min.   :0.000   Min.   :1.000   Min.   : 0.000  
    ##  Non-Hispanic White:6217   1st Qu.:1.180   1st Qu.:1.000   1st Qu.: 2.000  
    ##  Non-Hispanic Black:1597   Median :2.500   Median :1.000   Median : 5.000  
    ##  Non-Hispanic Asian: 681   Mean   :2.708   Mean   :1.109   Mean   : 5.031  
    ##  Other race        : 948   3rd Qu.:4.500   3rd Qu.:1.000   3rd Qu.: 8.000  
    ##  NA                :   0   Max.   :5.000   Max.   :9.000   Max.   :99.000  
    ##                            NA's   :2041    NA's   :6452    NA's   :7011    
    ##      ALQ130            ALQ142           ALQ270           ALQ280      
    ##  Min.   :  1.000   Min.   : 0.000   Min.   : 0.000   Min.   : 0.000  
    ##  1st Qu.:  1.000   1st Qu.: 0.000   1st Qu.: 0.000   1st Qu.: 0.000  
    ##  Median :  2.000   Median : 4.000   Median : 4.000   Median : 0.000  
    ##  Mean   :  5.843   Mean   : 4.742   Mean   : 4.838   Mean   : 3.545  
    ##  3rd Qu.:  3.000   3rd Qu.: 9.000   3rd Qu.: 9.000   3rd Qu.: 7.000  
    ##  Max.   :999.000   Max.   :99.000   Max.   :99.000   Max.   :99.000  
    ##  NA's   :7864      NA's   :7851     NA's   :9567     NA's   :9571    
    ##      ALQ151          ALQ170            DIQ010          DID040      
    ##  Min.   :1.000   Min.   :  0.000   Min.   :1.000   Min.   :  1.00  
    ##  1st Qu.:2.000   1st Qu.:  0.000   1st Qu.:2.000   1st Qu.: 40.00  
    ##  Median :2.000   Median :  1.000   Median :2.000   Median : 50.00  
    ##  Mean   :1.821   Mean   :  4.396   Mean   :1.935   Mean   : 70.02  
    ##  3rd Qu.:2.000   3rd Qu.:  2.000   3rd Qu.:2.000   3rd Qu.: 60.00  
    ##  Max.   :9.000   Max.   :999.000   Max.   :9.000   Max.   :999.00  
    ##  NA's   :7032    NA's   :9575      NA's   :193     NA's   :10852   
    ##      DIQ160          DIQ180          DIQ050          DID060      
    ##  Min.   :1.000   Min.   :1.000   Min.   :1.000   Min.   :  1.00  
    ##  1st Qu.:2.000   1st Qu.:1.000   1st Qu.:1.000   1st Qu.:  5.00  
    ##  Median :2.000   Median :2.000   Median :2.000   Median :  9.00  
    ##  Mean   :1.899   Mean   :1.819   Mean   :1.682   Mean   : 40.32  
    ##  3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.: 17.00  
    ##  Max.   :9.000   Max.   :9.000   Max.   :2.000   Max.   :999.00  
    ##  NA's   :3911    NA's   :3629    NA's   :10852   NA's   :11590   
    ##     DIQ060U          DIQ070         PAD790Q          PAD790U         
    ##  Min.   :1.000   Min.   :1.000   Min.   :   0.00   Length:11933      
    ##  1st Qu.:2.000   1st Qu.:1.000   1st Qu.:   1.00   Class :character  
    ##  Median :2.000   Median :2.000   Median :   2.00   Mode  :character  
    ##  Mean   :1.895   Mean   :1.633   Mean   :  60.14                     
    ##  3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.:   4.00                     
    ##  Max.   :2.000   Max.   :9.000   Max.   :9999.00                     
    ##  NA's   :11601   NA's   :9652    NA's   :3798                        
    ##      PAD800           PAD810Q          PAD810U              PAD820       
    ##  Min.   :   1.00   Min.   :   0.00   Length:11933       Min.   :   1.00  
    ##  1st Qu.:  30.00   1st Qu.:   0.00   Class :character   1st Qu.:  30.00  
    ##  Median :  60.00   Median :   0.00   Mode  :character   Median :  45.00  
    ##  Mean   :  93.44   Mean   :  49.21                      Mean   :  97.57  
    ##  3rd Qu.:  60.00   3rd Qu.:   2.00                      3rd Qu.:  60.00  
    ##  Max.   :9999.00   Max.   :9999.00                      Max.   :9999.00  
    ##  NA's   :5543      NA's   :3794                         NA's   :8246     
    ##      PAD680      told_pre_dm       told_dm       freq_moderate    
    ##  Min.   :   0   Min.   :0.000   Min.   :0.0000   Min.   :  0.000  
    ##  1st Qu.: 180   1st Qu.:0.000   1st Qu.:0.0000   1st Qu.:  1.000  
    ##  Median : 300   Median :0.000   Median :0.0000   Median :  2.000  
    ##  Mean   : 447   Mean   :0.115   Mean   :0.0944   Mean   :  2.662  
    ##  3rd Qu.: 480   3rd Qu.:0.000   3rd Qu.:0.0000   3rd Qu.:  4.000  
    ##  Max.   :9999   Max.   :1.000   Max.   :1.0000   Max.   :180.000  
    ##  NA's   :3795   NA's   :3926    NA's   :481      NA's   :3847     
    ##   min_moderate   freq_vigorous      min_vigorous      total_mod      
    ##  Min.   :  1.0   Min.   :  0.000   Min.   :  1.00   Min.   :  0.027  
    ##  1st Qu.: 30.0   1st Qu.:  0.000   1st Qu.: 30.00   1st Qu.: 10.714  
    ##  Median : 60.0   Median :  0.000   Median : 45.00   Median : 25.714  
    ##  Mean   : 63.9   Mean   :  1.167   Mean   : 60.44   Mean   : 41.287  
    ##  3rd Qu.: 60.0   3rd Qu.:  2.000   3rd Qu.: 60.00   3rd Qu.: 45.000  
    ##  Max.   :720.0   Max.   :200.000   Max.   :900.00   Max.   :900.000  
    ##  NA's   :5562    NA's   :3834      NA's   :8260     NA's   :5562     
    ##    total_vig          adj_vig          sum_mod_vig         sum_cat         
    ##  Min.   :  0.027   Min.   :   0.055   Min.   :   0.000   Length:11933      
    ##  1st Qu.:  4.286   1st Qu.:   8.571   1st Qu.:   0.000   Class :character  
    ##  Median :  8.571   Median :  17.143   Median :   4.286   Mode  :character  
    ##  Mean   : 23.314   Mean   :  46.628   Mean   :  36.391                     
    ##  3rd Qu.: 25.714   3rd Qu.:  51.429   3rd Qu.:  38.571                     
    ##  Max.   :960.000   Max.   :1920.000   Max.   :1988.571                     
    ##  NA's   :8261      NA's   :8261                                            
    ##        INDFMPIR_group   age_gp2            educ_num        
    ##  Low-income   :   0   Length:11933       Length:11933      
    ##  Middle-income:4955   Class :character   Class :character  
    ##  High-Income  :2977   Mode  :character   Mode  :character  
    ##  NA's         :4001                                        
    ##                                                            
    ##                                                            
    ##                                                            
    ##                                 educ_factor  
    ##  Less than 9th grade                  : 373  
    ##  9-11th grade (incl. 12th, no diploma): 666  
    ##  High school grad/GED or equivalent   :1749  
    ##  Some college or AA degree            :2370  
    ##  College graduate or above            :2625  
    ##  NA's                                 :4150  
    ## 

    ## 
    ##    No   Yes 
    ## 10371  1081

    ## 
    ##    No   Yes 
    ## 10371  1081

    ##  [1] "SEQN"           "DMDEDUC2"       "RIDAGEYR"       "RIAGENDR"      
    ##  [5] "RIDRETH3"       "INDFMPIR"       "ALQ111"         "ALQ121"        
    ##  [9] "ALQ130"         "ALQ142"         "ALQ270"         "ALQ280"        
    ## [13] "ALQ151"         "ALQ170"         "DIQ010"         "DID040"        
    ## [17] "DIQ160"         "DIQ180"         "DIQ050"         "DID060"        
    ## [21] "DIQ060U"        "DIQ070"         "PAD790Q"        "PAD790U"       
    ## [25] "PAD800"         "PAD810Q"        "PAD810U"        "PAD820"        
    ## [29] "PAD680"         "told_pre_dm"    "told_dm"        "freq_moderate" 
    ## [33] "min_moderate"   "freq_vigorous"  "min_vigorous"   "total_mod"     
    ## [37] "total_vig"      "adj_vig"        "sum_mod_vig"    "sum_cat"       
    ## [41] "INDFMPIR_group" "age_gp2"        "educ_num"       "educ_factor"   
    ## [45] "factor_dm"

    ##       SEQN           DMDEDUC2        RIDAGEYR       RIAGENDR   
    ##  Min.   :130378   Min.   :1.000   Min.   : 0.00   Male  :5575  
    ##  1st Qu.:133361   1st Qu.:3.000   1st Qu.:13.00   Female:6358  
    ##  Median :136344   Median :4.000   Median :37.00                
    ##  Mean   :136344   Mean   :3.805   Mean   :38.32                
    ##  3rd Qu.:139327   3rd Qu.:5.000   3rd Qu.:62.00                
    ##  Max.   :142310   Max.   :9.000   Max.   :80.00                
    ##                   NA's   :4139                                 
    ##                RIDRETH3       INDFMPIR         ALQ111          ALQ121      
    ##  Hispanic/Latino   :2490   Min.   :0.000   Min.   :1.000   Min.   : 0.000  
    ##  Non-Hispanic White:6217   1st Qu.:1.180   1st Qu.:1.000   1st Qu.: 2.000  
    ##  Non-Hispanic Black:1597   Median :2.500   Median :1.000   Median : 5.000  
    ##  Non-Hispanic Asian: 681   Mean   :2.708   Mean   :1.109   Mean   : 5.031  
    ##  Other race        : 948   3rd Qu.:4.500   3rd Qu.:1.000   3rd Qu.: 8.000  
    ##  NA                :   0   Max.   :5.000   Max.   :9.000   Max.   :99.000  
    ##                            NA's   :2041    NA's   :6452    NA's   :7011    
    ##      ALQ130            ALQ142           ALQ270           ALQ280      
    ##  Min.   :  1.000   Min.   : 0.000   Min.   : 0.000   Min.   : 0.000  
    ##  1st Qu.:  1.000   1st Qu.: 0.000   1st Qu.: 0.000   1st Qu.: 0.000  
    ##  Median :  2.000   Median : 4.000   Median : 4.000   Median : 0.000  
    ##  Mean   :  5.843   Mean   : 4.742   Mean   : 4.838   Mean   : 3.545  
    ##  3rd Qu.:  3.000   3rd Qu.: 9.000   3rd Qu.: 9.000   3rd Qu.: 7.000  
    ##  Max.   :999.000   Max.   :99.000   Max.   :99.000   Max.   :99.000  
    ##  NA's   :7864      NA's   :7851     NA's   :9567     NA's   :9571    
    ##      ALQ151          ALQ170            DIQ010          DID040      
    ##  Min.   :1.000   Min.   :  0.000   Min.   :1.000   Min.   :  1.00  
    ##  1st Qu.:2.000   1st Qu.:  0.000   1st Qu.:2.000   1st Qu.: 40.00  
    ##  Median :2.000   Median :  1.000   Median :2.000   Median : 50.00  
    ##  Mean   :1.821   Mean   :  4.396   Mean   :1.935   Mean   : 70.02  
    ##  3rd Qu.:2.000   3rd Qu.:  2.000   3rd Qu.:2.000   3rd Qu.: 60.00  
    ##  Max.   :9.000   Max.   :999.000   Max.   :9.000   Max.   :999.00  
    ##  NA's   :7032    NA's   :9575      NA's   :193     NA's   :10852   
    ##      DIQ160          DIQ180          DIQ050          DID060      
    ##  Min.   :1.000   Min.   :1.000   Min.   :1.000   Min.   :  1.00  
    ##  1st Qu.:2.000   1st Qu.:1.000   1st Qu.:1.000   1st Qu.:  5.00  
    ##  Median :2.000   Median :2.000   Median :2.000   Median :  9.00  
    ##  Mean   :1.899   Mean   :1.819   Mean   :1.682   Mean   : 40.32  
    ##  3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.: 17.00  
    ##  Max.   :9.000   Max.   :9.000   Max.   :2.000   Max.   :999.00  
    ##  NA's   :3911    NA's   :3629    NA's   :10852   NA's   :11590   
    ##     DIQ060U          DIQ070         PAD790Q          PAD790U         
    ##  Min.   :1.000   Min.   :1.000   Min.   :   0.00   Length:11933      
    ##  1st Qu.:2.000   1st Qu.:1.000   1st Qu.:   1.00   Class :character  
    ##  Median :2.000   Median :2.000   Median :   2.00   Mode  :character  
    ##  Mean   :1.895   Mean   :1.633   Mean   :  60.14                     
    ##  3rd Qu.:2.000   3rd Qu.:2.000   3rd Qu.:   4.00                     
    ##  Max.   :2.000   Max.   :9.000   Max.   :9999.00                     
    ##  NA's   :11601   NA's   :9652    NA's   :3798                        
    ##      PAD800           PAD810Q          PAD810U              PAD820       
    ##  Min.   :   1.00   Min.   :   0.00   Length:11933       Min.   :   1.00  
    ##  1st Qu.:  30.00   1st Qu.:   0.00   Class :character   1st Qu.:  30.00  
    ##  Median :  60.00   Median :   0.00   Mode  :character   Median :  45.00  
    ##  Mean   :  93.44   Mean   :  49.21                      Mean   :  97.57  
    ##  3rd Qu.:  60.00   3rd Qu.:   2.00                      3rd Qu.:  60.00  
    ##  Max.   :9999.00   Max.   :9999.00                      Max.   :9999.00  
    ##  NA's   :5543      NA's   :3794                         NA's   :8246     
    ##      PAD680      told_pre_dm       told_dm       freq_moderate    
    ##  Min.   :   0   Min.   :0.000   Min.   :0.0000   Min.   :  0.000  
    ##  1st Qu.: 180   1st Qu.:0.000   1st Qu.:0.0000   1st Qu.:  1.000  
    ##  Median : 300   Median :0.000   Median :0.0000   Median :  2.000  
    ##  Mean   : 447   Mean   :0.115   Mean   :0.0944   Mean   :  2.662  
    ##  3rd Qu.: 480   3rd Qu.:0.000   3rd Qu.:0.0000   3rd Qu.:  4.000  
    ##  Max.   :9999   Max.   :1.000   Max.   :1.0000   Max.   :180.000  
    ##  NA's   :3795   NA's   :3926    NA's   :481      NA's   :3847     
    ##   min_moderate   freq_vigorous      min_vigorous      total_mod      
    ##  Min.   :  1.0   Min.   :  0.000   Min.   :  1.00   Min.   :  0.027  
    ##  1st Qu.: 30.0   1st Qu.:  0.000   1st Qu.: 30.00   1st Qu.: 10.714  
    ##  Median : 60.0   Median :  0.000   Median : 45.00   Median : 25.714  
    ##  Mean   : 63.9   Mean   :  1.167   Mean   : 60.44   Mean   : 41.287  
    ##  3rd Qu.: 60.0   3rd Qu.:  2.000   3rd Qu.: 60.00   3rd Qu.: 45.000  
    ##  Max.   :720.0   Max.   :200.000   Max.   :900.00   Max.   :900.000  
    ##  NA's   :5562    NA's   :3834      NA's   :8260     NA's   :5562     
    ##    total_vig          adj_vig          sum_mod_vig         sum_cat         
    ##  Min.   :  0.027   Min.   :   0.055   Min.   :   0.000   Length:11933      
    ##  1st Qu.:  4.286   1st Qu.:   8.571   1st Qu.:   0.000   Class :character  
    ##  Median :  8.571   Median :  17.143   Median :   4.286   Mode  :character  
    ##  Mean   : 23.314   Mean   :  46.628   Mean   :  36.391                     
    ##  3rd Qu.: 25.714   3rd Qu.:  51.429   3rd Qu.:  38.571                     
    ##  Max.   :960.000   Max.   :1920.000   Max.   :1988.571                     
    ##  NA's   :8261      NA's   :8261                                            
    ##        INDFMPIR_group   age_gp2            educ_num        
    ##  Low-income   :   0   Length:11933       Length:11933      
    ##  Middle-income:4955   Class :character   Class :character  
    ##  High-Income  :2977   Mode  :character   Mode  :character  
    ##  NA's         :4001                                        
    ##                                                            
    ##                                                            
    ##                                                            
    ##                                 educ_factor   factor_dm   
    ##  Less than 9th grade                  : 373   No  :10371  
    ##  9-11th grade (incl. 12th, no diploma): 666   Yes : 1081  
    ##  High school grad/GED or equivalent   :1749   NA's:  481  
    ##  Some college or AA degree            :2370               
    ##  College graduate or above            :2625               
    ##  NA's                                 :4150               
    ## 

# Start analytics

``` r
str(Finalnhanes)
```

    ## tibble [11,933 × 45] (S3: tbl_df/tbl/data.frame)
    ##  $ SEQN          : num [1:11933] 130378 130379 130380 130381 130382 ...
    ##   ..- attr(*, "label")= chr "Respondent sequence number"
    ##  $ DMDEDUC2      : num [1:11933] 5 5 3 NA NA NA 2 3 4 5 ...
    ##   ..- attr(*, "label")= chr "Education level - Adults 20+"
    ##  $ RIDAGEYR      : num [1:11933] 43 66 44 5 2 3 43 65 34 68 ...
    ##   ..- attr(*, "label")= chr "Age in years at screening"
    ##  $ RIAGENDR      : Factor w/ 2 levels "Male","Female": 1 1 2 2 1 2 1 2 1 2 ...
    ##  $ RIDRETH3      : Factor w/ 6 levels "Hispanic/Latino",..: 4 2 1 5 2 1 1 2 1 2 ...
    ##  $ INDFMPIR      : num [1:11933] 5 5 1.41 1.53 3.6 NA 0.63 5 1.33 1.32 ...
    ##   ..- attr(*, "label")= chr "Ratio of family income to poverty"
    ##  $ ALQ111        : num [1:11933] NA 1 1 NA NA NA NA NA 1 1 ...
    ##   ..- attr(*, "label")= chr "Ever had a drink of any kind of alcohol"
    ##  $ ALQ121        : num [1:11933] NA 2 10 NA NA NA NA NA 4 0 ...
    ##   ..- attr(*, "label")= chr "Past 12 mos how often drink alc bev"
    ##  $ ALQ130        : num [1:11933] NA 3 1 NA NA NA NA NA 2 NA ...
    ##   ..- attr(*, "label")= chr "Avg # alcoholic drinks/day/past 12 mos"
    ##  $ ALQ142        : num [1:11933] NA 0 0 NA NA NA NA NA 10 NA ...
    ##   ..- attr(*, "label")= chr "# days have 4/5 drinks/past 12 mos"
    ##  $ ALQ270        : num [1:11933] NA NA NA NA NA NA NA NA 0 NA ...
    ##   ..- attr(*, "label")= chr "# times 4/5 drinks in 2hrs/past 12 mos"
    ##  $ ALQ280        : num [1:11933] NA NA NA NA NA NA NA NA 10 NA ...
    ##   ..- attr(*, "label")= chr "# times 8+ drinks in 1 day/past 12 mos"
    ##  $ ALQ151        : num [1:11933] NA 2 2 NA NA NA NA NA 2 2 ...
    ##   ..- attr(*, "label")= chr "Ever have 4/5 or more drinks every day"
    ##  $ ALQ170        : num [1:11933] NA NA NA NA NA NA NA NA 0 NA ...
    ##   ..- attr(*, "label")= chr "# times 4/5 drinks on occasion/past mo"
    ##  $ DIQ010        : num [1:11933] 2 2 1 2 2 2 2 2 2 2 ...
    ##   ..- attr(*, "label")= chr "Doctor told you have diabetes"
    ##  $ DID040        : num [1:11933] NA NA 35 NA NA NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "Age when first told you had diabetes"
    ##  $ DIQ160        : num [1:11933] 2 2 NA NA NA NA 2 1 2 2 ...
    ##   ..- attr(*, "label")= chr "Ever told you have prediabetes"
    ##  $ DIQ180        : num [1:11933] 2 1 NA NA NA NA 2 1 2 2 ...
    ##   ..- attr(*, "label")= chr "Had blood tested past three years"
    ##  $ DIQ050        : num [1:11933] NA NA 2 NA NA NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "Taking insulin now"
    ##  $ DID060        : num [1:11933] NA NA NA NA NA NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "How long taking insulin"
    ##  $ DIQ060U       : num [1:11933] NA NA NA NA NA NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "Unit of measure (month/year)"
    ##  $ DIQ070        : num [1:11933] NA NA 1 NA NA NA NA 2 NA NA ...
    ##   ..- attr(*, "label")= chr "Take diabetic pills to lower blood sugar"
    ##  $ PAD790Q       : num [1:11933] 3 4 1 NA NA NA 0 1 1 0 ...
    ##   ..- attr(*, "label")= chr "Frequency of moderate LTPA"
    ##  $ PAD790U       : chr [1:11933] "W" "W" "W" NA ...
    ##   ..- attr(*, "label")= chr "Moderate LTPA unit (day/week/month/year)"
    ##  $ PAD800        : num [1:11933] 45 45 20 NA NA NA NA 90 30 NA ...
    ##   ..- attr(*, "label")= chr "Minutes moderate LTPA"
    ##  $ PAD810Q       : num [1:11933] 3 3 0 NA NA NA 0 1 1 0 ...
    ##   ..- attr(*, "label")= chr "Frequency of vigorous LTPA"
    ##  $ PAD810U       : chr [1:11933] "W" "W" "" NA ...
    ##   ..- attr(*, "label")= chr "Vigorous LTPA unit (day/week/month/year)"
    ##  $ PAD820        : num [1:11933] 45 45 NA NA NA NA NA 60 30 NA ...
    ##   ..- attr(*, "label")= chr "Minutes vigorous LTPA"
    ##  $ PAD680        : num [1:11933] 360 480 240 NA NA NA 60 180 180 1200 ...
    ##   ..- attr(*, "label")= chr "Minutes sedentary activity"
    ##  $ told_pre_dm   : num [1:11933] 0 0 NA NA NA NA 0 1 0 0 ...
    ##  $ told_dm       : num [1:11933] 0 0 1 0 0 0 0 0 0 0 ...
    ##  $ freq_moderate : num [1:11933] 3 4 1 NA NA NA 0 1 1 0 ...
    ##  $ min_moderate  : num [1:11933] 45 45 20 NA NA NA NA 90 30 NA ...
    ##  $ freq_vigorous : num [1:11933] 3 3 0 NA NA NA 0 1 1 0 ...
    ##  $ min_vigorous  : num [1:11933] 45 45 NA NA NA NA NA 60 30 NA ...
    ##  $ total_mod     : num [1:11933] 19.29 25.71 2.86 NA NA ...
    ##  $ total_vig     : num [1:11933] 19.3 19.3 NA NA NA ...
    ##  $ adj_vig       : num [1:11933] 38.6 38.6 NA NA NA ...
    ##  $ sum_mod_vig   : num [1:11933] 57.86 64.29 2.86 0 0 ...
    ##  $ sum_cat       : chr [1:11933] "Less than 150" "Less than 150" "Less than 150" "Less than 150" ...
    ##  $ INDFMPIR_group: Factor w/ 3 levels "Low-income","Middle-income",..: 3 3 2 2 2 NA NA 3 2 2 ...
    ##  $ age_gp2       : chr [1:11933] "40-59" "60+" "40-59" NA ...
    ##  $ educ_num      : chr [1:11933] "5" "5" "3" NA ...
    ##  $ educ_factor   : Factor w/ 5 levels "Less than 9th grade",..: 5 5 3 NA NA NA 2 3 4 5 ...
    ##  $ factor_dm     : Factor w/ 2 levels "No","Yes": 1 1 2 1 1 1 1 1 1 1 ...
    ##  - attr(*, "label")= chr "Demographic Variables and Sample Weights"

``` r
#drop na values
Finalnhanes <- Finalnhanes %>%
    drop_na(educ_factor, told_dm, RIAGENDR, age_gp2, RIDRETH3, sum_cat, INDFMPIR_group, ALQ130)

final2 <- Finalnhanes %>%
    group_by(educ_factor, told_dm) %>%
    summarise(
        educ_num=educ_num,
        SEQN=SEQN,
        RIDAGEYR=RIDAGEYR,
        sum_mod_vig=sum_mod_vig,
        told_dm=told_dm,
        n = n(), .groups = "drop") %>%
    group_by(educ_factor) %>%
    mutate(
        totalp = sum(n, na.rm=FALSE),
        prop_dm = n/totalp,
        SE = sqrt((prop_dm * (1-prop_dm))/totalp))
```

    ## Warning: Returning more (or less) than 1 row per `summarise()` group was deprecated in
    ## dplyr 1.1.0.
    ## ℹ Please use `reframe()` instead.
    ## ℹ When switching from `summarise()` to `reframe()`, remember that `reframe()`
    ##   always returns an ungrouped data frame and adjust accordingly.
    ## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was
    ## generated.

``` r
table(final2$told_dm, useNA="ifany")    
```

    ## 
    ##    0    1 
    ## 2586  325

``` r
summary(final2)
```

    ##                                 educ_factor      told_dm      
    ##  Less than 9th grade                  :  26   Min.   :0.0000  
    ##  9-11th grade (incl. 12th, no diploma): 124   1st Qu.:0.0000  
    ##  High school grad/GED or equivalent   : 497   Median :0.0000  
    ##  Some college or AA degree            : 903   Mean   :0.1116  
    ##  College graduate or above            :1361   3rd Qu.:0.0000  
    ##                                               Max.   :1.0000  
    ##    educ_num              SEQN           RIDAGEYR      sum_mod_vig     
    ##  Length:2911        Min.   :130379   Min.   :20.00   Min.   :   0.00  
    ##  Class :character   1st Qu.:133317   1st Qu.:37.00   1st Qu.:   8.00  
    ##  Mode  :character   Median :136461   Median :56.00   Median :  27.86  
    ##                     Mean   :136366   Mean   :52.65   Mean   :  51.61  
    ##                     3rd Qu.:139345   3rd Qu.:67.00   3rd Qu.:  60.00  
    ##                     Max.   :142310   Max.   :80.00   Max.   :1234.29  
    ##        n              totalp           prop_dm                SE           
    ##  Min.   :   3.0   Min.   :    538   Min.   :6.321e-05   Min.   :6.290e-06  
    ##  1st Qu.: 417.0   1st Qu.: 635517   1st Qu.:7.886e-04   1st Qu.:2.221e-05  
    ##  Median : 789.0   Median : 635517   Median :7.886e-04   Median :2.221e-05  
    ##  Mean   : 832.8   Mean   : 975388   Mean   :1.718e-03   Mean   :1.492e-04  
    ##  3rd Qu.:1260.0   3rd Qu.:1597801   3rd Qu.:1.242e-03   3rd Qu.:4.417e-05  
    ##  Max.   :1260.0   Max.   :1597801   Max.   :4.275e-02   Max.   :8.722e-03

``` r
ggplot(final2, aes(x= educ_factor, y=prop_dm)) +
    geom_point() +
    geom_errorbar(aes(ymin=prop_dm - SE, ymax = prop_dm + SE), color= "orangered3",
                  width = 0.2)+
    labs( title = "Proportion of Diabetes for Education Level", x= "Educ Level",
          y= "Proportion of Diabetes") +
    theme_minimal() + 
    theme(
        axis.text.x = element_text(angle = 45, hjust = 1)
    )
```

![](Final_DM_by_Education_files/figure-gfm/analysis-1.png)<!-- -->

``` r
### stratify by gender
final_gender <- Finalnhanes %>%
    group_by(educ_factor, RIAGENDR, told_dm) %>%
    summarise(
        SEQN=SEQN,
        educ_factor=educ_factor,
        RIAGENDR = RIAGENDR,
        told_dm=told_dm,
        n = n(), .groups = "drop") %>%
    group_by(educ_factor) %>%
    mutate(
        totalp = sum(n, na.rm=FALSE),
        prop_dm = n/totalp,
        SE = sqrt((prop_dm * (1-prop_dm))/totalp))
```

    ## Warning: Returning more (or less) than 1 row per `summarise()` group was deprecated in
    ## dplyr 1.1.0.
    ## ℹ Please use `reframe()` instead.
    ## ℹ When switching from `summarise()` to `reframe()`, remember that `reframe()`
    ##   always returns an ungrouped data frame and adjust accordingly.
    ## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was
    ## generated.

``` r
table(final_gender$told_dm, useNA="ifany")    
```

    ## 
    ##    0    1 
    ## 2586  325

``` r
summary(final_gender)
```

    ##                                 educ_factor     RIAGENDR       told_dm      
    ##  Less than 9th grade                  :  26   Male  :1351   Min.   :0.0000  
    ##  9-11th grade (incl. 12th, no diploma): 124   Female:1560   1st Qu.:0.0000  
    ##  High school grad/GED or equivalent   : 497                 Median :0.0000  
    ##  Some college or AA degree            : 903                 Mean   :0.1116  
    ##  College graduate or above            :1361                 3rd Qu.:0.0000  
    ##                                                             Max.   :1.0000  
    ##       SEQN              n             totalp          prop_dm         
    ##  Min.   :130379   Min.   :  1.0   Min.   :   294   Min.   :5.194e-05  
    ##  1st Qu.:133317   1st Qu.:217.0   1st Qu.:323771   1st Qu.:6.938e-04  
    ##  Median :136461   Median :449.0   Median :323771   Median :8.645e-04  
    ##  Mean   :136366   Mean   :421.9   Mean   :494113   Mean   :1.718e-03  
    ##  3rd Qu.:139345   3rd Qu.:561.0   3rd Qu.:808567   3rd Qu.:1.387e-03  
    ##  Max.   :142310   Max.   :699.0   Max.   :808567   Max.   :5.102e-02  
    ##        SE           
    ##  Min.   :8.015e-06  
    ##  1st Qu.:2.928e-05  
    ##  Median :3.268e-05  
    ##  Mean   :2.038e-04  
    ##  3rd Qu.:6.540e-05  
    ##  Max.   :1.283e-02

``` r
# proportions by gender
ggplot(final_gender, aes(x = educ_factor, y = prop_dm, color = RIAGENDR)) +
    geom_point(position = position_dodge(width = 0.3)) +
    geom_errorbar(
        aes(ymin = prop_dm - SE, ymax = prop_dm + SE),
        width = 0.2,
        position = position_dodge(width = 0.3)
    ) +
    labs(
        title = "Proportion of Diabetes by Education Level and Gender",
        x = "Education Level",
        y = "Proportion with diabetes",
        color = "Gender"
    ) +
    theme_minimal() + 
    theme(
        axis.text.x = element_text(angle = 45, hjust = 1)
    )
```

![](Final_DM_by_Education_files/figure-gfm/analysis-2.png)<!-- -->

``` r
#Which gender is more likely to have the outcome for each value of educ
ggplot(final_gender, aes(x = educ_factor, y = prop_dm, color=RIAGENDR)) +
    geom_point(size = 3) +  
    geom_errorbar(aes(ymin = (prop_dm - SE),
                      ymax = (prop_dm + SE)),
                  width = 0.3) +
    labs(
        title = "Proportion of MetS by Sleep Duration",
        x = "Education Level",
        y = "Proportion with diabetes",
        color="Gender"
    ) +
    theme_minimal() 
```

![](Final_DM_by_Education_files/figure-gfm/analysis-3.png)<!-- -->

``` r
# faceted by gender 
ggplot(final_gender, aes(x = educ_factor, y = prop_dm)) +
    geom_point(size = 3, color = "orangered3") +  
    geom_errorbar(aes(ymin = (prop_dm - SE),
                      ymax = (prop_dm + SE)),
                  width = 0.3, color="orangered4") +
    labs(
        title = "Proportion of diabetes by Education Level, Faceted",
        x = "Education Level",
        y = "Proportion with diabetes",
    ) +
    facet_wrap(~ RIAGENDR) +
    theme_minimal() 
```

![](Final_DM_by_Education_files/figure-gfm/analysis-4.png)<!-- -->

# Hypothesis test

``` r
crosstabs_dm <- table(final2$told_dm, final2$educ_factor)
chisq.test(crosstabs_dm)
```

    ## Warning in chisq.test(crosstabs_dm): Chi-squared approximation may be incorrect

    ## 
    ##  Pearson's Chi-squared test
    ## 
    ## data:  crosstabs_dm
    ## X-squared = 47.438, df = 4, p-value = 1.236e-09

``` r
# model categorical
dm_model <- glm(told_dm ~ educ_factor, data = final2, family = binomial)
tbl_regression(dm_model, exponentiate = TRUE)
```

<div id="guqvcagblj" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#guqvcagblj table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
&#10;#guqvcagblj thead, #guqvcagblj tbody, #guqvcagblj tfoot, #guqvcagblj tr, #guqvcagblj td, #guqvcagblj th {
  border-style: none;
}
&#10;#guqvcagblj p {
  margin: 0;
  padding: 0;
}
&#10;#guqvcagblj .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}
&#10;#guqvcagblj .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}
&#10;#guqvcagblj .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}
&#10;#guqvcagblj .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}
&#10;#guqvcagblj .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#guqvcagblj .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#guqvcagblj .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#guqvcagblj .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}
&#10;#guqvcagblj .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}
&#10;#guqvcagblj .gt_column_spanner_outer:first-child {
  padding-left: 0;
}
&#10;#guqvcagblj .gt_column_spanner_outer:last-child {
  padding-right: 0;
}
&#10;#guqvcagblj .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}
&#10;#guqvcagblj .gt_spanner_row {
  border-bottom-style: hidden;
}
&#10;#guqvcagblj .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}
&#10;#guqvcagblj .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}
&#10;#guqvcagblj .gt_from_md > :first-child {
  margin-top: 0;
}
&#10;#guqvcagblj .gt_from_md > :last-child {
  margin-bottom: 0;
}
&#10;#guqvcagblj .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}
&#10;#guqvcagblj .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#guqvcagblj .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}
&#10;#guqvcagblj .gt_row_group_first td {
  border-top-width: 2px;
}
&#10;#guqvcagblj .gt_row_group_first th {
  border-top-width: 2px;
}
&#10;#guqvcagblj .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#guqvcagblj .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}
&#10;#guqvcagblj .gt_first_summary_row.thick {
  border-top-width: 2px;
}
&#10;#guqvcagblj .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#guqvcagblj .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#guqvcagblj .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}
&#10;#guqvcagblj .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}
&#10;#guqvcagblj .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}
&#10;#guqvcagblj .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#guqvcagblj .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#guqvcagblj .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#guqvcagblj .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#guqvcagblj .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#guqvcagblj .gt_left {
  text-align: left;
}
&#10;#guqvcagblj .gt_center {
  text-align: center;
}
&#10;#guqvcagblj .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}
&#10;#guqvcagblj .gt_font_normal {
  font-weight: normal;
}
&#10;#guqvcagblj .gt_font_bold {
  font-weight: bold;
}
&#10;#guqvcagblj .gt_font_italic {
  font-style: italic;
}
&#10;#guqvcagblj .gt_super {
  font-size: 65%;
}
&#10;#guqvcagblj .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}
&#10;#guqvcagblj .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}
&#10;#guqvcagblj .gt_indent_1 {
  text-indent: 5px;
}
&#10;#guqvcagblj .gt_indent_2 {
  text-indent: 10px;
}
&#10;#guqvcagblj .gt_indent_3 {
  text-indent: 15px;
}
&#10;#guqvcagblj .gt_indent_4 {
  text-indent: 20px;
}
&#10;#guqvcagblj .gt_indent_5 {
  text-indent: 25px;
}
&#10;#guqvcagblj .katex-display {
  display: inline-flex !important;
  margin-bottom: 0.75em !important;
}
&#10;#guqvcagblj div.Reactable > div.rt-table > div.rt-thead > div.rt-tr.rt-tr-group-header > div.rt-th-group:after {
  height: 0px !important;
}
</style>
<table class="gt_table" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
  <thead>
    <tr class="gt_col_headings">
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="label"><span class='gt_from_md'><strong>Characteristic</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="estimate"><span class='gt_from_md'><strong>OR</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="conf.low"><span class='gt_from_md'><strong>95% CI</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="p.value"><span class='gt_from_md'><strong>p-value</strong></span></th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="label" class="gt_row gt_left">educ_factor</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Less than 9th grade</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    9-11th grade (incl. 12th, no diploma)</td>
<td headers="estimate" class="gt_row gt_center">2.13</td>
<td headers="conf.low" class="gt_row gt_center">0.68, 9.47</td>
<td headers="p.value" class="gt_row gt_center">0.2</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    High school grad/GED or equivalent</td>
<td headers="estimate" class="gt_row gt_center">1.47</td>
<td headers="conf.low" class="gt_row gt_center">0.50, 6.30</td>
<td headers="p.value" class="gt_row gt_center">0.5</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Some college or AA degree</td>
<td headers="estimate" class="gt_row gt_center">1.11</td>
<td headers="conf.low" class="gt_row gt_center">0.38, 4.72</td>
<td headers="p.value" class="gt_row gt_center">0.9</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    College graduate or above</td>
<td headers="estimate" class="gt_row gt_center">0.61</td>
<td headers="conf.low" class="gt_row gt_center">0.21, 2.62</td>
<td headers="p.value" class="gt_row gt_center">0.4</td></tr>
  </tbody>
  <tfoot class="gt_sourcenotes">
    <tr>
      <td class="gt_sourcenote" colspan="4"><span class='gt_from_md'>Abbreviations: CI = Confidence Interval, OR = Odds Ratio</span></td>
    </tr>
  </tfoot>
  &#10;</table>
</div>

``` r
summary(dm_model)
```

    ## 
    ## Call:
    ## glm(formula = told_dm ~ educ_factor, family = binomial, data = final2)
    ## 
    ## Coefficients:
    ##                                                  Estimate Std. Error z value
    ## (Intercept)                                       -2.0369     0.6138  -3.318
    ## educ_factor9-11th grade (incl. 12th, no diploma)   0.7580     0.6513   1.164
    ## educ_factorHigh school grad/GED or equivalent      0.3858     0.6259   0.616
    ## educ_factorSome college or AA degree               0.1023     0.6220   0.164
    ## educ_factorCollege graduate or above              -0.4869     0.6225  -0.782
    ##                                                  Pr(>|z|)    
    ## (Intercept)                                      0.000906 ***
    ## educ_factor9-11th grade (incl. 12th, no diploma) 0.244471    
    ## educ_factorHigh school grad/GED or equivalent    0.537591    
    ## educ_factorSome college or AA degree             0.869338    
    ## educ_factorCollege graduate or above             0.434149    
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## (Dispersion parameter for binomial family taken to be 1)
    ## 
    ##     Null deviance: 2037.4  on 2910  degrees of freedom
    ## Residual deviance: 1991.7  on 2906  degrees of freedom
    ## AIC: 2001.7
    ## 
    ## Number of Fisher Scoring iterations: 5

``` r
tbl_dm_cat <- tidy(dm_model, exponentiate=TRUE, conf.int=TRUE)

# model with numeric exposure
model_dm_num <- glm(told_dm ~ educ_num, data = final2, family = binomial)


# create table: numeric
tbl_dm_num <- tidy(model_dm_num, exponentiate = TRUE, conf.int = TRUE)

tbl_dm_num$model <- "Numeric"
tbl_dm_cat$model <- "Categorical"


names(Finalnhanes)
```

    ##  [1] "SEQN"           "DMDEDUC2"       "RIDAGEYR"       "RIAGENDR"      
    ##  [5] "RIDRETH3"       "INDFMPIR"       "ALQ111"         "ALQ121"        
    ##  [9] "ALQ130"         "ALQ142"         "ALQ270"         "ALQ280"        
    ## [13] "ALQ151"         "ALQ170"         "DIQ010"         "DID040"        
    ## [17] "DIQ160"         "DIQ180"         "DIQ050"         "DID060"        
    ## [21] "DIQ060U"        "DIQ070"         "PAD790Q"        "PAD790U"       
    ## [25] "PAD800"         "PAD810Q"        "PAD810U"        "PAD820"        
    ## [29] "PAD680"         "told_pre_dm"    "told_dm"        "freq_moderate" 
    ## [33] "min_moderate"   "freq_vigorous"  "min_vigorous"   "total_mod"     
    ## [37] "total_vig"      "adj_vig"        "sum_mod_vig"    "sum_cat"       
    ## [41] "INDFMPIR_group" "age_gp2"        "educ_num"       "educ_factor"   
    ## [45] "factor_dm"

``` r
adj_dm_model <- glm(told_dm ~ educ_factor + RIAGENDR + age_gp2 + RIDRETH3 +
                       sum_cat + INDFMPIR_group+ ALQ130 + INDFMPIR_group*educ_factor, data=Finalnhanes, 
                       family=binomial)

adj_dm_model_tbl <- tidy(adj_dm_model, conf.int = TRUE, exponentiate = TRUE)
tbl_regression(adj_dm_model, exponentiate=TRUE)
```

<div id="ceoexohdli" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#ceoexohdli table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
&#10;#ceoexohdli thead, #ceoexohdli tbody, #ceoexohdli tfoot, #ceoexohdli tr, #ceoexohdli td, #ceoexohdli th {
  border-style: none;
}
&#10;#ceoexohdli p {
  margin: 0;
  padding: 0;
}
&#10;#ceoexohdli .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}
&#10;#ceoexohdli .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}
&#10;#ceoexohdli .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}
&#10;#ceoexohdli .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}
&#10;#ceoexohdli .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#ceoexohdli .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#ceoexohdli .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#ceoexohdli .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}
&#10;#ceoexohdli .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}
&#10;#ceoexohdli .gt_column_spanner_outer:first-child {
  padding-left: 0;
}
&#10;#ceoexohdli .gt_column_spanner_outer:last-child {
  padding-right: 0;
}
&#10;#ceoexohdli .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}
&#10;#ceoexohdli .gt_spanner_row {
  border-bottom-style: hidden;
}
&#10;#ceoexohdli .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}
&#10;#ceoexohdli .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}
&#10;#ceoexohdli .gt_from_md > :first-child {
  margin-top: 0;
}
&#10;#ceoexohdli .gt_from_md > :last-child {
  margin-bottom: 0;
}
&#10;#ceoexohdli .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}
&#10;#ceoexohdli .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#ceoexohdli .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}
&#10;#ceoexohdli .gt_row_group_first td {
  border-top-width: 2px;
}
&#10;#ceoexohdli .gt_row_group_first th {
  border-top-width: 2px;
}
&#10;#ceoexohdli .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#ceoexohdli .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}
&#10;#ceoexohdli .gt_first_summary_row.thick {
  border-top-width: 2px;
}
&#10;#ceoexohdli .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#ceoexohdli .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#ceoexohdli .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}
&#10;#ceoexohdli .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}
&#10;#ceoexohdli .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}
&#10;#ceoexohdli .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#ceoexohdli .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#ceoexohdli .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#ceoexohdli .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#ceoexohdli .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#ceoexohdli .gt_left {
  text-align: left;
}
&#10;#ceoexohdli .gt_center {
  text-align: center;
}
&#10;#ceoexohdli .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}
&#10;#ceoexohdli .gt_font_normal {
  font-weight: normal;
}
&#10;#ceoexohdli .gt_font_bold {
  font-weight: bold;
}
&#10;#ceoexohdli .gt_font_italic {
  font-style: italic;
}
&#10;#ceoexohdli .gt_super {
  font-size: 65%;
}
&#10;#ceoexohdli .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}
&#10;#ceoexohdli .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}
&#10;#ceoexohdli .gt_indent_1 {
  text-indent: 5px;
}
&#10;#ceoexohdli .gt_indent_2 {
  text-indent: 10px;
}
&#10;#ceoexohdli .gt_indent_3 {
  text-indent: 15px;
}
&#10;#ceoexohdli .gt_indent_4 {
  text-indent: 20px;
}
&#10;#ceoexohdli .gt_indent_5 {
  text-indent: 25px;
}
&#10;#ceoexohdli .katex-display {
  display: inline-flex !important;
  margin-bottom: 0.75em !important;
}
&#10;#ceoexohdli div.Reactable > div.rt-table > div.rt-thead > div.rt-tr.rt-tr-group-header > div.rt-th-group:after {
  height: 0px !important;
}
</style>
<table class="gt_table" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
  <thead>
    <tr class="gt_col_headings">
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="label"><span class='gt_from_md'><strong>Characteristic</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="estimate"><span class='gt_from_md'><strong>OR</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="conf.low"><span class='gt_from_md'><strong>95% CI</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="p.value"><span class='gt_from_md'><strong>p-value</strong></span></th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="label" class="gt_row gt_left">educ_factor</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Less than 9th grade</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    9-11th grade (incl. 12th, no diploma)</td>
<td headers="estimate" class="gt_row gt_center">3.18</td>
<td headers="conf.low" class="gt_row gt_center">0.79, 21.6</td>
<td headers="p.value" class="gt_row gt_center">0.2</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    High school grad/GED or equivalent</td>
<td headers="estimate" class="gt_row gt_center">2.81</td>
<td headers="conf.low" class="gt_row gt_center">0.74, 18.5</td>
<td headers="p.value" class="gt_row gt_center">0.2</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Some college or AA degree</td>
<td headers="estimate" class="gt_row gt_center">1.95</td>
<td headers="conf.low" class="gt_row gt_center">0.52, 12.9</td>
<td headers="p.value" class="gt_row gt_center">0.4</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    College graduate or above</td>
<td headers="estimate" class="gt_row gt_center">1.40</td>
<td headers="conf.low" class="gt_row gt_center">0.36, 9.33</td>
<td headers="p.value" class="gt_row gt_center">0.7</td></tr>
    <tr><td headers="label" class="gt_row gt_left">RIAGENDR</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Male</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Female</td>
<td headers="estimate" class="gt_row gt_center">0.78</td>
<td headers="conf.low" class="gt_row gt_center">0.61, 1.00</td>
<td headers="p.value" class="gt_row gt_center">0.047</td></tr>
    <tr><td headers="label" class="gt_row gt_left">age_gp2</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    20-39</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    40-59</td>
<td headers="estimate" class="gt_row gt_center">6.39</td>
<td headers="conf.low" class="gt_row gt_center">3.93, 11.1</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    60+</td>
<td headers="estimate" class="gt_row gt_center">11.0</td>
<td headers="conf.low" class="gt_row gt_center">6.72, 19.2</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">RIDRETH3</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Hispanic/Latino</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic White</td>
<td headers="estimate" class="gt_row gt_center">0.68</td>
<td headers="conf.low" class="gt_row gt_center">0.47, 0.99</td>
<td headers="p.value" class="gt_row gt_center">0.040</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic Black</td>
<td headers="estimate" class="gt_row gt_center">1.79</td>
<td headers="conf.low" class="gt_row gt_center">1.14, 2.83</td>
<td headers="p.value" class="gt_row gt_center">0.012</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic Asian</td>
<td headers="estimate" class="gt_row gt_center">0.55</td>
<td headers="conf.low" class="gt_row gt_center">0.18, 1.35</td>
<td headers="p.value" class="gt_row gt_center">0.2</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Other race</td>
<td headers="estimate" class="gt_row gt_center">1.21</td>
<td headers="conf.low" class="gt_row gt_center">0.68, 2.12</td>
<td headers="p.value" class="gt_row gt_center">0.5</td></tr>
    <tr><td headers="label" class="gt_row gt_left">sum_cat</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    150+</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Less than 150</td>
<td headers="estimate" class="gt_row gt_center">1.91</td>
<td headers="conf.low" class="gt_row gt_center">1.11, 3.53</td>
<td headers="p.value" class="gt_row gt_center">0.027</td></tr>
    <tr><td headers="label" class="gt_row gt_left">INDFMPIR_group</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Middle-income</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    High-Income</td>
<td headers="estimate" class="gt_row gt_center">3.73</td>
<td headers="conf.low" class="gt_row gt_center">0.14, 57.6</td>
<td headers="p.value" class="gt_row gt_center">0.3</td></tr>
    <tr><td headers="label" class="gt_row gt_left">Avg # alcoholic drinks/day/past 12 mos</td>
<td headers="estimate" class="gt_row gt_center">1.00</td>
<td headers="conf.low" class="gt_row gt_center">1.00, 1.00</td>
<td headers="p.value" class="gt_row gt_center">0.4</td></tr>
    <tr><td headers="label" class="gt_row gt_left">educ_factor * INDFMPIR_group</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    9-11th grade (incl. 12th, no diploma) * High-Income</td>
<td headers="estimate" class="gt_row gt_center">0.27</td>
<td headers="conf.low" class="gt_row gt_center">0.01, 8.53</td>
<td headers="p.value" class="gt_row gt_center">0.4</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    High school grad/GED or equivalent * High-Income</td>
<td headers="estimate" class="gt_row gt_center">0.16</td>
<td headers="conf.low" class="gt_row gt_center">0.01, 4.30</td>
<td headers="p.value" class="gt_row gt_center">0.2</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Some college or AA degree * High-Income</td>
<td headers="estimate" class="gt_row gt_center">0.31</td>
<td headers="conf.low" class="gt_row gt_center">0.02, 8.41</td>
<td headers="p.value" class="gt_row gt_center">0.4</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    College graduate or above * High-Income</td>
<td headers="estimate" class="gt_row gt_center">0.21</td>
<td headers="conf.low" class="gt_row gt_center">0.01, 5.61</td>
<td headers="p.value" class="gt_row gt_center">0.3</td></tr>
  </tbody>
  <tfoot class="gt_sourcenotes">
    <tr>
      <td class="gt_sourcenote" colspan="4"><span class='gt_from_md'>Abbreviations: CI = Confidence Interval, OR = Odds Ratio</span></td>
    </tr>
  </tfoot>
  &#10;</table>
</div>

``` r
adj_dm_modeldf <- adj_dm_model_tbl %>%
    mutate(
        sig = case_when(
            p.value < 0.001 ~ "***",
            p.value < 0.01 ~ "**",
            p.value < 0.05 ~ "*",
            TRUE ~ ""
        ),
        label = paste0(round(estimate, 2), " ", sig),
        color_group = ifelse(estimate > 1, "orangered3", "red4")
    )


ggplot(adj_dm_modeldf, aes(x = estimate, y = fct_rev(term), color = color_group)) +
    geom_point() +
    geom_errorbarh(aes(xmin = conf.low, xmax = conf.high), height = 0.2) +
    geom_vline(xintercept = 1, linetype = "dashed", color = "orangered4") +
    geom_text(aes(label = label), hjust = -0.3, size = 3) +
    scale_color_manual(values = c("orangered3", "red4")) +
    labs(x = "Odds Ratios", y = "", title = "Adjusted Odds Ratios with 95% CI") +
    theme_classic() +
    theme(legend.position = "none") + 
    theme(axis.text.y = element_text(angle = 45)) + 
    theme(axis.text=element_text(size=8),
            axis.title=element_text(size=12,face="bold"))
```

![](Final_DM_by_Education_files/figure-gfm/chisq-1.png)<!-- -->

``` r
clean_dm <- Finalnhanes 
```

# Step 2: Fit the full model

``` r
adj_dm_model_clean <- glm(told_dm ~ educ_factor+RIAGENDR+age_gp2+RIDRETH3+sum_cat+
                                 INDFMPIR_group+ALQ130 + INDFMPIR_group*educ_factor,data = clean_dm, family = binomial)

backward_adj_dm <- step(adj_dm_model_clean, direction = "backward")
```

    ## Start:  AIC=1860.54
    ## told_dm ~ educ_factor + RIAGENDR + age_gp2 + RIDRETH3 + sum_cat + 
    ##     INDFMPIR_group + ALQ130 + INDFMPIR_group * educ_factor
    ## 
    ##                              Df Deviance    AIC
    ## - educ_factor:INDFMPIR_group  4   1827.4 1857.4
    ## - ALQ130                      1   1823.1 1859.1
    ## <none>                            1822.5 1860.5
    ## - RIAGENDR                    1   1826.5 1862.5
    ## - sum_cat                     1   1828.2 1864.2
    ## - RIDRETH3                    4   1852.5 1882.5
    ## - age_gp2                     2   1953.6 1987.6
    ## 
    ## Step:  AIC=1857.41
    ## told_dm ~ educ_factor + RIAGENDR + age_gp2 + RIDRETH3 + sum_cat + 
    ##     INDFMPIR_group + ALQ130
    ## 
    ##                  Df Deviance    AIC
    ## - ALQ130          1   1828.0 1856.0
    ## - INDFMPIR_group  1   1828.4 1856.4
    ## <none>                1827.4 1857.4
    ## - RIAGENDR        1   1831.7 1859.7
    ## - sum_cat         1   1833.6 1861.6
    ## - educ_factor     4   1849.9 1871.9
    ## - RIDRETH3        4   1858.3 1880.3
    ## - age_gp2         2   1958.8 1984.8
    ## 
    ## Step:  AIC=1856
    ## told_dm ~ educ_factor + RIAGENDR + age_gp2 + RIDRETH3 + sum_cat + 
    ##     INDFMPIR_group
    ## 
    ##                  Df Deviance    AIC
    ## - INDFMPIR_group  1   1829.0 1855.0
    ## <none>                1828.0 1856.0
    ## - RIAGENDR        1   1832.3 1858.3
    ## - sum_cat         1   1834.2 1860.2
    ## - educ_factor     4   1850.7 1870.7
    ## - RIDRETH3        4   1859.0 1879.0
    ## - age_gp2         2   1960.6 1984.6
    ## 
    ## Step:  AIC=1855.03
    ## told_dm ~ educ_factor + RIAGENDR + age_gp2 + RIDRETH3 + sum_cat
    ## 
    ##               Df Deviance    AIC
    ## <none>             1829.0 1855.0
    ## - RIAGENDR     1   1833.1 1857.1
    ## - sum_cat      1   1835.2 1859.2
    ## - educ_factor  4   1859.2 1877.2
    ## - RIDRETH3     4   1861.5 1879.5
    ## - age_gp2      2   1960.8 1982.8

``` r
tbl_regression(backward_adj_dm, exponentiate = TRUE)
```

<div id="byuqqhdfhm" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#byuqqhdfhm table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
&#10;#byuqqhdfhm thead, #byuqqhdfhm tbody, #byuqqhdfhm tfoot, #byuqqhdfhm tr, #byuqqhdfhm td, #byuqqhdfhm th {
  border-style: none;
}
&#10;#byuqqhdfhm p {
  margin: 0;
  padding: 0;
}
&#10;#byuqqhdfhm .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}
&#10;#byuqqhdfhm .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}
&#10;#byuqqhdfhm .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}
&#10;#byuqqhdfhm .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}
&#10;#byuqqhdfhm .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#byuqqhdfhm .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#byuqqhdfhm .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#byuqqhdfhm .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}
&#10;#byuqqhdfhm .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}
&#10;#byuqqhdfhm .gt_column_spanner_outer:first-child {
  padding-left: 0;
}
&#10;#byuqqhdfhm .gt_column_spanner_outer:last-child {
  padding-right: 0;
}
&#10;#byuqqhdfhm .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}
&#10;#byuqqhdfhm .gt_spanner_row {
  border-bottom-style: hidden;
}
&#10;#byuqqhdfhm .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}
&#10;#byuqqhdfhm .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}
&#10;#byuqqhdfhm .gt_from_md > :first-child {
  margin-top: 0;
}
&#10;#byuqqhdfhm .gt_from_md > :last-child {
  margin-bottom: 0;
}
&#10;#byuqqhdfhm .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}
&#10;#byuqqhdfhm .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#byuqqhdfhm .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}
&#10;#byuqqhdfhm .gt_row_group_first td {
  border-top-width: 2px;
}
&#10;#byuqqhdfhm .gt_row_group_first th {
  border-top-width: 2px;
}
&#10;#byuqqhdfhm .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#byuqqhdfhm .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}
&#10;#byuqqhdfhm .gt_first_summary_row.thick {
  border-top-width: 2px;
}
&#10;#byuqqhdfhm .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#byuqqhdfhm .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#byuqqhdfhm .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}
&#10;#byuqqhdfhm .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}
&#10;#byuqqhdfhm .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}
&#10;#byuqqhdfhm .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#byuqqhdfhm .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#byuqqhdfhm .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#byuqqhdfhm .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#byuqqhdfhm .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#byuqqhdfhm .gt_left {
  text-align: left;
}
&#10;#byuqqhdfhm .gt_center {
  text-align: center;
}
&#10;#byuqqhdfhm .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}
&#10;#byuqqhdfhm .gt_font_normal {
  font-weight: normal;
}
&#10;#byuqqhdfhm .gt_font_bold {
  font-weight: bold;
}
&#10;#byuqqhdfhm .gt_font_italic {
  font-style: italic;
}
&#10;#byuqqhdfhm .gt_super {
  font-size: 65%;
}
&#10;#byuqqhdfhm .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}
&#10;#byuqqhdfhm .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}
&#10;#byuqqhdfhm .gt_indent_1 {
  text-indent: 5px;
}
&#10;#byuqqhdfhm .gt_indent_2 {
  text-indent: 10px;
}
&#10;#byuqqhdfhm .gt_indent_3 {
  text-indent: 15px;
}
&#10;#byuqqhdfhm .gt_indent_4 {
  text-indent: 20px;
}
&#10;#byuqqhdfhm .gt_indent_5 {
  text-indent: 25px;
}
&#10;#byuqqhdfhm .katex-display {
  display: inline-flex !important;
  margin-bottom: 0.75em !important;
}
&#10;#byuqqhdfhm div.Reactable > div.rt-table > div.rt-thead > div.rt-tr.rt-tr-group-header > div.rt-th-group:after {
  height: 0px !important;
}
</style>
<table class="gt_table" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
  <thead>
    <tr class="gt_col_headings">
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="label"><span class='gt_from_md'><strong>Characteristic</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="estimate"><span class='gt_from_md'><strong>OR</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="conf.low"><span class='gt_from_md'><strong>95% CI</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="p.value"><span class='gt_from_md'><strong>p-value</strong></span></th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="label" class="gt_row gt_left">educ_factor</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Less than 9th grade</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    9-11th grade (incl. 12th, no diploma)</td>
<td headers="estimate" class="gt_row gt_center">2.27</td>
<td headers="conf.low" class="gt_row gt_center">0.69, 10.3</td>
<td headers="p.value" class="gt_row gt_center">0.2</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    High school grad/GED or equivalent</td>
<td headers="estimate" class="gt_row gt_center">1.77</td>
<td headers="conf.low" class="gt_row gt_center">0.57, 7.74</td>
<td headers="p.value" class="gt_row gt_center">0.4</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Some college or AA degree</td>
<td headers="estimate" class="gt_row gt_center">1.47</td>
<td headers="conf.low" class="gt_row gt_center">0.48, 6.41</td>
<td headers="p.value" class="gt_row gt_center">0.5</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    College graduate or above</td>
<td headers="estimate" class="gt_row gt_center">0.84</td>
<td headers="conf.low" class="gt_row gt_center">0.27, 3.67</td>
<td headers="p.value" class="gt_row gt_center">0.8</td></tr>
    <tr><td headers="label" class="gt_row gt_left">RIAGENDR</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Male</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Female</td>
<td headers="estimate" class="gt_row gt_center">0.78</td>
<td headers="conf.low" class="gt_row gt_center">0.61, 0.99</td>
<td headers="p.value" class="gt_row gt_center">0.043</td></tr>
    <tr><td headers="label" class="gt_row gt_left">age_gp2</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    20-39</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    40-59</td>
<td headers="estimate" class="gt_row gt_center">6.28</td>
<td headers="conf.low" class="gt_row gt_center">3.87, 10.9</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    60+</td>
<td headers="estimate" class="gt_row gt_center">11.0</td>
<td headers="conf.low" class="gt_row gt_center">6.72, 19.2</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">RIDRETH3</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Hispanic/Latino</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic White</td>
<td headers="estimate" class="gt_row gt_center">0.68</td>
<td headers="conf.low" class="gt_row gt_center">0.47, 0.99</td>
<td headers="p.value" class="gt_row gt_center">0.038</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic Black</td>
<td headers="estimate" class="gt_row gt_center">1.85</td>
<td headers="conf.low" class="gt_row gt_center">1.18, 2.92</td>
<td headers="p.value" class="gt_row gt_center">0.008</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic Asian</td>
<td headers="estimate" class="gt_row gt_center">0.56</td>
<td headers="conf.low" class="gt_row gt_center">0.19, 1.37</td>
<td headers="p.value" class="gt_row gt_center">0.2</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Other race</td>
<td headers="estimate" class="gt_row gt_center">1.24</td>
<td headers="conf.low" class="gt_row gt_center">0.70, 2.16</td>
<td headers="p.value" class="gt_row gt_center">0.5</td></tr>
    <tr><td headers="label" class="gt_row gt_left">sum_cat</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    150+</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Less than 150</td>
<td headers="estimate" class="gt_row gt_center">1.96</td>
<td headers="conf.low" class="gt_row gt_center">1.14, 3.62</td>
<td headers="p.value" class="gt_row gt_center">0.022</td></tr>
  </tbody>
  <tfoot class="gt_sourcenotes">
    <tr>
      <td class="gt_sourcenote" colspan="4"><span class='gt_from_md'>Abbreviations: CI = Confidence Interval, OR = Odds Ratio</span></td>
    </tr>
  </tfoot>
  &#10;</table>
</div>

``` r
plot_dm <- tidy(backward_adj_dm, conf.int = TRUE, exponentiate = TRUE) %>%
    filter(term != "(Intercept)") %>%  # Optional: remove intercept
    mutate(
        sig = case_when(
            p.value < 0.001 ~ "***",
            p.value < 0.01 ~ "**",
            p.value < 0.05 ~ "*",
            TRUE ~ ""
        ),
        label = paste0(round(estimate, 2), " ", sig),
        color_group = ifelse(estimate > 1, "orangered3", "red4"),
        term = fct_reorder(term, estimate)  # Reorder for better plotting
    )

ggplot(plot_dm, aes(x = estimate, y = term, color = color_group)) +
    geom_point(size = 3) +
    geom_errorbarh(aes(xmin = conf.low, xmax = conf.high), height = 0.2) +
    geom_vline(xintercept = 1, linetype = "dashed", color = "orangered4") +
    geom_text(aes(label = label), hjust = -0.3, size = 3) +
    scale_color_manual(values = c("orangered3", "red4")) +
    labs(
        title = "Adjusted Odds Ratios from Backward Selection Model",
        x = "Odds Ratio",
        y = ""
    ) +
    theme_classic() +
    theme(legend.position = "none")
```

![](Final_DM_by_Education_files/figure-gfm/full-1.png)<!-- -->

# Final Model

``` r
### FINAL MODEL -DM
# inlcude significant dictors (age, phys activity) + conceptual confounders

final_dm <- glm(told_dm ~ educ_factor + RIAGENDR + age_gp2 + RIDRETH3 + 
                       sum_cat,data = clean_dm, family = binomial)
tbl_regression(final_dm, exponentiate=TRUE)
```

<div id="zousktjcsn" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#zousktjcsn table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
&#10;#zousktjcsn thead, #zousktjcsn tbody, #zousktjcsn tfoot, #zousktjcsn tr, #zousktjcsn td, #zousktjcsn th {
  border-style: none;
}
&#10;#zousktjcsn p {
  margin: 0;
  padding: 0;
}
&#10;#zousktjcsn .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}
&#10;#zousktjcsn .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}
&#10;#zousktjcsn .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}
&#10;#zousktjcsn .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}
&#10;#zousktjcsn .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#zousktjcsn .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#zousktjcsn .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#zousktjcsn .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}
&#10;#zousktjcsn .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}
&#10;#zousktjcsn .gt_column_spanner_outer:first-child {
  padding-left: 0;
}
&#10;#zousktjcsn .gt_column_spanner_outer:last-child {
  padding-right: 0;
}
&#10;#zousktjcsn .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}
&#10;#zousktjcsn .gt_spanner_row {
  border-bottom-style: hidden;
}
&#10;#zousktjcsn .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}
&#10;#zousktjcsn .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}
&#10;#zousktjcsn .gt_from_md > :first-child {
  margin-top: 0;
}
&#10;#zousktjcsn .gt_from_md > :last-child {
  margin-bottom: 0;
}
&#10;#zousktjcsn .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}
&#10;#zousktjcsn .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#zousktjcsn .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}
&#10;#zousktjcsn .gt_row_group_first td {
  border-top-width: 2px;
}
&#10;#zousktjcsn .gt_row_group_first th {
  border-top-width: 2px;
}
&#10;#zousktjcsn .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#zousktjcsn .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}
&#10;#zousktjcsn .gt_first_summary_row.thick {
  border-top-width: 2px;
}
&#10;#zousktjcsn .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#zousktjcsn .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#zousktjcsn .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}
&#10;#zousktjcsn .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}
&#10;#zousktjcsn .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}
&#10;#zousktjcsn .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#zousktjcsn .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#zousktjcsn .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#zousktjcsn .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#zousktjcsn .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#zousktjcsn .gt_left {
  text-align: left;
}
&#10;#zousktjcsn .gt_center {
  text-align: center;
}
&#10;#zousktjcsn .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}
&#10;#zousktjcsn .gt_font_normal {
  font-weight: normal;
}
&#10;#zousktjcsn .gt_font_bold {
  font-weight: bold;
}
&#10;#zousktjcsn .gt_font_italic {
  font-style: italic;
}
&#10;#zousktjcsn .gt_super {
  font-size: 65%;
}
&#10;#zousktjcsn .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}
&#10;#zousktjcsn .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}
&#10;#zousktjcsn .gt_indent_1 {
  text-indent: 5px;
}
&#10;#zousktjcsn .gt_indent_2 {
  text-indent: 10px;
}
&#10;#zousktjcsn .gt_indent_3 {
  text-indent: 15px;
}
&#10;#zousktjcsn .gt_indent_4 {
  text-indent: 20px;
}
&#10;#zousktjcsn .gt_indent_5 {
  text-indent: 25px;
}
&#10;#zousktjcsn .katex-display {
  display: inline-flex !important;
  margin-bottom: 0.75em !important;
}
&#10;#zousktjcsn div.Reactable > div.rt-table > div.rt-thead > div.rt-tr.rt-tr-group-header > div.rt-th-group:after {
  height: 0px !important;
}
</style>
<table class="gt_table" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
  <thead>
    <tr class="gt_col_headings">
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="label"><span class='gt_from_md'><strong>Characteristic</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="estimate"><span class='gt_from_md'><strong>OR</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="conf.low"><span class='gt_from_md'><strong>95% CI</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="p.value"><span class='gt_from_md'><strong>p-value</strong></span></th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="label" class="gt_row gt_left">educ_factor</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Less than 9th grade</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    9-11th grade (incl. 12th, no diploma)</td>
<td headers="estimate" class="gt_row gt_center">2.27</td>
<td headers="conf.low" class="gt_row gt_center">0.69, 10.3</td>
<td headers="p.value" class="gt_row gt_center">0.2</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    High school grad/GED or equivalent</td>
<td headers="estimate" class="gt_row gt_center">1.77</td>
<td headers="conf.low" class="gt_row gt_center">0.57, 7.74</td>
<td headers="p.value" class="gt_row gt_center">0.4</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Some college or AA degree</td>
<td headers="estimate" class="gt_row gt_center">1.47</td>
<td headers="conf.low" class="gt_row gt_center">0.48, 6.41</td>
<td headers="p.value" class="gt_row gt_center">0.5</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    College graduate or above</td>
<td headers="estimate" class="gt_row gt_center">0.84</td>
<td headers="conf.low" class="gt_row gt_center">0.27, 3.67</td>
<td headers="p.value" class="gt_row gt_center">0.8</td></tr>
    <tr><td headers="label" class="gt_row gt_left">RIAGENDR</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Male</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Female</td>
<td headers="estimate" class="gt_row gt_center">0.78</td>
<td headers="conf.low" class="gt_row gt_center">0.61, 0.99</td>
<td headers="p.value" class="gt_row gt_center">0.043</td></tr>
    <tr><td headers="label" class="gt_row gt_left">age_gp2</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    20-39</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    40-59</td>
<td headers="estimate" class="gt_row gt_center">6.28</td>
<td headers="conf.low" class="gt_row gt_center">3.87, 10.9</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    60+</td>
<td headers="estimate" class="gt_row gt_center">11.0</td>
<td headers="conf.low" class="gt_row gt_center">6.72, 19.2</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">RIDRETH3</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Hispanic/Latino</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic White</td>
<td headers="estimate" class="gt_row gt_center">0.68</td>
<td headers="conf.low" class="gt_row gt_center">0.47, 0.99</td>
<td headers="p.value" class="gt_row gt_center">0.038</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic Black</td>
<td headers="estimate" class="gt_row gt_center">1.85</td>
<td headers="conf.low" class="gt_row gt_center">1.18, 2.92</td>
<td headers="p.value" class="gt_row gt_center">0.008</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic Asian</td>
<td headers="estimate" class="gt_row gt_center">0.56</td>
<td headers="conf.low" class="gt_row gt_center">0.19, 1.37</td>
<td headers="p.value" class="gt_row gt_center">0.2</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Other race</td>
<td headers="estimate" class="gt_row gt_center">1.24</td>
<td headers="conf.low" class="gt_row gt_center">0.70, 2.16</td>
<td headers="p.value" class="gt_row gt_center">0.5</td></tr>
    <tr><td headers="label" class="gt_row gt_left">sum_cat</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    150+</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Less than 150</td>
<td headers="estimate" class="gt_row gt_center">1.96</td>
<td headers="conf.low" class="gt_row gt_center">1.14, 3.62</td>
<td headers="p.value" class="gt_row gt_center">0.022</td></tr>
  </tbody>
  <tfoot class="gt_sourcenotes">
    <tr>
      <td class="gt_sourcenote" colspan="4"><span class='gt_from_md'>Abbreviations: CI = Confidence Interval, OR = Odds Ratio</span></td>
    </tr>
  </tfoot>
  &#10;</table>
</div>

``` r
final_dm <- tidy(final_dm, conf.int = TRUE, exponentiate = TRUE) %>%
    filter(term != "(Intercept)") %>%  # Optional: remove intercept
    mutate(
        sig = case_when(
            p.value < 0.001 ~ "***",
            p.value < 0.01 ~ "**",
            p.value < 0.05 ~ "*",
            TRUE ~ ""
        ),
        label = paste0(round(estimate, 2), " ", sig),
        color_group = ifelse(estimate > 1, "orangered3", "red4"),
        term = fct_reorder(term, estimate  # Reorder for better plotting
    ))

ggplot(final_dm, aes(x = estimate, y = term, color = color_group)) +
    geom_point(size = 3) +
    geom_errorbarh(aes(xmin = conf.low, xmax = conf.high), height = 0.2) +
    geom_vline(xintercept = 1, linetype = "dashed", color = "orangered4") +
    geom_text(aes(label = label), hjust = -0.3, size = 3) +
    scale_color_manual(values = c("orangered3", "red4")) +
    labs(
        title = "Adjusted Odds Ratios from Backward Selection Model",
        x = "Odds Ratio",
        y = ""
    ) +
    theme_classic() +
    theme(legend.position = "none")
```

![](Final_DM_by_Education_files/figure-gfm/unnamed-chunk-1-1.png)<!-- -->

# Stratify by ses

    ## Warning: Returning more (or less) than 1 row per `summarise()` group was deprecated in
    ## dplyr 1.1.0.
    ## ℹ Please use `reframe()` instead.
    ## ℹ When switching from `summarise()` to `reframe()`, remember that `reframe()`
    ##   always returns an ungrouped data frame and adjust accordingly.
    ## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was
    ## generated.

    ## 
    ##    0    1 
    ## 2586  325

    ##                                 educ_factor         INDFMPIR_group
    ##  Less than 9th grade                  :  26   Low-income   :   0  
    ##  9-11th grade (incl. 12th, no diploma): 124   Middle-income:1516  
    ##  High school grad/GED or equivalent   : 497   High-Income  :1395  
    ##  Some college or AA degree            : 903                       
    ##  College graduate or above            :1361                       
    ##                                                                   
    ##     told_dm            SEQN              n             totalp      
    ##  Min.   :0.0000   Min.   :130379   Min.   :  1.0   Min.   :   414  
    ##  1st Qu.:0.0000   1st Qu.:133317   1st Qu.:264.0   1st Qu.:352107  
    ##  Median :0.0000   Median :136461   Median :396.0   Median :352107  
    ##  Mean   :0.1116   Mean   :136366   Mean   :472.5   Mean   :552605  
    ##  3rd Qu.:0.0000   3rd Qu.:139345   3rd Qu.:864.0   3rd Qu.:908777  
    ##  Max.   :1.0000   Max.   :142310   Max.   :864.0   Max.   :908777  
    ##     prop_dm                SE           
    ##  Min.   :4.071e-05   Min.   :6.693e-06  
    ##  1st Qu.:7.498e-04   1st Qu.:3.233e-05  
    ##  Median :9.507e-04   Median :3.233e-05  
    ##  Mean   :1.718e-03   Mean   :1.732e-04  
    ##  3rd Qu.:1.491e-03   3rd Qu.:6.502e-05  
    ##  Max.   :4.831e-02   Max.   :1.054e-02

<div id="duyvrisfhq" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#duyvrisfhq table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
&#10;#duyvrisfhq thead, #duyvrisfhq tbody, #duyvrisfhq tfoot, #duyvrisfhq tr, #duyvrisfhq td, #duyvrisfhq th {
  border-style: none;
}
&#10;#duyvrisfhq p {
  margin: 0;
  padding: 0;
}
&#10;#duyvrisfhq .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}
&#10;#duyvrisfhq .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}
&#10;#duyvrisfhq .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}
&#10;#duyvrisfhq .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}
&#10;#duyvrisfhq .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#duyvrisfhq .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#duyvrisfhq .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#duyvrisfhq .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}
&#10;#duyvrisfhq .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}
&#10;#duyvrisfhq .gt_column_spanner_outer:first-child {
  padding-left: 0;
}
&#10;#duyvrisfhq .gt_column_spanner_outer:last-child {
  padding-right: 0;
}
&#10;#duyvrisfhq .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}
&#10;#duyvrisfhq .gt_spanner_row {
  border-bottom-style: hidden;
}
&#10;#duyvrisfhq .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}
&#10;#duyvrisfhq .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}
&#10;#duyvrisfhq .gt_from_md > :first-child {
  margin-top: 0;
}
&#10;#duyvrisfhq .gt_from_md > :last-child {
  margin-bottom: 0;
}
&#10;#duyvrisfhq .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}
&#10;#duyvrisfhq .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#duyvrisfhq .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}
&#10;#duyvrisfhq .gt_row_group_first td {
  border-top-width: 2px;
}
&#10;#duyvrisfhq .gt_row_group_first th {
  border-top-width: 2px;
}
&#10;#duyvrisfhq .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#duyvrisfhq .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}
&#10;#duyvrisfhq .gt_first_summary_row.thick {
  border-top-width: 2px;
}
&#10;#duyvrisfhq .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#duyvrisfhq .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#duyvrisfhq .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}
&#10;#duyvrisfhq .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}
&#10;#duyvrisfhq .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}
&#10;#duyvrisfhq .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#duyvrisfhq .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#duyvrisfhq .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#duyvrisfhq .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#duyvrisfhq .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#duyvrisfhq .gt_left {
  text-align: left;
}
&#10;#duyvrisfhq .gt_center {
  text-align: center;
}
&#10;#duyvrisfhq .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}
&#10;#duyvrisfhq .gt_font_normal {
  font-weight: normal;
}
&#10;#duyvrisfhq .gt_font_bold {
  font-weight: bold;
}
&#10;#duyvrisfhq .gt_font_italic {
  font-style: italic;
}
&#10;#duyvrisfhq .gt_super {
  font-size: 65%;
}
&#10;#duyvrisfhq .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}
&#10;#duyvrisfhq .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}
&#10;#duyvrisfhq .gt_indent_1 {
  text-indent: 5px;
}
&#10;#duyvrisfhq .gt_indent_2 {
  text-indent: 10px;
}
&#10;#duyvrisfhq .gt_indent_3 {
  text-indent: 15px;
}
&#10;#duyvrisfhq .gt_indent_4 {
  text-indent: 20px;
}
&#10;#duyvrisfhq .gt_indent_5 {
  text-indent: 25px;
}
&#10;#duyvrisfhq .katex-display {
  display: inline-flex !important;
  margin-bottom: 0.75em !important;
}
&#10;#duyvrisfhq div.Reactable > div.rt-table > div.rt-thead > div.rt-tr.rt-tr-group-header > div.rt-th-group:after {
  height: 0px !important;
}
</style>
<table class="gt_table" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
  <thead>
    <tr class="gt_col_headings">
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="label"><span class='gt_from_md'><strong>Characteristic</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="stat_0"><span class='gt_from_md'><strong>N = 2,911</strong></span><span class="gt_footnote_marks" style="white-space:nowrap;font-style:italic;font-weight:normal;line-height:0;"><sup>1</sup></span></th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="label" class="gt_row gt_left">educ_factor</td>
<td headers="stat_0" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Less than 9th grade</td>
<td headers="stat_0" class="gt_row gt_center">26 (0.9%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    9-11th grade (incl. 12th, no diploma)</td>
<td headers="stat_0" class="gt_row gt_center">124 (4.3%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    High school grad/GED or equivalent</td>
<td headers="stat_0" class="gt_row gt_center">497 (17%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Some college or AA degree</td>
<td headers="stat_0" class="gt_row gt_center">903 (31%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    College graduate or above</td>
<td headers="stat_0" class="gt_row gt_center">1,361 (47%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">INDFMPIR_group</td>
<td headers="stat_0" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Low-income</td>
<td headers="stat_0" class="gt_row gt_center">0 (0%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Middle-income</td>
<td headers="stat_0" class="gt_row gt_center">1,516 (52%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    High-Income</td>
<td headers="stat_0" class="gt_row gt_center">1,395 (48%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">told_dm</td>
<td headers="stat_0" class="gt_row gt_center">325 (11%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">SEQN</td>
<td headers="stat_0" class="gt_row gt_center">136,461 (133,316, 139,347)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">n</td>
<td headers="stat_0" class="gt_row gt_center">396 (264, 864)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">totalp</td>
<td headers="stat_0" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    414</td>
<td headers="stat_0" class="gt_row gt_center">26 (0.9%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    7770</td>
<td headers="stat_0" class="gt_row gt_center">124 (4.3%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    106359</td>
<td headers="stat_0" class="gt_row gt_center">497 (17%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    352107</td>
<td headers="stat_0" class="gt_row gt_center">903 (31%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    908777</td>
<td headers="stat_0" class="gt_row gt_center">1,361 (47%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">prop_dm</td>
<td headers="stat_0" class="gt_row gt_center">0.0010 (0.0007, 0.0015)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">SE</td>
<td headers="stat_0" class="gt_row gt_center">0.0000 (0.0000, 0.0001)</td></tr>
  </tbody>
  &#10;  <tfoot class="gt_footnotes">
    <tr>
      <td class="gt_footnote" colspan="2"><span class="gt_footnote_marks" style="white-space:nowrap;font-style:italic;font-weight:normal;line-height:0;"><sup>1</sup></span> <span class='gt_from_md'>n (%); Median (Q1, Q3)</span></td>
    </tr>
  </tfoot>
</table>
</div>

![](Final_DM_by_Education_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

\#Interaction Term

``` r
names(Finalnhanes)
```

    ##  [1] "SEQN"           "DMDEDUC2"       "RIDAGEYR"       "RIAGENDR"      
    ##  [5] "RIDRETH3"       "INDFMPIR"       "ALQ111"         "ALQ121"        
    ##  [9] "ALQ130"         "ALQ142"         "ALQ270"         "ALQ280"        
    ## [13] "ALQ151"         "ALQ170"         "DIQ010"         "DID040"        
    ## [17] "DIQ160"         "DIQ180"         "DIQ050"         "DID060"        
    ## [21] "DIQ060U"        "DIQ070"         "PAD790Q"        "PAD790U"       
    ## [25] "PAD800"         "PAD810Q"        "PAD810U"        "PAD820"        
    ## [29] "PAD680"         "told_pre_dm"    "told_dm"        "freq_moderate" 
    ## [33] "min_moderate"   "freq_vigorous"  "min_vigorous"   "total_mod"     
    ## [37] "total_vig"      "adj_vig"        "sum_mod_vig"    "sum_cat"       
    ## [41] "INDFMPIR_group" "age_gp2"        "educ_num"       "educ_factor"   
    ## [45] "factor_dm"

``` r
adj_dm_model <- glm(told_dm ~ educ_factor + RIAGENDR + age_gp2 + RIDRETH3 +
                        sum_cat + INDFMPIR_group+ ALQ130, data=Finalnhanes, 
                    family=binomial)

adj_dm_model_tbl <- tidy(adj_dm_model, conf.int = TRUE, exponentiate = TRUE)
tbl_regression(adj_dm_model, exponentiate=TRUE)
```

<div id="lydfollzur" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#lydfollzur table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
&#10;#lydfollzur thead, #lydfollzur tbody, #lydfollzur tfoot, #lydfollzur tr, #lydfollzur td, #lydfollzur th {
  border-style: none;
}
&#10;#lydfollzur p {
  margin: 0;
  padding: 0;
}
&#10;#lydfollzur .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}
&#10;#lydfollzur .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}
&#10;#lydfollzur .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}
&#10;#lydfollzur .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}
&#10;#lydfollzur .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#lydfollzur .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#lydfollzur .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#lydfollzur .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}
&#10;#lydfollzur .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}
&#10;#lydfollzur .gt_column_spanner_outer:first-child {
  padding-left: 0;
}
&#10;#lydfollzur .gt_column_spanner_outer:last-child {
  padding-right: 0;
}
&#10;#lydfollzur .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}
&#10;#lydfollzur .gt_spanner_row {
  border-bottom-style: hidden;
}
&#10;#lydfollzur .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}
&#10;#lydfollzur .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}
&#10;#lydfollzur .gt_from_md > :first-child {
  margin-top: 0;
}
&#10;#lydfollzur .gt_from_md > :last-child {
  margin-bottom: 0;
}
&#10;#lydfollzur .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}
&#10;#lydfollzur .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#lydfollzur .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}
&#10;#lydfollzur .gt_row_group_first td {
  border-top-width: 2px;
}
&#10;#lydfollzur .gt_row_group_first th {
  border-top-width: 2px;
}
&#10;#lydfollzur .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#lydfollzur .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}
&#10;#lydfollzur .gt_first_summary_row.thick {
  border-top-width: 2px;
}
&#10;#lydfollzur .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#lydfollzur .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#lydfollzur .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}
&#10;#lydfollzur .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}
&#10;#lydfollzur .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}
&#10;#lydfollzur .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#lydfollzur .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#lydfollzur .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#lydfollzur .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#lydfollzur .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#lydfollzur .gt_left {
  text-align: left;
}
&#10;#lydfollzur .gt_center {
  text-align: center;
}
&#10;#lydfollzur .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}
&#10;#lydfollzur .gt_font_normal {
  font-weight: normal;
}
&#10;#lydfollzur .gt_font_bold {
  font-weight: bold;
}
&#10;#lydfollzur .gt_font_italic {
  font-style: italic;
}
&#10;#lydfollzur .gt_super {
  font-size: 65%;
}
&#10;#lydfollzur .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}
&#10;#lydfollzur .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}
&#10;#lydfollzur .gt_indent_1 {
  text-indent: 5px;
}
&#10;#lydfollzur .gt_indent_2 {
  text-indent: 10px;
}
&#10;#lydfollzur .gt_indent_3 {
  text-indent: 15px;
}
&#10;#lydfollzur .gt_indent_4 {
  text-indent: 20px;
}
&#10;#lydfollzur .gt_indent_5 {
  text-indent: 25px;
}
&#10;#lydfollzur .katex-display {
  display: inline-flex !important;
  margin-bottom: 0.75em !important;
}
&#10;#lydfollzur div.Reactable > div.rt-table > div.rt-thead > div.rt-tr.rt-tr-group-header > div.rt-th-group:after {
  height: 0px !important;
}
</style>
<table class="gt_table" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
  <thead>
    <tr class="gt_col_headings">
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="label"><span class='gt_from_md'><strong>Characteristic</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="estimate"><span class='gt_from_md'><strong>OR</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="conf.low"><span class='gt_from_md'><strong>95% CI</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="p.value"><span class='gt_from_md'><strong>p-value</strong></span></th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="label" class="gt_row gt_left">educ_factor</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Less than 9th grade</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    9-11th grade (incl. 12th, no diploma)</td>
<td headers="estimate" class="gt_row gt_center">2.36</td>
<td headers="conf.low" class="gt_row gt_center">0.71, 10.9</td>
<td headers="p.value" class="gt_row gt_center">0.2</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    High school grad/GED or equivalent</td>
<td headers="estimate" class="gt_row gt_center">1.86</td>
<td headers="conf.low" class="gt_row gt_center">0.60, 8.24</td>
<td headers="p.value" class="gt_row gt_center">0.3</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Some college or AA degree</td>
<td headers="estimate" class="gt_row gt_center">1.57</td>
<td headers="conf.low" class="gt_row gt_center">0.51, 6.98</td>
<td headers="p.value" class="gt_row gt_center">0.5</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    College graduate or above</td>
<td headers="estimate" class="gt_row gt_center">0.94</td>
<td headers="conf.low" class="gt_row gt_center">0.30, 4.18</td>
<td headers="p.value" class="gt_row gt_center">>0.9</td></tr>
    <tr><td headers="label" class="gt_row gt_left">RIAGENDR</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Male</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Female</td>
<td headers="estimate" class="gt_row gt_center">0.77</td>
<td headers="conf.low" class="gt_row gt_center">0.61, 0.99</td>
<td headers="p.value" class="gt_row gt_center">0.039</td></tr>
    <tr><td headers="label" class="gt_row gt_left">age_gp2</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    20-39</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    40-59</td>
<td headers="estimate" class="gt_row gt_center">6.39</td>
<td headers="conf.low" class="gt_row gt_center">3.93, 11.1</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    60+</td>
<td headers="estimate" class="gt_row gt_center">11.0</td>
<td headers="conf.low" class="gt_row gt_center">6.72, 19.2</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">RIDRETH3</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Hispanic/Latino</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic White</td>
<td headers="estimate" class="gt_row gt_center">0.69</td>
<td headers="conf.low" class="gt_row gt_center">0.48, 1.01</td>
<td headers="p.value" class="gt_row gt_center">0.048</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic Black</td>
<td headers="estimate" class="gt_row gt_center">1.84</td>
<td headers="conf.low" class="gt_row gt_center">1.17, 2.91</td>
<td headers="p.value" class="gt_row gt_center">0.008</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic Asian</td>
<td headers="estimate" class="gt_row gt_center">0.55</td>
<td headers="conf.low" class="gt_row gt_center">0.18, 1.36</td>
<td headers="p.value" class="gt_row gt_center">0.2</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Other race</td>
<td headers="estimate" class="gt_row gt_center">1.25</td>
<td headers="conf.low" class="gt_row gt_center">0.70, 2.17</td>
<td headers="p.value" class="gt_row gt_center">0.4</td></tr>
    <tr><td headers="label" class="gt_row gt_left">sum_cat</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    150+</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Less than 150</td>
<td headers="estimate" class="gt_row gt_center">1.96</td>
<td headers="conf.low" class="gt_row gt_center">1.14, 3.63</td>
<td headers="p.value" class="gt_row gt_center">0.021</td></tr>
    <tr><td headers="label" class="gt_row gt_left">INDFMPIR_group</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Middle-income</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    High-Income</td>
<td headers="estimate" class="gt_row gt_center">0.88</td>
<td headers="conf.low" class="gt_row gt_center">0.67, 1.14</td>
<td headers="p.value" class="gt_row gt_center">0.3</td></tr>
    <tr><td headers="label" class="gt_row gt_left">Avg # alcoholic drinks/day/past 12 mos</td>
<td headers="estimate" class="gt_row gt_center">1.00</td>
<td headers="conf.low" class="gt_row gt_center">1.00, 1.00</td>
<td headers="p.value" class="gt_row gt_center">0.4</td></tr>
  </tbody>
  <tfoot class="gt_sourcenotes">
    <tr>
      <td class="gt_sourcenote" colspan="4"><span class='gt_from_md'>Abbreviations: CI = Confidence Interval, OR = Odds Ratio</span></td>
    </tr>
  </tfoot>
  &#10;</table>
</div>

``` r
adj_dm_modeldf <- adj_dm_model_tbl %>%
    mutate(
        sig = case_when(
            p.value < 0.001 ~ "***",
            p.value < 0.01 ~ "**",
            p.value < 0.05 ~ "*",
            TRUE ~ ""
        ),
        label = paste0(round(estimate, 2), " ", sig),
        color_group = ifelse(estimate > 1, "blue", "red")
    )


ggplot(adj_dm_modeldf, aes(x = estimate, y = fct_rev(term), color = color_group)) +
    geom_point() +
    geom_errorbarh(aes(xmin = conf.low, xmax = conf.high), height = 0.2) +
    geom_vline(xintercept = 1, linetype = "dashed", color = "black") +
    geom_text(aes(label = label), hjust = -0.3, size = 3) +
    scale_color_manual(values = c("orangered3", "red4")) +
    labs(x = "Odds Ratios", y = "", title = "Adjusted Odds Ratios with 95% CI") +
    theme_classic() +
    theme(legend.position = "none") +
    theme(
        axis.text.y = element_text(angle = 45, hjust = 1)
    )
```

![](Final_DM_by_Education_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

``` r
clean_dm <- Finalnhanes 
```

# Step 2: Fit the full model

``` r
adj_dm_model_clean <- glm(told_dm ~ educ_factor+RIAGENDR+age_gp2+RIDRETH3+sum_cat+
                              INDFMPIR_group+ALQ130 + INDFMPIR_group*educ_factor,
                          data = clean_dm, family = binomial)

backward_adj_dm <- step(adj_dm_model_clean, direction = "backward")
```

    ## Start:  AIC=1860.54
    ## told_dm ~ educ_factor + RIAGENDR + age_gp2 + RIDRETH3 + sum_cat + 
    ##     INDFMPIR_group + ALQ130 + INDFMPIR_group * educ_factor
    ## 
    ##                              Df Deviance    AIC
    ## - educ_factor:INDFMPIR_group  4   1827.4 1857.4
    ## - ALQ130                      1   1823.1 1859.1
    ## <none>                            1822.5 1860.5
    ## - RIAGENDR                    1   1826.5 1862.5
    ## - sum_cat                     1   1828.2 1864.2
    ## - RIDRETH3                    4   1852.5 1882.5
    ## - age_gp2                     2   1953.6 1987.6
    ## 
    ## Step:  AIC=1857.41
    ## told_dm ~ educ_factor + RIAGENDR + age_gp2 + RIDRETH3 + sum_cat + 
    ##     INDFMPIR_group + ALQ130
    ## 
    ##                  Df Deviance    AIC
    ## - ALQ130          1   1828.0 1856.0
    ## - INDFMPIR_group  1   1828.4 1856.4
    ## <none>                1827.4 1857.4
    ## - RIAGENDR        1   1831.7 1859.7
    ## - sum_cat         1   1833.6 1861.6
    ## - educ_factor     4   1849.9 1871.9
    ## - RIDRETH3        4   1858.3 1880.3
    ## - age_gp2         2   1958.8 1984.8
    ## 
    ## Step:  AIC=1856
    ## told_dm ~ educ_factor + RIAGENDR + age_gp2 + RIDRETH3 + sum_cat + 
    ##     INDFMPIR_group
    ## 
    ##                  Df Deviance    AIC
    ## - INDFMPIR_group  1   1829.0 1855.0
    ## <none>                1828.0 1856.0
    ## - RIAGENDR        1   1832.3 1858.3
    ## - sum_cat         1   1834.2 1860.2
    ## - educ_factor     4   1850.7 1870.7
    ## - RIDRETH3        4   1859.0 1879.0
    ## - age_gp2         2   1960.6 1984.6
    ## 
    ## Step:  AIC=1855.03
    ## told_dm ~ educ_factor + RIAGENDR + age_gp2 + RIDRETH3 + sum_cat
    ## 
    ##               Df Deviance    AIC
    ## <none>             1829.0 1855.0
    ## - RIAGENDR     1   1833.1 1857.1
    ## - sum_cat      1   1835.2 1859.2
    ## - educ_factor  4   1859.2 1877.2
    ## - RIDRETH3     4   1861.5 1879.5
    ## - age_gp2      2   1960.8 1982.8

``` r
tbl_regression(backward_adj_dm, exponentiate = TRUE)
```

<div id="rdvsmyavyy" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#rdvsmyavyy table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
&#10;#rdvsmyavyy thead, #rdvsmyavyy tbody, #rdvsmyavyy tfoot, #rdvsmyavyy tr, #rdvsmyavyy td, #rdvsmyavyy th {
  border-style: none;
}
&#10;#rdvsmyavyy p {
  margin: 0;
  padding: 0;
}
&#10;#rdvsmyavyy .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}
&#10;#rdvsmyavyy .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}
&#10;#rdvsmyavyy .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}
&#10;#rdvsmyavyy .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}
&#10;#rdvsmyavyy .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#rdvsmyavyy .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#rdvsmyavyy .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#rdvsmyavyy .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}
&#10;#rdvsmyavyy .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}
&#10;#rdvsmyavyy .gt_column_spanner_outer:first-child {
  padding-left: 0;
}
&#10;#rdvsmyavyy .gt_column_spanner_outer:last-child {
  padding-right: 0;
}
&#10;#rdvsmyavyy .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}
&#10;#rdvsmyavyy .gt_spanner_row {
  border-bottom-style: hidden;
}
&#10;#rdvsmyavyy .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}
&#10;#rdvsmyavyy .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}
&#10;#rdvsmyavyy .gt_from_md > :first-child {
  margin-top: 0;
}
&#10;#rdvsmyavyy .gt_from_md > :last-child {
  margin-bottom: 0;
}
&#10;#rdvsmyavyy .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}
&#10;#rdvsmyavyy .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#rdvsmyavyy .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}
&#10;#rdvsmyavyy .gt_row_group_first td {
  border-top-width: 2px;
}
&#10;#rdvsmyavyy .gt_row_group_first th {
  border-top-width: 2px;
}
&#10;#rdvsmyavyy .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#rdvsmyavyy .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}
&#10;#rdvsmyavyy .gt_first_summary_row.thick {
  border-top-width: 2px;
}
&#10;#rdvsmyavyy .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#rdvsmyavyy .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#rdvsmyavyy .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}
&#10;#rdvsmyavyy .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}
&#10;#rdvsmyavyy .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}
&#10;#rdvsmyavyy .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#rdvsmyavyy .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#rdvsmyavyy .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#rdvsmyavyy .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#rdvsmyavyy .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#rdvsmyavyy .gt_left {
  text-align: left;
}
&#10;#rdvsmyavyy .gt_center {
  text-align: center;
}
&#10;#rdvsmyavyy .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}
&#10;#rdvsmyavyy .gt_font_normal {
  font-weight: normal;
}
&#10;#rdvsmyavyy .gt_font_bold {
  font-weight: bold;
}
&#10;#rdvsmyavyy .gt_font_italic {
  font-style: italic;
}
&#10;#rdvsmyavyy .gt_super {
  font-size: 65%;
}
&#10;#rdvsmyavyy .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}
&#10;#rdvsmyavyy .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}
&#10;#rdvsmyavyy .gt_indent_1 {
  text-indent: 5px;
}
&#10;#rdvsmyavyy .gt_indent_2 {
  text-indent: 10px;
}
&#10;#rdvsmyavyy .gt_indent_3 {
  text-indent: 15px;
}
&#10;#rdvsmyavyy .gt_indent_4 {
  text-indent: 20px;
}
&#10;#rdvsmyavyy .gt_indent_5 {
  text-indent: 25px;
}
&#10;#rdvsmyavyy .katex-display {
  display: inline-flex !important;
  margin-bottom: 0.75em !important;
}
&#10;#rdvsmyavyy div.Reactable > div.rt-table > div.rt-thead > div.rt-tr.rt-tr-group-header > div.rt-th-group:after {
  height: 0px !important;
}
</style>
<table class="gt_table" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
  <thead>
    <tr class="gt_col_headings">
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="label"><span class='gt_from_md'><strong>Characteristic</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="estimate"><span class='gt_from_md'><strong>OR</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="conf.low"><span class='gt_from_md'><strong>95% CI</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="p.value"><span class='gt_from_md'><strong>p-value</strong></span></th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="label" class="gt_row gt_left">educ_factor</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Less than 9th grade</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    9-11th grade (incl. 12th, no diploma)</td>
<td headers="estimate" class="gt_row gt_center">2.27</td>
<td headers="conf.low" class="gt_row gt_center">0.69, 10.3</td>
<td headers="p.value" class="gt_row gt_center">0.2</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    High school grad/GED or equivalent</td>
<td headers="estimate" class="gt_row gt_center">1.77</td>
<td headers="conf.low" class="gt_row gt_center">0.57, 7.74</td>
<td headers="p.value" class="gt_row gt_center">0.4</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Some college or AA degree</td>
<td headers="estimate" class="gt_row gt_center">1.47</td>
<td headers="conf.low" class="gt_row gt_center">0.48, 6.41</td>
<td headers="p.value" class="gt_row gt_center">0.5</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    College graduate or above</td>
<td headers="estimate" class="gt_row gt_center">0.84</td>
<td headers="conf.low" class="gt_row gt_center">0.27, 3.67</td>
<td headers="p.value" class="gt_row gt_center">0.8</td></tr>
    <tr><td headers="label" class="gt_row gt_left">RIAGENDR</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Male</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Female</td>
<td headers="estimate" class="gt_row gt_center">0.78</td>
<td headers="conf.low" class="gt_row gt_center">0.61, 0.99</td>
<td headers="p.value" class="gt_row gt_center">0.043</td></tr>
    <tr><td headers="label" class="gt_row gt_left">age_gp2</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    20-39</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    40-59</td>
<td headers="estimate" class="gt_row gt_center">6.28</td>
<td headers="conf.low" class="gt_row gt_center">3.87, 10.9</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    60+</td>
<td headers="estimate" class="gt_row gt_center">11.0</td>
<td headers="conf.low" class="gt_row gt_center">6.72, 19.2</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">RIDRETH3</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Hispanic/Latino</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic White</td>
<td headers="estimate" class="gt_row gt_center">0.68</td>
<td headers="conf.low" class="gt_row gt_center">0.47, 0.99</td>
<td headers="p.value" class="gt_row gt_center">0.038</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic Black</td>
<td headers="estimate" class="gt_row gt_center">1.85</td>
<td headers="conf.low" class="gt_row gt_center">1.18, 2.92</td>
<td headers="p.value" class="gt_row gt_center">0.008</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic Asian</td>
<td headers="estimate" class="gt_row gt_center">0.56</td>
<td headers="conf.low" class="gt_row gt_center">0.19, 1.37</td>
<td headers="p.value" class="gt_row gt_center">0.2</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Other race</td>
<td headers="estimate" class="gt_row gt_center">1.24</td>
<td headers="conf.low" class="gt_row gt_center">0.70, 2.16</td>
<td headers="p.value" class="gt_row gt_center">0.5</td></tr>
    <tr><td headers="label" class="gt_row gt_left">sum_cat</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    150+</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Less than 150</td>
<td headers="estimate" class="gt_row gt_center">1.96</td>
<td headers="conf.low" class="gt_row gt_center">1.14, 3.62</td>
<td headers="p.value" class="gt_row gt_center">0.022</td></tr>
  </tbody>
  <tfoot class="gt_sourcenotes">
    <tr>
      <td class="gt_sourcenote" colspan="4"><span class='gt_from_md'>Abbreviations: CI = Confidence Interval, OR = Odds Ratio</span></td>
    </tr>
  </tfoot>
  &#10;</table>
</div>

``` r
plot_dm <- tidy(backward_adj_dm, conf.int = TRUE, exponentiate = TRUE) %>%
    filter(term != "(Intercept)") %>%  # Optional: remove intercept
    mutate(
        sig = case_when(
            p.value < 0.001 ~ "***",
            p.value < 0.01 ~ "**",
            p.value < 0.05 ~ "*",
            TRUE ~ ""
        ),
        label = paste0(round(estimate, 2), " ", sig),
        color_group = ifelse(estimate > 1, "orangered3", "red4"),
        term = fct_reorder(term, estimate)  # Reorder for better plotting
    )

ggplot(plot_dm, aes(x = estimate, y = term, color = color_group)) +
    geom_point(size = 3) +
    geom_errorbarh(aes(xmin = conf.low, xmax = conf.high), height = 0.2) +
    geom_vline(xintercept = 1, linetype = "dashed", color = "orangered4") +
    geom_text(aes(label = label), hjust = -0.3, size = 3) +
    scale_color_manual(values = c("orangered3", "red4")) +
    labs(
        title = "Adjusted Odds Ratios from Backward Selection Model",
        x = "Odds Ratio",
        y = ""
    ) +
    theme_classic() +
    theme(legend.position = "none")
```

![](Final_DM_by_Education_files/figure-gfm/full%20interation%20term-1.png)<!-- -->

# FINAL MODEL -DM

``` r
#include significant dictors (age, phys activity) + conceptual confounders

final_dm <- glm(told_dm ~ educ_factor + RIAGENDR + age_gp2 + RIDRETH3 + 
                    sum_cat,data = clean_dm, family = binomial)
tbl_regression(final_dm, exponentiate=TRUE)
```

<div id="nfvjkukxrw" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#nfvjkukxrw table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
&#10;#nfvjkukxrw thead, #nfvjkukxrw tbody, #nfvjkukxrw tfoot, #nfvjkukxrw tr, #nfvjkukxrw td, #nfvjkukxrw th {
  border-style: none;
}
&#10;#nfvjkukxrw p {
  margin: 0;
  padding: 0;
}
&#10;#nfvjkukxrw .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}
&#10;#nfvjkukxrw .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}
&#10;#nfvjkukxrw .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}
&#10;#nfvjkukxrw .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}
&#10;#nfvjkukxrw .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#nfvjkukxrw .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#nfvjkukxrw .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#nfvjkukxrw .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}
&#10;#nfvjkukxrw .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}
&#10;#nfvjkukxrw .gt_column_spanner_outer:first-child {
  padding-left: 0;
}
&#10;#nfvjkukxrw .gt_column_spanner_outer:last-child {
  padding-right: 0;
}
&#10;#nfvjkukxrw .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}
&#10;#nfvjkukxrw .gt_spanner_row {
  border-bottom-style: hidden;
}
&#10;#nfvjkukxrw .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}
&#10;#nfvjkukxrw .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}
&#10;#nfvjkukxrw .gt_from_md > :first-child {
  margin-top: 0;
}
&#10;#nfvjkukxrw .gt_from_md > :last-child {
  margin-bottom: 0;
}
&#10;#nfvjkukxrw .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}
&#10;#nfvjkukxrw .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#nfvjkukxrw .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}
&#10;#nfvjkukxrw .gt_row_group_first td {
  border-top-width: 2px;
}
&#10;#nfvjkukxrw .gt_row_group_first th {
  border-top-width: 2px;
}
&#10;#nfvjkukxrw .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#nfvjkukxrw .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}
&#10;#nfvjkukxrw .gt_first_summary_row.thick {
  border-top-width: 2px;
}
&#10;#nfvjkukxrw .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#nfvjkukxrw .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#nfvjkukxrw .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}
&#10;#nfvjkukxrw .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}
&#10;#nfvjkukxrw .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}
&#10;#nfvjkukxrw .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#nfvjkukxrw .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#nfvjkukxrw .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#nfvjkukxrw .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#nfvjkukxrw .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#nfvjkukxrw .gt_left {
  text-align: left;
}
&#10;#nfvjkukxrw .gt_center {
  text-align: center;
}
&#10;#nfvjkukxrw .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}
&#10;#nfvjkukxrw .gt_font_normal {
  font-weight: normal;
}
&#10;#nfvjkukxrw .gt_font_bold {
  font-weight: bold;
}
&#10;#nfvjkukxrw .gt_font_italic {
  font-style: italic;
}
&#10;#nfvjkukxrw .gt_super {
  font-size: 65%;
}
&#10;#nfvjkukxrw .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}
&#10;#nfvjkukxrw .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}
&#10;#nfvjkukxrw .gt_indent_1 {
  text-indent: 5px;
}
&#10;#nfvjkukxrw .gt_indent_2 {
  text-indent: 10px;
}
&#10;#nfvjkukxrw .gt_indent_3 {
  text-indent: 15px;
}
&#10;#nfvjkukxrw .gt_indent_4 {
  text-indent: 20px;
}
&#10;#nfvjkukxrw .gt_indent_5 {
  text-indent: 25px;
}
&#10;#nfvjkukxrw .katex-display {
  display: inline-flex !important;
  margin-bottom: 0.75em !important;
}
&#10;#nfvjkukxrw div.Reactable > div.rt-table > div.rt-thead > div.rt-tr.rt-tr-group-header > div.rt-th-group:after {
  height: 0px !important;
}
</style>
<table class="gt_table" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
  <thead>
    <tr class="gt_col_headings">
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="label"><span class='gt_from_md'><strong>Characteristic</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="estimate"><span class='gt_from_md'><strong>OR</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="conf.low"><span class='gt_from_md'><strong>95% CI</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="p.value"><span class='gt_from_md'><strong>p-value</strong></span></th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="label" class="gt_row gt_left">educ_factor</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Less than 9th grade</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    9-11th grade (incl. 12th, no diploma)</td>
<td headers="estimate" class="gt_row gt_center">2.27</td>
<td headers="conf.low" class="gt_row gt_center">0.69, 10.3</td>
<td headers="p.value" class="gt_row gt_center">0.2</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    High school grad/GED or equivalent</td>
<td headers="estimate" class="gt_row gt_center">1.77</td>
<td headers="conf.low" class="gt_row gt_center">0.57, 7.74</td>
<td headers="p.value" class="gt_row gt_center">0.4</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Some college or AA degree</td>
<td headers="estimate" class="gt_row gt_center">1.47</td>
<td headers="conf.low" class="gt_row gt_center">0.48, 6.41</td>
<td headers="p.value" class="gt_row gt_center">0.5</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    College graduate or above</td>
<td headers="estimate" class="gt_row gt_center">0.84</td>
<td headers="conf.low" class="gt_row gt_center">0.27, 3.67</td>
<td headers="p.value" class="gt_row gt_center">0.8</td></tr>
    <tr><td headers="label" class="gt_row gt_left">RIAGENDR</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Male</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Female</td>
<td headers="estimate" class="gt_row gt_center">0.78</td>
<td headers="conf.low" class="gt_row gt_center">0.61, 0.99</td>
<td headers="p.value" class="gt_row gt_center">0.043</td></tr>
    <tr><td headers="label" class="gt_row gt_left">age_gp2</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    20-39</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    40-59</td>
<td headers="estimate" class="gt_row gt_center">6.28</td>
<td headers="conf.low" class="gt_row gt_center">3.87, 10.9</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    60+</td>
<td headers="estimate" class="gt_row gt_center">11.0</td>
<td headers="conf.low" class="gt_row gt_center">6.72, 19.2</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">RIDRETH3</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Hispanic/Latino</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic White</td>
<td headers="estimate" class="gt_row gt_center">0.68</td>
<td headers="conf.low" class="gt_row gt_center">0.47, 0.99</td>
<td headers="p.value" class="gt_row gt_center">0.038</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic Black</td>
<td headers="estimate" class="gt_row gt_center">1.85</td>
<td headers="conf.low" class="gt_row gt_center">1.18, 2.92</td>
<td headers="p.value" class="gt_row gt_center">0.008</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic Asian</td>
<td headers="estimate" class="gt_row gt_center">0.56</td>
<td headers="conf.low" class="gt_row gt_center">0.19, 1.37</td>
<td headers="p.value" class="gt_row gt_center">0.2</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Other race</td>
<td headers="estimate" class="gt_row gt_center">1.24</td>
<td headers="conf.low" class="gt_row gt_center">0.70, 2.16</td>
<td headers="p.value" class="gt_row gt_center">0.5</td></tr>
    <tr><td headers="label" class="gt_row gt_left">sum_cat</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    150+</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Less than 150</td>
<td headers="estimate" class="gt_row gt_center">1.96</td>
<td headers="conf.low" class="gt_row gt_center">1.14, 3.62</td>
<td headers="p.value" class="gt_row gt_center">0.022</td></tr>
  </tbody>
  <tfoot class="gt_sourcenotes">
    <tr>
      <td class="gt_sourcenote" colspan="4"><span class='gt_from_md'>Abbreviations: CI = Confidence Interval, OR = Odds Ratio</span></td>
    </tr>
  </tfoot>
  &#10;</table>
</div>

``` r
final_dm <- tidy(final_dm, conf.int = TRUE, exponentiate = TRUE) %>%
    filter(term != "(Intercept)") %>%  # Optional: remove intercept
    mutate(
        sig = case_when(
            p.value < 0.001 ~ "***",
            p.value < 0.01 ~ "**",
            p.value < 0.05 ~ "*",
            TRUE ~ ""
        ),
        label = paste0(round(estimate, 2), " ", sig),
        color_group = ifelse(estimate > 1, "orangered3", "red4"),
        term = fct_reorder(term, estimate  # Reorder for better plotting
        ))

ggplot(final_dm, aes(x = estimate, y = term, color = color_group)) +
    geom_point(size = 3) +
    geom_errorbarh(aes(xmin = conf.low, xmax = conf.high), height = 0.2) +
    geom_vline(xintercept = 1, linetype = "dashed", color = "orangered4") +
    geom_text(aes(label = label), hjust = -0.3, size = 3) +
    scale_color_manual(values = c("orangered3", "red4")) +
    labs(
        title = "Adjusted Odds Ratios: Diabetes Final Model",
        x = "Odds Ratio",
        y = ""
    ) +
    theme_classic() +
    theme(legend.position = "none")
```

![](Final_DM_by_Education_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

``` r
#####
```

# Repeat all analytic steps for PREDIABETES

    ## 
    ##    0    1 <NA> 
    ## 2202  382  327

    ## 
    ##    0    1 <NA> 
    ## 2202  382  327

    ## tibble [2,911 × 45] (S3: tbl_df/tbl/data.frame)
    ##  $ SEQN          : num [1:2911] 130379 130380 130386 130389 130392 ...
    ##   ..- attr(*, "label")= chr "Respondent sequence number"
    ##  $ DMDEDUC2      : num [1:2911] 5 3 4 5 5 5 3 4 3 3 ...
    ##   ..- attr(*, "label")= chr "Education level - Adults 20+"
    ##  $ RIDAGEYR      : num [1:2911] 66 44 34 59 74 51 33 56 67 47 ...
    ##   ..- attr(*, "label")= chr "Age in years at screening"
    ##  $ RIAGENDR      : Factor w/ 2 levels "Male","Female": 1 2 1 1 2 1 2 2 2 1 ...
    ##  $ RIDRETH3      : Factor w/ 6 levels "Hispanic/Latino",..: 2 1 1 2 2 2 5 2 2 1 ...
    ##  $ INDFMPIR      : num [1:2911] 5 1.41 1.33 5 3.04 5 1.1 4.82 4.48 1.67 ...
    ##   ..- attr(*, "label")= chr "Ratio of family income to poverty"
    ##  $ ALQ111        : num [1:2911] 1 1 1 1 1 1 1 1 1 1 ...
    ##   ..- attr(*, "label")= chr "Ever had a drink of any kind of alcohol"
    ##  $ ALQ121        : num [1:2911] 2 10 4 2 8 6 10 3 8 3 ...
    ##   ..- attr(*, "label")= chr "Past 12 mos how often drink alc bev"
    ##  $ ALQ130        : num [1:2911] 3 1 2 2 1 1 1 1 2 1 ...
    ##   ..- attr(*, "label")= chr "Avg # alcoholic drinks/day/past 12 mos"
    ##  $ ALQ142        : num [1:2911] 0 0 10 10 10 0 0 0 0 0 ...
    ##   ..- attr(*, "label")= chr "# days have 4/5 drinks/past 12 mos"
    ##  $ ALQ270        : num [1:2911] NA NA 0 0 0 NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "# times 4/5 drinks in 2hrs/past 12 mos"
    ##  $ ALQ280        : num [1:2911] NA NA 10 0 0 NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "# times 8+ drinks in 1 day/past 12 mos"
    ##  $ ALQ151        : num [1:2911] 2 2 2 2 2 2 2 2 2 2 ...
    ##   ..- attr(*, "label")= chr "Ever have 4/5 or more drinks every day"
    ##  $ ALQ170        : num [1:2911] NA NA 0 0 0 NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "# times 4/5 drinks on occasion/past mo"
    ##  $ DIQ010        : num [1:2911] 2 1 2 2 2 2 2 2 2 2 ...
    ##   ..- attr(*, "label")= chr "Doctor told you have diabetes"
    ##  $ DID040        : num [1:2911] NA 35 NA NA NA NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "Age when first told you had diabetes"
    ##  $ DIQ160        : num [1:2911] 2 NA 2 1 2 2 2 2 1 2 ...
    ##   ..- attr(*, "label")= chr "Ever told you have prediabetes"
    ##  $ DIQ180        : num [1:2911] 1 NA 2 1 1 1 2 1 1 2 ...
    ##   ..- attr(*, "label")= chr "Had blood tested past three years"
    ##  $ DIQ050        : num [1:2911] NA 2 NA NA NA NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "Taking insulin now"
    ##  $ DID060        : num [1:2911] NA NA NA NA NA NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "How long taking insulin"
    ##  $ DIQ060U       : num [1:2911] NA NA NA NA NA NA NA NA NA NA ...
    ##   ..- attr(*, "label")= chr "Unit of measure (month/year)"
    ##  $ DIQ070        : num [1:2911] NA 1 NA 2 NA NA NA NA 2 NA ...
    ##   ..- attr(*, "label")= chr "Take diabetic pills to lower blood sugar"
    ##  $ PAD790Q       : num [1:2911] 4 1 1 3 0 7 3 3 0 7 ...
    ##   ..- attr(*, "label")= chr "Frequency of moderate LTPA"
    ##  $ PAD790U       : chr [1:2911] "W" "W" "W" "W" ...
    ##   ..- attr(*, "label")= chr "Moderate LTPA unit (day/week/month/year)"
    ##  $ PAD800        : num [1:2911] 45 20 30 45 NA 45 15 20 NA 120 ...
    ##   ..- attr(*, "label")= chr "Minutes moderate LTPA"
    ##  $ PAD810Q       : num [1:2911] 3 0 1 2 0 4 0 0 0 2 ...
    ##   ..- attr(*, "label")= chr "Frequency of vigorous LTPA"
    ##  $ PAD810U       : chr [1:2911] "W" "" "M" "M" ...
    ##   ..- attr(*, "label")= chr "Vigorous LTPA unit (day/week/month/year)"
    ##  $ PAD820        : num [1:2911] 45 NA 30 30 NA 30 NA NA NA 60 ...
    ##   ..- attr(*, "label")= chr "Minutes vigorous LTPA"
    ##  $ PAD680        : num [1:2911] 480 240 180 720 300 420 360 240 480 60 ...
    ##   ..- attr(*, "label")= chr "Minutes sedentary activity"
    ##  $ told_pre_dm   : num [1:2911] 0 NA 0 1 0 0 0 0 1 0 ...
    ##  $ told_dm       : num [1:2911] 0 1 0 0 0 0 0 0 0 0 ...
    ##  $ freq_moderate : num [1:2911] 4 1 1 3 0 7 3 3 0 7 ...
    ##  $ min_moderate  : num [1:2911] 45 20 30 45 NA 45 15 20 NA 120 ...
    ##  $ freq_vigorous : num [1:2911] 3 0 1 2 0 4 0 0 0 2 ...
    ##  $ min_vigorous  : num [1:2911] 45 NA 30 30 NA 30 NA NA NA 60 ...
    ##  $ total_mod     : num [1:2911] 25.71 2.86 4.29 19.29 NA ...
    ##  $ total_vig     : num [1:2911] 19.3 NA 1 2 NA ...
    ##  $ adj_vig       : num [1:2911] 38.6 NA 2 4 NA ...
    ##  $ sum_mod_vig   : num [1:2911] 64.29 2.86 6.29 23.29 0 ...
    ##  $ sum_cat       : chr [1:2911] "Less than 150" "Less than 150" "Less than 150" "Less than 150" ...
    ##  $ INDFMPIR_group: Factor w/ 3 levels "Low-income","Middle-income",..: 3 2 2 3 2 3 2 3 3 2 ...
    ##  $ age_gp2       : chr [1:2911] "60+" "40-59" "20-39" "40-59" ...
    ##  $ educ_num      : chr [1:2911] "5" "3" "4" "5" ...
    ##  $ educ_factor   : Factor w/ 5 levels "Less than 9th grade",..: 5 3 4 5 5 5 3 4 3 3 ...
    ##  $ factor_dm     : Factor w/ 2 levels "No","Yes": 1 2 1 1 1 1 1 1 1 1 ...
    ##  - attr(*, "label")= chr "Demographic Variables and Sample Weights"

    ##  [1] "SEQN"           "DMDEDUC2"       "RIDAGEYR"       "RIAGENDR"      
    ##  [5] "RIDRETH3"       "INDFMPIR"       "ALQ111"         "ALQ121"        
    ##  [9] "ALQ130"         "ALQ142"         "ALQ270"         "ALQ280"        
    ## [13] "ALQ151"         "ALQ170"         "DIQ010"         "DID040"        
    ## [17] "DIQ160"         "DIQ180"         "DIQ050"         "DID060"        
    ## [21] "DIQ060U"        "DIQ070"         "PAD790Q"        "PAD790U"       
    ## [25] "PAD800"         "PAD810Q"        "PAD810U"        "PAD820"        
    ## [29] "PAD680"         "told_pre_dm"    "told_dm"        "freq_moderate" 
    ## [33] "min_moderate"   "freq_vigorous"  "min_vigorous"   "total_mod"     
    ## [37] "total_vig"      "adj_vig"        "sum_mod_vig"    "sum_cat"       
    ## [41] "INDFMPIR_group" "age_gp2"        "educ_num"       "educ_factor"   
    ## [45] "factor_dm"

    ## Warning: Returning more (or less) than 1 row per `summarise()` group was deprecated in
    ## dplyr 1.1.0.
    ## ℹ Please use `reframe()` instead.
    ## ℹ When switching from `summarise()` to `reframe()`, remember that `reframe()`
    ##   always returns an ungrouped data frame and adjust accordingly.
    ## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was
    ## generated.

    ## 
    ##    0    1 
    ## 2202  382

    ##                                 educ_factor    told_pre_dm    
    ##  Less than 9th grade                  :  23   Min.   :0.0000  
    ##  9-11th grade (incl. 12th, no diploma):  97   1st Qu.:0.0000  
    ##  High school grad/GED or equivalent   : 416   Median :0.0000  
    ##  Some college or AA degree            : 788   Mean   :0.1478  
    ##  College graduate or above            :1260   3rd Qu.:0.0000  
    ##                                               Max.   :1.0000  
    ##    educ_num              SEQN           RIDAGEYR     sum_mod_vig      
    ##  Length:2584        Min.   :130379   Min.   :20.0   Min.   :   0.000  
    ##  Class :character   1st Qu.:133320   1st Qu.:36.0   1st Qu.:   8.571  
    ##  Mode  :character   Median :136458   Median :53.0   Median :  30.000  
    ##                     Mean   :136364   Mean   :51.5   Mean   :  54.007  
    ##                     3rd Qu.:139351   3rd Qu.:66.0   3rd Qu.:  64.286  
    ##                     Max.   :142310   Max.   :80.0   Max.   :1234.286  
    ##        n              totalp         prop_pre_dm              SE           
    ##  Min.   :   2.0   Min.   :    445   Min.   :0.0001376   Min.   :1.062e-05  
    ##  1st Qu.: 349.0   1st Qu.: 449864   1st Qu.:0.0008946   1st Qu.:2.706e-05  
    ##  Median : 658.0   Median : 449864   Median :0.0008946   Median :2.706e-05  
    ##  Mean   : 698.2   Mean   : 753011   Mean   :0.0019350   Mean   :1.780e-04  
    ##  3rd Qu.:1092.0   3rd Qu.:1220688   3rd Qu.:0.0014627   3rd Qu.:5.698e-05  
    ##  Max.   :1092.0   Max.   :1220688   Max.   :0.0471910   Max.   :1.005e-02

![](Final_DM_by_Education_files/figure-gfm/pre-1.png)<!-- -->

# stratify by gender

``` r
final_gender <- Finalnhanes %>%
    group_by(educ_factor, RIAGENDR, told_pre_dm) %>%
    summarise(
        SEQN=SEQN,
        educ_factor=educ_factor,
        RIAGENDR = RIAGENDR,
        told_pre_dm=told_pre_dm,
        n = n(), .groups = "drop") %>%
    group_by(educ_factor) %>%
    mutate(
        totalp = sum(n, na.rm=FALSE),
        prop_pre_dm = n/totalp,
        SE = sqrt((prop_pre_dm * (1-prop_pre_dm))/totalp))
```

    ## Warning: Returning more (or less) than 1 row per `summarise()` group was deprecated in
    ## dplyr 1.1.0.
    ## ℹ Please use `reframe()` instead.
    ## ℹ When switching from `summarise()` to `reframe()`, remember that `reframe()`
    ##   always returns an ungrouped data frame and adjust accordingly.
    ## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was
    ## generated.

``` r
table(final_gender$told_pre_dm, useNA="ifany")    
```

    ## 
    ##    0    1 <NA> 
    ## 2202  382  327

``` r
summary(final_gender)
```

    ##                                 educ_factor     RIAGENDR     told_pre_dm    
    ##  Less than 9th grade                  :  26   Male  :1351   Min.   :0.0000  
    ##  9-11th grade (incl. 12th, no diploma): 124   Female:1560   1st Qu.:0.0000  
    ##  High school grad/GED or equivalent   : 497                 Median :0.0000  
    ##  Some college or AA degree            : 903                 Mean   :0.1478  
    ##  College graduate or above            :1361                 3rd Qu.:0.0000  
    ##                                                             Max.   :1.0000  
    ##                                                             NA's   :327     
    ##       SEQN              n           totalp        prop_pre_dm       
    ##  Min.   :130379   Min.   :  1   Min.   :   242   Min.   :6.744e-05  
    ##  1st Qu.:133317   1st Qu.: 94   1st Qu.:234945   1st Qu.:7.820e-04  
    ##  Median :136461   Median :366   Median :234945   Median :9.715e-04  
    ##  Mean   :136366   Mean   :319   Mean   :375593   Mean   :1.718e-03  
    ##  3rd Qu.:139345   3rd Qu.:487   3rd Qu.:622751   3rd Qu.:1.558e-03  
    ##  Max.   :142310   Max.   :605   Max.   :622751   Max.   :5.372e-02  
    ##                                                                     
    ##        SE           
    ##  Min.   :1.041e-05  
    ##  1st Qu.:3.542e-05  
    ##  Median :3.948e-05  
    ##  Mean   :2.279e-04  
    ##  3rd Qu.:8.137e-05  
    ##  Max.   :1.449e-02  
    ## 

# Drop NA Values

    ##                                 educ_factor    told_pre_dm    
    ##  Less than 9th grade                  :  23   Min.   :0.0000  
    ##  9-11th grade (incl. 12th, no diploma):  97   1st Qu.:0.0000  
    ##  High school grad/GED or equivalent   : 416   Median :0.0000  
    ##  Some college or AA degree            : 788   Mean   :0.1478  
    ##  College graduate or above            :1260   3rd Qu.:0.0000  
    ##                                               Max.   :1.0000  
    ##    educ_num              SEQN           RIDAGEYR     sum_mod_vig      
    ##  Length:2584        Min.   :130379   Min.   :20.0   Min.   :   0.000  
    ##  Class :character   1st Qu.:133320   1st Qu.:36.0   1st Qu.:   8.571  
    ##  Mode  :character   Median :136458   Median :53.0   Median :  30.000  
    ##                     Mean   :136364   Mean   :51.5   Mean   :  54.007  
    ##                     3rd Qu.:139351   3rd Qu.:66.0   3rd Qu.:  64.286  
    ##                     Max.   :142310   Max.   :80.0   Max.   :1234.286  
    ##        n              totalp         prop_pre_dm              SE           
    ##  Min.   :   2.0   Min.   :    445   Min.   :0.0001376   Min.   :1.062e-05  
    ##  1st Qu.: 349.0   1st Qu.: 449864   1st Qu.:0.0008946   1st Qu.:2.706e-05  
    ##  Median : 658.0   Median : 449864   Median :0.0008946   Median :2.706e-05  
    ##  Mean   : 698.2   Mean   : 753011   Mean   :0.0019350   Mean   :1.780e-04  
    ##  3rd Qu.:1092.0   3rd Qu.:1220688   3rd Qu.:0.0014627   3rd Qu.:5.698e-05  
    ##  Max.   :1092.0   Max.   :1220688   Max.   :0.0471910   Max.   :1.005e-02

    ## 
    ## FALSE 
    ##  2584

    ## 
    ## FALSE 
    ##  2584

    ##                   Less than 9th grade 9-11th grade (incl. 12th, no diploma) 
    ##                                    23                                    97 
    ##    High school grad/GED or equivalent             Some college or AA degree 
    ##                                   416                                   788 
    ##             College graduate or above 
    ##                                  1260

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##  0.0000  0.0000  0.0000  0.1478  0.0000  1.0000

    ## 
    ##                   Less than 9th grade 9-11th grade (incl. 12th, no diploma) 
    ##                                    23                                    97 
    ##    High school grad/GED or equivalent             Some college or AA degree 
    ##                                   416                                   788 
    ##             College graduate or above 
    ##                                  1260

# Full model with interaction term-predm

``` r
# Step 2: Fit the full model
adj_predm_model_clean <- glm(told_pre_dm ~ educ_factor+RIAGENDR+age_gp2+RIDRETH3+sum_cat+
                                 INDFMPIR_group+ALQ130,data = clean_predm, family = binomial)

backward_adj_pre <- step(adj_predm_model_clean, direction = "backward")
```

    ## Start:  AIC=2070.43
    ## told_pre_dm ~ educ_factor + RIAGENDR + age_gp2 + RIDRETH3 + sum_cat + 
    ##     INDFMPIR_group + ALQ130

    ## Warning: glm.fit: fitted probabilities numerically 0 or 1 occurred

    ##                  Df Deviance    AIC
    ## - INDFMPIR_group  1   2040.4 2068.4
    ## - RIAGENDR        1   2041.5 2069.4
    ## - educ_factor     4   2047.5 2069.5
    ## - ALQ130          1   2042.1 2070.1
    ## <none>                2040.4 2070.4
    ## - sum_cat         1   2043.1 2071.1
    ## - RIDRETH3        4   2050.8 2072.8
    ## - age_gp2         2   2148.8 2174.8
    ## 
    ## Step:  AIC=2068.44
    ## told_pre_dm ~ educ_factor + RIAGENDR + age_gp2 + RIDRETH3 + sum_cat + 
    ##     ALQ130

    ## Warning: glm.fit: fitted probabilities numerically 0 or 1 occurred

    ##               Df Deviance    AIC
    ## - RIAGENDR     1   2041.5 2067.4
    ## - educ_factor  4   2047.8 2067.8
    ## - ALQ130       1   2042.2 2068.2
    ## <none>             2040.4 2068.4
    ## - sum_cat      1   2043.1 2069.1
    ## - RIDRETH3     4   2050.8 2070.8
    ## - age_gp2      2   2149.1 2173.1
    ## 
    ## Step:  AIC=2067.45
    ## told_pre_dm ~ educ_factor + age_gp2 + RIDRETH3 + sum_cat + ALQ130

    ## Warning: glm.fit: fitted probabilities numerically 0 or 1 occurred

    ##               Df Deviance    AIC
    ## - educ_factor  4   2048.9 2066.9
    ## - ALQ130       1   2043.3 2067.3
    ## <none>             2041.5 2067.4
    ## - sum_cat      1   2044.4 2068.4
    ## - RIDRETH3     4   2051.7 2069.7
    ## - age_gp2      2   2150.3 2172.3
    ## 
    ## Step:  AIC=2066.86
    ## told_pre_dm ~ age_gp2 + RIDRETH3 + sum_cat + ALQ130
    ## 
    ##            Df Deviance    AIC
    ## <none>          2048.9 2066.9
    ## - ALQ130    1   2050.9 2066.9
    ## - sum_cat   1   2051.4 2067.4
    ## - RIDRETH3  4   2058.0 2068.0
    ## - age_gp2   2   2157.6 2171.6

``` r
tbl_regression(backward_adj_pre, exponentiate=TRUE)
```

    ## Warning: glm.fit: fitted probabilities numerically 0 or 1 occurred

<div id="dxnctrsyao" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#dxnctrsyao table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
&#10;#dxnctrsyao thead, #dxnctrsyao tbody, #dxnctrsyao tfoot, #dxnctrsyao tr, #dxnctrsyao td, #dxnctrsyao th {
  border-style: none;
}
&#10;#dxnctrsyao p {
  margin: 0;
  padding: 0;
}
&#10;#dxnctrsyao .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}
&#10;#dxnctrsyao .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}
&#10;#dxnctrsyao .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}
&#10;#dxnctrsyao .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}
&#10;#dxnctrsyao .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#dxnctrsyao .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#dxnctrsyao .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#dxnctrsyao .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}
&#10;#dxnctrsyao .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}
&#10;#dxnctrsyao .gt_column_spanner_outer:first-child {
  padding-left: 0;
}
&#10;#dxnctrsyao .gt_column_spanner_outer:last-child {
  padding-right: 0;
}
&#10;#dxnctrsyao .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}
&#10;#dxnctrsyao .gt_spanner_row {
  border-bottom-style: hidden;
}
&#10;#dxnctrsyao .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}
&#10;#dxnctrsyao .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}
&#10;#dxnctrsyao .gt_from_md > :first-child {
  margin-top: 0;
}
&#10;#dxnctrsyao .gt_from_md > :last-child {
  margin-bottom: 0;
}
&#10;#dxnctrsyao .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}
&#10;#dxnctrsyao .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#dxnctrsyao .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}
&#10;#dxnctrsyao .gt_row_group_first td {
  border-top-width: 2px;
}
&#10;#dxnctrsyao .gt_row_group_first th {
  border-top-width: 2px;
}
&#10;#dxnctrsyao .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#dxnctrsyao .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}
&#10;#dxnctrsyao .gt_first_summary_row.thick {
  border-top-width: 2px;
}
&#10;#dxnctrsyao .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#dxnctrsyao .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#dxnctrsyao .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}
&#10;#dxnctrsyao .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}
&#10;#dxnctrsyao .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}
&#10;#dxnctrsyao .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#dxnctrsyao .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#dxnctrsyao .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#dxnctrsyao .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#dxnctrsyao .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#dxnctrsyao .gt_left {
  text-align: left;
}
&#10;#dxnctrsyao .gt_center {
  text-align: center;
}
&#10;#dxnctrsyao .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}
&#10;#dxnctrsyao .gt_font_normal {
  font-weight: normal;
}
&#10;#dxnctrsyao .gt_font_bold {
  font-weight: bold;
}
&#10;#dxnctrsyao .gt_font_italic {
  font-style: italic;
}
&#10;#dxnctrsyao .gt_super {
  font-size: 65%;
}
&#10;#dxnctrsyao .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}
&#10;#dxnctrsyao .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}
&#10;#dxnctrsyao .gt_indent_1 {
  text-indent: 5px;
}
&#10;#dxnctrsyao .gt_indent_2 {
  text-indent: 10px;
}
&#10;#dxnctrsyao .gt_indent_3 {
  text-indent: 15px;
}
&#10;#dxnctrsyao .gt_indent_4 {
  text-indent: 20px;
}
&#10;#dxnctrsyao .gt_indent_5 {
  text-indent: 25px;
}
&#10;#dxnctrsyao .katex-display {
  display: inline-flex !important;
  margin-bottom: 0.75em !important;
}
&#10;#dxnctrsyao div.Reactable > div.rt-table > div.rt-thead > div.rt-tr.rt-tr-group-header > div.rt-th-group:after {
  height: 0px !important;
}
</style>
<table class="gt_table" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
  <thead>
    <tr class="gt_col_headings">
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="label"><span class='gt_from_md'><strong>Characteristic</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="estimate"><span class='gt_from_md'><strong>OR</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="conf.low"><span class='gt_from_md'><strong>95% CI</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="p.value"><span class='gt_from_md'><strong>p-value</strong></span></th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="label" class="gt_row gt_left">age_gp2</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    20-39</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    40-59</td>
<td headers="estimate" class="gt_row gt_center">4.27</td>
<td headers="conf.low" class="gt_row gt_center">2.99, 6.26</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    60+</td>
<td headers="estimate" class="gt_row gt_center">5.75</td>
<td headers="conf.low" class="gt_row gt_center">3.96, 8.55</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">RIDRETH3</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Hispanic/Latino</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic White</td>
<td headers="estimate" class="gt_row gt_center">0.65</td>
<td headers="conf.low" class="gt_row gt_center">0.47, 0.91</td>
<td headers="p.value" class="gt_row gt_center">0.011</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic Black</td>
<td headers="estimate" class="gt_row gt_center">0.75</td>
<td headers="conf.low" class="gt_row gt_center">0.45, 1.22</td>
<td headers="p.value" class="gt_row gt_center">0.3</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic Asian</td>
<td headers="estimate" class="gt_row gt_center">1.12</td>
<td headers="conf.low" class="gt_row gt_center">0.59, 2.05</td>
<td headers="p.value" class="gt_row gt_center">0.7</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Other race</td>
<td headers="estimate" class="gt_row gt_center">0.60</td>
<td headers="conf.low" class="gt_row gt_center">0.32, 1.08</td>
<td headers="p.value" class="gt_row gt_center">0.10</td></tr>
    <tr><td headers="label" class="gt_row gt_left">sum_cat</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    150+</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Less than 150</td>
<td headers="estimate" class="gt_row gt_center">1.47</td>
<td headers="conf.low" class="gt_row gt_center">0.92, 2.50</td>
<td headers="p.value" class="gt_row gt_center">0.13</td></tr>
    <tr><td headers="label" class="gt_row gt_left">Avg # alcoholic drinks/day/past 12 mos</td>
<td headers="estimate" class="gt_row gt_center">1.00</td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center">0.5</td></tr>
  </tbody>
  <tfoot class="gt_sourcenotes">
    <tr>
      <td class="gt_sourcenote" colspan="4"><span class='gt_from_md'>Abbreviations: CI = Confidence Interval, OR = Odds Ratio</span></td>
    </tr>
  </tfoot>
  &#10;</table>
</div>

``` r
plot_predm <- tidy(backward_adj_pre, conf.int = TRUE, exponentiate = TRUE) %>%
    filter(term != "(Intercept)") %>%  # Optional: remove intercept
    mutate(
        sig = case_when(
            p.value < 0.001 ~ "***",
            p.value < 0.01 ~ "**",
            p.value < 0.05 ~ "*",
            TRUE ~ ""
        ),
        label = paste0(round(estimate, 2), " ", sig),
        color_group = ifelse(estimate > 1, "cornflowerblue", "darkblue"),
        term = fct_reorder(term, estimate)  # Reorder for better plotting
    )
```

    ## Warning: glm.fit: fitted probabilities numerically 0 or 1 occurred

``` r
ggplot(plot_predm, aes(x = estimate, y = term, color = color_group)) +
    geom_point(size = 3) +
    geom_errorbarh(aes(xmin = conf.low, xmax = conf.high), height = 0.2) +
    geom_vline(xintercept = 1, linetype = "dashed", color = "purple") +
    geom_text(aes(label = label), hjust = -0.3, size = 3) +
    scale_color_manual(values = c("cornflowerblue", "darkblue")) +
    labs(
        title = "Adjusted Odds Ratios from Backward Selection Model",
        x = "Odds Ratio",
        y = ""
    ) +
    theme_classic() +
    theme(legend.position = "none")
```

    ## Warning: Removed 1 row containing missing values or values outside the scale range
    ## (`geom_errorbarh()`).

![](Final_DM_by_Education_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

``` r
### FINAL MODEL with INTERACTION TERM PRE-DM
# inlcude significant predictors (age, phys activity) + conceptual confounders

final_predm <- glm(told_pre_dm ~ educ_factor + RIAGENDR + age_gp2 + RIDRETH3 + 
                       sum_cat,data = clean_predm, family = binomial)
tbl_regression(final_predm, exponentiate=TRUE)
```

<div id="kjbgxfdvhi" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#kjbgxfdvhi table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
&#10;#kjbgxfdvhi thead, #kjbgxfdvhi tbody, #kjbgxfdvhi tfoot, #kjbgxfdvhi tr, #kjbgxfdvhi td, #kjbgxfdvhi th {
  border-style: none;
}
&#10;#kjbgxfdvhi p {
  margin: 0;
  padding: 0;
}
&#10;#kjbgxfdvhi .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}
&#10;#kjbgxfdvhi .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}
&#10;#kjbgxfdvhi .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}
&#10;#kjbgxfdvhi .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}
&#10;#kjbgxfdvhi .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#kjbgxfdvhi .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#kjbgxfdvhi .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#kjbgxfdvhi .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}
&#10;#kjbgxfdvhi .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}
&#10;#kjbgxfdvhi .gt_column_spanner_outer:first-child {
  padding-left: 0;
}
&#10;#kjbgxfdvhi .gt_column_spanner_outer:last-child {
  padding-right: 0;
}
&#10;#kjbgxfdvhi .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}
&#10;#kjbgxfdvhi .gt_spanner_row {
  border-bottom-style: hidden;
}
&#10;#kjbgxfdvhi .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}
&#10;#kjbgxfdvhi .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}
&#10;#kjbgxfdvhi .gt_from_md > :first-child {
  margin-top: 0;
}
&#10;#kjbgxfdvhi .gt_from_md > :last-child {
  margin-bottom: 0;
}
&#10;#kjbgxfdvhi .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}
&#10;#kjbgxfdvhi .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#kjbgxfdvhi .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}
&#10;#kjbgxfdvhi .gt_row_group_first td {
  border-top-width: 2px;
}
&#10;#kjbgxfdvhi .gt_row_group_first th {
  border-top-width: 2px;
}
&#10;#kjbgxfdvhi .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#kjbgxfdvhi .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}
&#10;#kjbgxfdvhi .gt_first_summary_row.thick {
  border-top-width: 2px;
}
&#10;#kjbgxfdvhi .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#kjbgxfdvhi .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#kjbgxfdvhi .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}
&#10;#kjbgxfdvhi .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}
&#10;#kjbgxfdvhi .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}
&#10;#kjbgxfdvhi .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#kjbgxfdvhi .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#kjbgxfdvhi .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#kjbgxfdvhi .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#kjbgxfdvhi .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#kjbgxfdvhi .gt_left {
  text-align: left;
}
&#10;#kjbgxfdvhi .gt_center {
  text-align: center;
}
&#10;#kjbgxfdvhi .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}
&#10;#kjbgxfdvhi .gt_font_normal {
  font-weight: normal;
}
&#10;#kjbgxfdvhi .gt_font_bold {
  font-weight: bold;
}
&#10;#kjbgxfdvhi .gt_font_italic {
  font-style: italic;
}
&#10;#kjbgxfdvhi .gt_super {
  font-size: 65%;
}
&#10;#kjbgxfdvhi .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}
&#10;#kjbgxfdvhi .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}
&#10;#kjbgxfdvhi .gt_indent_1 {
  text-indent: 5px;
}
&#10;#kjbgxfdvhi .gt_indent_2 {
  text-indent: 10px;
}
&#10;#kjbgxfdvhi .gt_indent_3 {
  text-indent: 15px;
}
&#10;#kjbgxfdvhi .gt_indent_4 {
  text-indent: 20px;
}
&#10;#kjbgxfdvhi .gt_indent_5 {
  text-indent: 25px;
}
&#10;#kjbgxfdvhi .katex-display {
  display: inline-flex !important;
  margin-bottom: 0.75em !important;
}
&#10;#kjbgxfdvhi div.Reactable > div.rt-table > div.rt-thead > div.rt-tr.rt-tr-group-header > div.rt-th-group:after {
  height: 0px !important;
}
</style>
<table class="gt_table" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
  <thead>
    <tr class="gt_col_headings">
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="label"><span class='gt_from_md'><strong>Characteristic</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="estimate"><span class='gt_from_md'><strong>OR</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="conf.low"><span class='gt_from_md'><strong>95% CI</strong></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="p.value"><span class='gt_from_md'><strong>p-value</strong></span></th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="label" class="gt_row gt_left">educ_factor</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Less than 9th grade</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    9-11th grade (incl. 12th, no diploma)</td>
<td headers="estimate" class="gt_row gt_center">2.62</td>
<td headers="conf.low" class="gt_row gt_center">0.65, 17.7</td>
<td headers="p.value" class="gt_row gt_center">0.2</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    High school grad/GED or equivalent</td>
<td headers="estimate" class="gt_row gt_center">3.01</td>
<td headers="conf.low" class="gt_row gt_center">0.83, 19.3</td>
<td headers="p.value" class="gt_row gt_center">0.15</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Some college or AA degree</td>
<td headers="estimate" class="gt_row gt_center">3.30</td>
<td headers="conf.low" class="gt_row gt_center">0.92, 21.1</td>
<td headers="p.value" class="gt_row gt_center">0.12</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    College graduate or above</td>
<td headers="estimate" class="gt_row gt_center">2.47</td>
<td headers="conf.low" class="gt_row gt_center">0.69, 15.8</td>
<td headers="p.value" class="gt_row gt_center">0.2</td></tr>
    <tr><td headers="label" class="gt_row gt_left">RIAGENDR</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Male</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Female</td>
<td headers="estimate" class="gt_row gt_center">1.13</td>
<td headers="conf.low" class="gt_row gt_center">0.90, 1.42</td>
<td headers="p.value" class="gt_row gt_center">0.3</td></tr>
    <tr><td headers="label" class="gt_row gt_left">age_gp2</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    20-39</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    40-59</td>
<td headers="estimate" class="gt_row gt_center">4.29</td>
<td headers="conf.low" class="gt_row gt_center">3.00, 6.29</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    60+</td>
<td headers="estimate" class="gt_row gt_center">5.83</td>
<td headers="conf.low" class="gt_row gt_center">4.01, 8.68</td>
<td headers="p.value" class="gt_row gt_center"><0.001</td></tr>
    <tr><td headers="label" class="gt_row gt_left">RIDRETH3</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Hispanic/Latino</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic White</td>
<td headers="estimate" class="gt_row gt_center">0.64</td>
<td headers="conf.low" class="gt_row gt_center">0.46, 0.90</td>
<td headers="p.value" class="gt_row gt_center">0.009</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic Black</td>
<td headers="estimate" class="gt_row gt_center">0.70</td>
<td headers="conf.low" class="gt_row gt_center">0.42, 1.15</td>
<td headers="p.value" class="gt_row gt_center">0.2</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non-Hispanic Asian</td>
<td headers="estimate" class="gt_row gt_center">1.19</td>
<td headers="conf.low" class="gt_row gt_center">0.62, 2.19</td>
<td headers="p.value" class="gt_row gt_center">0.6</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Other race</td>
<td headers="estimate" class="gt_row gt_center">0.57</td>
<td headers="conf.low" class="gt_row gt_center">0.30, 1.04</td>
<td headers="p.value" class="gt_row gt_center">0.076</td></tr>
    <tr><td headers="label" class="gt_row gt_left">sum_cat</td>
<td headers="estimate" class="gt_row gt_center"><br /></td>
<td headers="conf.low" class="gt_row gt_center"><br /></td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    150+</td>
<td headers="estimate" class="gt_row gt_center">—</td>
<td headers="conf.low" class="gt_row gt_center">—</td>
<td headers="p.value" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Less than 150</td>
<td headers="estimate" class="gt_row gt_center">1.50</td>
<td headers="conf.low" class="gt_row gt_center">0.93, 2.54</td>
<td headers="p.value" class="gt_row gt_center">0.11</td></tr>
  </tbody>
  <tfoot class="gt_sourcenotes">
    <tr>
      <td class="gt_sourcenote" colspan="4"><span class='gt_from_md'>Abbreviations: CI = Confidence Interval, OR = Odds Ratio</span></td>
    </tr>
  </tfoot>
  &#10;</table>
</div>

``` r
final_predm <- tidy(final_predm, conf.int = TRUE, exponentiate = TRUE) %>%
    filter(term != "(Intercept)") %>%  # Optional: remove intercept
    mutate(
        sig = case_when(
            p.value < 0.001 ~ "***",
            p.value < 0.01 ~ "**",
            p.value < 0.05 ~ "*",
            TRUE ~ ""
        ),
        label = paste0(round(estimate, 2), " ", sig),
        color_group = ifelse(estimate > 1, "cornflowerblue", "darkblue"),
        term = fct_reorder(term, estimate)  # Reorder for better plotting
    )


ggplot(final_predm, aes(x = estimate, y = term, color = color_group)) +
    geom_point(size = 3) +
    geom_errorbarh(aes(xmin = conf.low, xmax = conf.high), height = 0.2) +
    geom_vline(xintercept = 1, linetype = "dashed", color = "navyblue") +
    geom_text(aes(label = label), hjust = -0.3, size = 3) +
    scale_color_manual(values = c("cornflowerblue", "darkblue")) +
    labs(
        title = "Adjusted Odds Ratios: Prediabetes Final Model",
        x = "Odds Ratio",
        y = ""
    ) +
    theme_classic() +
    theme(legend.position = "none")
```

![](Final_DM_by_Education_files/figure-gfm/unnamed-chunk-8-1.png)<!-- -->
