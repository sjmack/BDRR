`{r, echo = FALSE}  knitr::opts_chunk$set(   collapse = TRUE,   comment = "#>",   fig.path = "README-" )`

BIGDAWG Relative Risk (BDRR)
============================

v1.0.0.9000 (May 8, 2020)

The BDRR “package” includes one function, *riskRatio()*, which
calculates relative risk and associated measures for BIGDAWG-formatted
genotype datasets, using the fmsb::riskratio function.

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
`p.value`, and `Significant` columns.
