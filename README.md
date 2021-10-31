# Assignment-01-R-and-R-Markdown-
ANA 515 
--
title: "ANA 515 Assignment 1"
author: "Akash Chauhan"
date: "10/30/2021"
output:
  html_document:
    df_print: paged
  theme:
    bootswatch: solar
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

##calling packages
```{r library}
install.packages("tidyverse")
install.packages("knitr")
install.packages("bslib")
```-

## calling dataset from github

```{r gundeaths, echo=FALSE}
url <- "https://raw.githubusercontent.com/fivethirtyeight/guns-data/master/full_data.csv"
Gundeaths <- read.csv(url)
dim(Gundeaths)
summary(Gundeaths)
head(Gundeaths)
tail(Gundeaths)
```


## Making subset youth from main dataset (gundeaths)

```{r youth, echo=FALSE}
library(tidyverse)
library(knitr)
library(bslib)
youth<-filter(Gundeaths, age<=65)
## Calling summary for the new dataset
summary(youth)


```


## Inline code

```{r inline-code, echo=FALSE}
##We have data about 100789 individuals killed by guns. Only 15,687 are older than 65. 
```

## Calling graph using ggplot fucntion


```{r youth-dist, echo=FALSE}
youth %>%
  ggplot(aes
         (age)) + geom_freqpoly(binwidth =1)

```

## Distribution of youth race


```{r race-dist, echo=FALSE}
## gun death by race

youth %>%
  ggplot(aes(fct_infreq(race) %>% fct_rev())) + geom_bar() + coord_flip() + labs(x = "victim race")
```

