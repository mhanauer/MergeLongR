---
title: "Merging Longitudinal Data in R"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```
Here is an example of how to merge data in R with a longitudinal study.  In this example, we initially asked for participants ethnicities in the data set dataTest.  Given that ethnicity does not change over time, we do not want the participants to insert their ethnicity every time, so we only ask them once and match their unique id and ethnicity with their unique id in the data that we collected from their responses over time (i.e. dataTest1).  This process is relatively simple using the merge, and within merge, by function.  We merge the two data sets on the unique id variable by the id variables and every time a unique id is present, the participant's id filled in.  In this example, every person is measured four times, therefore, each of the four occasions an id is present in the later data set (i.e. dataTest1 in this example), the ethnicity associated with that id from the initial data set (i.e. dataTest) is inputted.  For example, person 20 is Asian American (AA) therefore, in the later data set, dataTest1, each of the four measurements for person 20 is Asian American, while each of the four measurements for person 21 is White, because in the initial data set (i.e. dataTest) person 21 is White. 
```{r}
dataTest = data.frame(id = 1:100, ethnicity = c(rep("AA", 20), rep("WHITE", 30), rep("AI", 20), rep("BLACK", 30)))
head(dataTest)
dataTest1 = data.frame(id = rep(1:100, each = 4), x1 = rnorm(400), x2 = rnorm(400))
head(dataTest1)
dataTest2 = merge(dataTest, dataTest1, by = c("id"))
head(dataTest2)
dataTest2
```

