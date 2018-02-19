---
title: Phyllotaxis3D, Belatedly
author: Hernando
date: '2018-02-19'
slug: phyllotaxis3d-belatedly
categories:
  - R
tags:
  - Shiny
  - Phyllotaxis
---

I coded my first R/Shiny app a month ago, but never wrote about it anywhere. Here's the backstory.

# What the heck is phyllotaxis, anyway?

As part of my exploration of the R world I came upon @aschinchon's fantastic [fronkonstin](https://fronkonstin.com/) website. It's a beautiful and creative display of mathematics and art, often pushing the limits of what can be done in a few lines of R [code](https://fronkonstin.com/2017/11/07/drawing-10-million-points-with-ggplot-clifford-attractors/).

Shortly after, I noticed the launch of DataCamp's [projects](https://www.datacamp.com/projects) section, and one of them was by Antonio on [phyllotaxis](https://www.datacamp.com/projects/62). [Phyllotaxis](https://en.wikipedia.org/wiki/Phyllotaxis) is the arrangement of leaves on a plant stem and often follows surprising mathematical arrangements. It's a fun project to hone your ggplot2 skills while also creating some attractive spiral patterns.

That project inspired me to research 3D phyllotaxis patterns and whether I could create something in R to visualize them.  I decided this would be an opportunity to create my first Shiny app in R.  I found that none other than Stephen Wolfram had written about it in [_A New Kind of Science_](http://www.wolframscience.com/nks/p411--growth-of-plants-and-animals/) and created a Mathematica [document](http://demonstrations.wolfram.com/PhyllotaxisSpiralsIn3D/) to view them.  While Mathematica is an awe-inspiring program that still seems ahead of its time, decades after it was released, I imagine that its proprietary nature has somewhat limited widespread adoption, and the document above requires a browser plug-in that few people will have likely installed and adds a barrier to usage. Shiny, which doesn't require any kind of plug-in, seemed to be the perfect tool for the job.

I coded my Shiny app following the general approach of the Wolfram demonstration, but using the plotly package to create the 3D scatters. I tweaked some parameter ranges and default values, and added a slew of color palettes to view the 3D spirals in myriad ways.

Some of the results are here:

<img src = "https://raw.githubusercontent.com/cortinah/ShinyPhyllotaxis3D/master/images/A.png", width = "200", height = "200">
<img src = "https://raw.githubusercontent.com/cortinah/ShinyPhyllotaxis3D/master/images/B.png", width = "200", height = "200">
<img src = "https://raw.githubusercontent.com/cortinah/ShinyPhyllotaxis3D/master/images/C.png", width = "200", height = "200">
<img src = "https://raw.githubusercontent.com/cortinah/ShinyPhyllotaxis3D/master/images/D.png", width = "200", height = "200">
<img src = "https://raw.githubusercontent.com/cortinah/ShinyPhyllotaxis3D/master/images/E.png", width = "200", height = "200">

# The Shiny App
Make your own 3D spirals by trying the app yourself [here](https://cortinah.shinyapps.io/phyllotaxis3d/)

If it doesn't work it's because all time has been used up for a free Shiny app instance at shinyapps.io.  Try again soon.

The code is hosted on [Github](https://github.com/cortinah/ShinyPhyllotaxis3D)

# And @dataandme's Tweet

{{< tweet 955440483932700672 >}}


Thank you for the shout-out Mara - this app wouldn't exist without the encouragement and work of the R community.