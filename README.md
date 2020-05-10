BIGDAWG Relative Risk (BDRR)
================

## version 1.0.1.9000

BDRR includes one function, *relRisk()*, which calculates relative risk
and associated measures for BIGDAWG-formatted case-control genotype
datasets (shown below), using the fmsb::riskratio function.

``` r
BIGDAWG::HLA_data[1:4,]
```

    ##   SampleID Disease           A           A        DRB1        DRB1        DQB1
    ## 1  SCo0001       0 01:01:01:01 01:01:01:01    01:01:01    01:01:01 05:03:01:01
    ## 2  SCo0002       0 03:01:01:01       68:06    08:01:03 15:01:01:01    03:02:12
    ## 3  SCo0003       0       26:08       32:02 07:01:01:01 15:01:01:01    03:02:01
    ## 4  SCo0004       0 01:01:01:01    32:01:01    01:01:01    11:04:01 05:03:01:01
    ##          DQB1  DRB3        DRB3     DRB4  DRB4  DRB5     DRB5
    ## 1 05:03:01:01 00:00       00:00    00:00 00:00 00:00    00:00
    ## 2 03:01:01:01 00:00       00:00    00:00 00:00 00:00 01:01:01
    ## 3 03:01:01:01 00:00       00:00 01:03:03 00:00 00:00 01:01:01
    ## 4    02:01:01 00:00 02:01:01:01    00:00 00:00 00:00    00:00

Details about the
[BIGDAWG](https://cran.r-project.org/package=BIGDAWG)-format can be
found in the [BIGDAWG
Vignette](https://cran.r-project.org/web/packages/BIGDAWG/vignettes/BIGDAWG.html).
BDRR accepts both BIGDAWG-formatted data frames and tab-delimited text
files as input.

The *riskRatio() function* returns an R list object that contains an
`$alleles` and a `$genotypes` list of analytic result data frames for
each locus. Data in these data frames are organized in `Locus`,
`Variant`, `Cases`, `Controls`, `RelativeRisk`, `CI.low`, `CI.high`,
`p.value`, and `Significant` columns, as shown below.

``` r
library(BDRR)
exampleRR <- relRisk(BIGDAWG::HLA_data[,1:4])
exampleRR$alleles[[1]][1:5,]    
```

    ##   Locus     Variant Cases Controls      RelativeRisk            CI.low
    ## 1     A 01:01:01:01   176      166  1.03432941327678 0.928482721560761
    ## 2     A 02:01:01:01    52       58 0.945940890385335 0.774586359500803
    ## 3     A    02:05:01   105      142 0.843683161448755 0.727283103794645
    ## 4     A 03:01:01:01   150      145  1.02052995941752 0.908069882145854
    ## 5     A    03:01:03   137      108  1.12949687674962  1.00601549637306
    ##             CI.high            p.value Significant
    ## 1  1.15224258925478  0.545807942758558            
    ## 2  1.15520258926283  0.576318536881742            
    ## 3 0.978712791756468 0.0164963281727013           *
    ## 4  1.14691767511065  0.735265482077059            
    ## 5  1.26813473469008 0.0518592554276245

``` r
exampleRR$genotypes[[1]][1:5,]
```

    ##   Locus                 Variant Cases Controls      RelativeRisk
    ## 1     A 01:01:01:01+01:01:01:01     8        7  1.06936026936027
    ## 2     A 01:01:01:01+02:01:01:01     4        5 0.890230270511961
    ## 3     A    01:01:01:01+02:05:01     9       11 0.900910010111224
    ## 4     A 01:01:01:01+03:01:01:01    13       12  1.04263959390863
    ## 5     A    01:01:01:01+03:01:03    12        9  1.14691393798899
    ##              CI.low          CI.high           p.value Significant
    ## 1 0.664735770005212 1.72027960173905   0.7895603369942            
    ## 2 0.428256020543676 1.85055176464232 0.742918500771633            
    ## 3 0.553846329803078 1.46545856249907 0.659670604051562            
    ## 4 0.713590916343736 1.52341810677183 0.832674625598276            
    ## 5 0.789817680366197 1.66546231345888 0.504666081455455
