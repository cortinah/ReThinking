---
title: 'The Riddler: Santa Needs Some Help With Math'
author: Hernando Cortina
date: '2018-12-22'
slug: the-riddler-santa-needs-some-help-with-math
categories:
  - R
tags:
  - Riddler
  - Math
---

For the last [Riddler](https://fivethirtyeight.com/features/santa-needs-some-help-with-math/) of the year I attempt to solve both the Express and Classic Riddlers!

### Riddler Express: How Long Will it Take Santa to Place his Reindeer?
We need to find out how long it will take Santa to place his reindeer in the correct sled positions, if he proceeds at random. It takes a minute to harness a reindeer, and the reindeer will grunt to indicate it's in the right position.

Thinking in terms of a probability tree, if we consider the first position in the sled, the expected time that it will take to place the reindeer correctly looks like this:
<img src="/post/2018-12-22-the-riddler-santa-needs-some-help-with-math_files/ridlerexpressanta.png" alt="" width="900px"/>

The expected time that it will take for the first reindeer placed correctly is the sum of all the paths leading to the green circles. For example:

$$
E[T_{8}] = \left (\frac{1}{8} \cdot 1 \right) + \left (\frac{7}{8} \cdot \frac{1}{7} \cdot 2  \right ) + \left (\frac{7}{8} \cdot \frac{6}{7} \cdot\frac{1}{6} \cdot 3  \right ) + ...
$$

This process can be repeated for each of the eight deer, with the tree getting one branch shorter for each deer that has been already correctly placed. The expected time to place all eight deer would then be the sum of the expected time for each deer i in 8 to 1:

$$
E[T] = \sum E[t_{i}]
$$

To generalize this problem to a sled with N deer, I coded the expected time in R as follows:


```r
raindeer <- function(N) {
  if (N==2) return(3/2)
  if (N==1) return(1) 
  n <- N
  t <- 2
  T <- (1/n)
  while (n>2) {
    T <- T + ( prod(seq(N-1,2)[1:(t-1)]) / prod(seq(N,3)[1:(t-1)]) ) * ((1/(n-1))*t)
    t <- t+1
    n <- n-1
  }
  T <- T + ( prod(seq(N-1,2)[1:(t-2)]) / prod(seq(N,3)[1:(t-2)]) ) * ((1/(n))*t)
  T
}

sled <- function(N) sum(sapply(1:N, raindeer))

sled(8)
```

[1] 22

So it should take Santa on average about 22 minutes to get his eight-deer sled ready to go. But what if Santa was riding an XL eighteen-deer rig? Over an hour and a half of setup time!


```r
sled(18)
```

[1] 94.5
