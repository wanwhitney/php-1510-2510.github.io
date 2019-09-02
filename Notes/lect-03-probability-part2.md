---
title       : Basic Probability
author      : Adam J Sullivan 
job         : Assistant Professor of Biostatistics
work        : Brown University
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js # {highlight.js, prettify, highlight}
hitheme     :  github     # 
widgets     : [mathjax, quiz, bootstrap, interactive] # {mathjax, quiz, bootstrap}
ext_widgets : {rCharts: [libraries/nvd3, libraries/leaflet, libraries/dygraphs]}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
logo        : publichealthlogo.png
biglogo     : publichealthlogo.png
assets      : {assets: ../../assets}
---  .segue bg:grey






--- .class #id

## Conditional Probability

![xkcd.com](https://imgs.xkcd.com/comics/conditional_risk.png)

--- .class #id

## Conditional Probability 

- Conditional probability imposes a restriction.  
- If we condition on something, then our sample space changes and our probability might as well. 
- This is easiest seen with cards but we can imagine other things to avoid increasing your chances of a gambling addiction. 
- Consider a box of donuts, there are 5 plain donuts, 5 glazed, and 2 jelly. (*Important real life problem*) 

--- .class #id

## Conditional Probability 

- We can calculate your probabilites using R:


```r
donut <- rep(c("plain", "glazed", "jelly"), times=c(5,5,2))
test <- replicate(T, sample(donut,1))
```

```
## Error in integer(n): invalid 'length' argument
```

```r
prop.table(table(test))
```

```
## Error in table(test): object 'test' not found
```

--- .class #id

## Conditional Probability

- Now being the "nice" person I am, I give one of you a jelly donut. 
- Now the probability that another person gets a jelly donut is conditional on the fact that I got rid of one already. 


```r
donut <- rep(c("plain", "glazed", "jelly"), times=c(5,5,2))
test <- replicate(T, sample(donut[-12],1))
```

```
## Error in integer(n): invalid 'length' argument
```

```r
prop.table(table(test))
```

```
## Error in table(test): object 'test' not found
```


--- .class #id

## Why Conditional Probability? 

- We already know that many factors come into play when it comes to health:
    - Age
    - Race
    - Sex
    - Gender
    - Socioeconomics
    - etc...
- As soon as we need to consider these factors we are conditioning our model on these characteristics.




--- .class #id

## Conditional Probability

$$Pr(B|A) = \dfrac{Pr(A\cap B)}{Pr(A)}$$

- Consider the probability of getting a jelly donut given I already gave one away: 


```r
a <- 2/12
b_a <- 1/11
cond <- (a*b_a)/a
cond
```

```
## [1] 0.09090909
```

--- .class #id

## Recall

- We were close with simulation and it was much easier



```r
donut <- rep(c("plain", "glazed", "jelly"), times=c(5,5,2))
test <- replicate(T, sample(donut[-12],1))
```

```
## Error in integer(n): invalid 'length' argument
```

```r
prop.table(table(test))
```

```
## Error in table(test): object 'test' not found
```

- ***See now you don't mind using R, since I could make you do so many fun math formulas instead***