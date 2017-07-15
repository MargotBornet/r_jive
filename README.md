
<!-- README.md is generated from README.Rmd. Please edit that file -->
ajive: Angle based Joint and Individual Variation Explained
-----------------------------------------------------------

**Author:** [Iain Carmichael](https://idc9.github.io/)<br/> **License:** [MIT](https://opensource.org/licenses/MIT)

This package is still under development -- more examples and code revisions coming soon.

Overview
========

Angle based Joint and Individual Variation Explained (AJIVE) is a dimensionality reduction algorithm for the multi-block setting i.e. *K* different data matrices, with the same set of observations and (possibly) different numbers of variables) **AJIVE finds *joint* modes of variation which are common to all *K* data blocks as well as modes of *individual* variation which are specific to each block.** For a detailed discussion of AJIVE see [Angle-Based Joint and Individual Variation Explained](https://arxiv.org/pdf/1704.02060.pdf).

Installation
============

The `ajive` package is currently available using devtools

``` r
# install.packages('devtools')
devtools::install_github("idc9/r_jive")
```

Example
=======

Consider the following two block toy example: the first block has 200 observations (rows) and 100 variables; the second block has the same set of 200 observations and 500 variables (similar to Figure 2 of the AJIVE paper).

``` r
library(ajive)
blocks <- sample_toy_data(n=200, dx=100, dy=500)

data_blocks_heatmap(blocks, show_color_bar=FALSE)
```

![](man/figures/README-unnamed-chunk-3-1.png)

After selecting the initial signal ranks we can compute the AJIVE decomposition using the `ajive` function.

``` r
initial_signal_ranks <- c(2, 2) # set by looking at scree plots
jive_decomposition <- ajive(blocks, initial_signal_ranks)
```

The heatmap below shows that AJIVE separates the joint and inidividual signals for this toy data set.

``` r
decomposition_heatmaps(blocks, jive_decomposition)
```

![](man/figures/README-unnamed-chunk-5-1.png)
