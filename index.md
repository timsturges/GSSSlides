---
title       : General Social Survey Visualizer
subtitle    : National Attitudes On Spending
author      : Tim Sturges
job         : Audio Engineer, Aspirant Data Scientist
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## About The App

I have created an app which will quickly and easily allow one to explore the 
relationship between two categorical variables related to attitudes on national 
spending as measured by the General Social Survey.  

For those unfamiliar, The General Social Survey is a biennial national survey conducted 
by the National Opinion Research Center at the University of Chicago. It is a reliable 
and thorough measurement of various national attitudes and trends in the United States. 
For more information, please visit the GSS website: http://www3.norc.org/GSS+Website/

--- .class #id 

## More About The App

In the interest of simplicity and focused attention, I have selected a subset of 
variables from the complete survey which are limited to attitudes on national 
spending. Speaking broadly, national populations appear to have strong opinions 
regarding how our tax revenue ought to be spent, and national spending seems to 
be a good indicator for our citizens' attidues regarding national priorities.  

The variables available in the app are both categorical with three response levels: 
"About Right", "Too Little", and "Too Much". The app asks the user to select two 
variables, each of which is a national spending program (or category thereof), and 
a year of interest. This creates a subset of the data based on the year of interest, 
and then renders a mosaic plot representing the relationship between the two variables 
as a box with area porportional to the whole plot. Below the plot is a proportion 
table which explicitly states those proportions as percent values. Following that 
is a Chi-Square test of independence which determines whether or not we can conclude 
that two variables are related at the 5% significance level.

--- .class #id 

## For Example

This is a sample mosaic plot which generates 1000 randomly-generated survey observations. 
Though the observations are randomly generated each time the page is reloaded, 
they are probability weighted, and will therefore tend produce similar results.
![plot of chunk unnamed-chunk-1](figure/unnamed-chunk-1.png) 

--- .class #id 

## For Example Continued


```
##              
##               About Right Too Little Too Much
##   About Right         1.4        8.4      9.6
##   Too Little          1.3        4.2      4.6
##   Too Much            7.9       27.6     35.0
```

```
## Number of cases in table: 1000 
## Number of factors: 2 
## Test for independence of all factors:
## 	Chisq = 4, df = 4, p-value = 0.4
```

```
## [1] "Null Hypothesis: These two variables are independent."
```

```
## [1] "Alternative Hypothesis: These two variables are not independent."
```

```
## [1] "Based on the observed p-value we cannot reject the null hypothesis."
```

--- .class #id 

## Caveat

The data used in the app is drawn from another Coursera MOOC, Data Analysis and 
Statistical Inference with Dr. Mine Çetinkaya-Rundel at Duke University. Although 
I believe that the data is sound, I cannot speak to any preprocessing which the 
data might have undergone in preparation for that course. Thus, it would be cavalier 
to assume that actual conclusions about national attitudes towards spending can 
be drawn from the app.

--- .class #id 

## Problems

I did experience a few problems during the creation of this app. I would have 
liked to improve the mosaic plot in a number of ways. The one used by this app 
calls the "mosaicplot" function in the base {graphics} library. Although it it does 
render the plot well, I would have preferred to superimpose the proportion labels 
on the plot itself, as well as display the p-value as part of the plot, rather than 
adding the separate table and text below. Also, I would liked to have colored the 
plot in a more logical way that better reflects the associations between the variables. 
"mosaicplot" is somewhat limited for these goals, but I was having trouble getting 
other mosaic plot functions (e.g. "mosaic" from {vcd}) to work with shiny. Given 
more time, or perhaps for future apps, these are the problems I would like to address.
