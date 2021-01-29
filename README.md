---
title: "Brexit Poll Data Analysis (plot included)"
author: "Can Li"
#date: "`r format(Sys.Date())`"
output: github_document
---

#### **Overview**

- In June 2016, the United Kingdom (UK) held a referendum to determine whether the country would "Remain" in the European Union (EU) or "Leave" the EU. This referendum is commonly known as Brexit. Although the media and others interpreted poll results as forecasting "Remain" ( p>0.5, p indicating the proportion voted "Remain") , the actual proportion that voted "Remain" was only 48.1%  (p=0.481)  and the UK thus voted to leave the EU. Pollsters in the UK were criticized for overestimating support for "Remain". 

-  This is a report on polling data _brexit_polls_ from the _dslabs_ package, which contains actual polling data for the 6 months before the Brexit vote. I develop polling models to forecast Brexit results. The code in R generate plots.



```{r setup, include = FALSE}
knitr::opts_chunk$set(message = FALSE,
                      warning = FALSE,
                      fig.align = "center",
                      dev = "png",
                      cache = TRUE)
                
```
#### **I used the following libraries:**
```{r loading-libs}
library(tidyverse)
library(dslabs)
```
#### **and the following dataset:**
```{r read-data, echo=TRUE}
data("brexit_polls")
```

#### **Here we can see the first 5 rows of polling data:**
- Variables include raw proportions of voters preferring "Remain", "Leave", and "Undecided" 

- The spread is the *difference* in the raw proportion of voters choosing "Remain" and the raw proportion choosing "Leave".


```{r table-view, echo=FALSE}
table_view <- top_n(brexit_polls, 5)
table_view
```

#### **Here is the plot I generated:**
```{r plots, echo=FALSE}
## Including Plots
brexit_polls %>% ggplot(aes(enddate, spread, color = poll_type)) +
  geom_smooth(method = "loess", span = 0.3) +
  geom_point() +
  geom_hline(yintercept = -0.038, color="blue") +
  xlab("End Date") +
  ylab("Spread") +
  labs(title = "Spread Over 6 Months before Vote",
       caption = "Blue line indicates the actual spread, both online and telephone polls largely missed predicting.") +
  theme_grey() +
  ggplot2::theme(plot.title = ggplot2::element_text(hjust = 0.5, size=12, color = "purple"))
