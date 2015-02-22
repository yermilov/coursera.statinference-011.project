---
title: "The exponential distribution and the Central Limit Theorem"
---

# The exponential distribution and the Central Limit Theorem
Yaroslav Yermilov

## Overview

In this report we will investigate the exponential distribution and compare it with the Central Limit Theorem. We will investigate the distribution of averages of 40 exponentials in 1000 simulations.

As part of analysys we will:

1. Show the sample mean and compare it to the theoretical mean of the distribution.

1. Show how variable the sample is (via variance) and compare it to the theoretical variance of the distribution.

1. Show that the distribution is approximately normal.


## Simulations

To simulate the exponential distribution R function rexp is used. It's rate is set to 0.2, which means that it's theoretical mean is 1/0.2 = 5 and theoretical standard deviation is also 5. 
We will investigate averages of 40 iid, simulated 1000 times:


```r
number_of_simulations <- 1000
sample_size <- 40
lambda <- 0.2

exp_means <- NULL
for (i in 1:number_of_simulations) exp_means = c(exp_means, mean(rexp(sample_size, rate = lambda)))
head(exp_means)
```

```
## [1] 4.633839 5.545132 4.939696 6.926401 5.269258 5.312287
```

Let's look at distribution histogram:


```r
library(ggplot2)

data_frame <- data.frame(exp_means)

ggplot(data_frame, aes(x = exp_means)) + 
geom_histogram(aes(y = ..density..)) + 
geom_density(size = 2, color = "red") + 
labs(x = 'Value') +
labs(y = 'Count')
```

```
## stat_bin: binwidth defaulted to range/30. Use 'binwidth = x' to adjust this.
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2-1.png) 
