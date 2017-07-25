---
title: "Power Analysis in R for Multilevel Models"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```
Here is an example of how to merge data in R with a longitudinal study.  In this example, we initially ask for particpants ethnicities.  Given that ethnicity does not change over time, we do not want the particpants to insert their ethnicity every time, so we only ask them once and match their unique and ethnicity with their unique id in the data that we collected    
```{r}
dataTest = data.frame(id = 1:100, ethnicity = c(rep("AA", 20), rep("WHITE", 30), rep("AI", 20), rep("BLACK", 30)))
dataTest
 # Now I need to create a long data without ethnicity and somehow combine them where I fill in the same ethnicity every time a particular id is present.  

dataTest1 = data.frame(id = rep(1:100, each = 4), x1 = rnorm(400), x2 = rnorm(400))
dataTest2 = merge(dataTest, dataTest1, by = c("id"))
dataTest2
```

