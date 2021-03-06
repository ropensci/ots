ots
===



[![R-check](https://github.com/ropensci/ots/workflows/R-check/badge.svg)](https://github.com/ropensci/ots/actions?query=workflow%3AR-check)

`ots` is an R client to retrieve data from various ocean time series datasets, including:

* BATS
* HOT
* CALCOFI
* LTER Kelp
* UOPG
* more to come...

Jump over to the issues page to suggest data sets to include or comment on ongoing data source integration progress.

What's the point of getting data from the web in R? This way we only have to solve the problem of how to efficiently get a dataset once, then you can benefit from that. In addition, this should allow you to get any changes to the dataset that appear, or corrections. Last, getting data programatically in R should get you one step closer to a reproducible workflow, one that makes science easier primarily for yourself, and for others using your work.

## Install


```r
install.packages("devtools")
devtools::install_github("ropensci/ots")
```


```r
library("ots")
```

## Easy integration with dplyr


```r
library('dplyr')
tbl_df(bats("zooplankton")$data) %>% 
  filter(sieve_size > 1000) %>% 
  group_by(cruise) %>% 
  summarise(mean_water_vol = mean(water_vol))
```

## BATS - Zooplankton dataset


```r
bats("zooplankton")
```

## BATS - Production dataset


```r
bats("production")
```

## HOT dataset


```r
hot()
```

## Channels Islands National Park kelp data


```r
kelp("benthic_cover")
```

## CALCOFI data


```r
calcofi('hydro_cast')
```

## UOPG data

Various datasets available through this source - in this example getting data from Biowatt, and getting the meteorology data. Note that we still need to fix the column names...


```r
(biowatt_met <- uopg(dataset = 'biowatt', type = "meteorology"))
```

## More coming...

## Meta

* Please [report any issues or bugs](https://github.com/ropensci/ots/issues).
* License: MIT
* Get citation information for `ots` in R doing `citation(package = 'ots')`
* Please note that this package is released with a [Contributor Code of Conduct](https://ropensci.org/code-of-conduct/). By contributing to this project, you agree to abide by its terms.

[![ropensci](https://ropensci.org/public_images/github_footer.png)](https://ropensci.org)
