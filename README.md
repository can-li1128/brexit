#### **Overview**

- In June 2016, the United Kingdom (UK) held a referendum to determine whether the country would "Remain" in the European Union (EU) or "Leave" the EU. This referendum is commonly known as Brexit. Although the media and others interpreted poll results as forecasting "Remain" ( p>0.5, p indicating the proportion voted "Remain") , the actual proportion that voted "Remain" was only 48.1%  (p=0.481)  and the UK thus voted to leave the EU. Pollsters in the UK were criticized for overestimating support for "Remain". 

-  This is a report on polling data _brexit_polls_ from the _dslabs_ package, which contains actual polling data for the 6 months before the Brexit vote. I develop polling models to forecast Brexit results. The code in R generate plots.
                
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
