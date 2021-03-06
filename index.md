---
title       : LRM - A Shiny App
subtitle    : Final project for Coursera 'Developing Data Products' course 
author      : Azmi Mohamed Ridwan
job         : Free Agent
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : solarized_light      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
--- 

## Introduction

LRM is a web application which allows the user to interactively experiment with Linear Regression Modelling. The user can select any combination of the available variables and review the result of the model in the display area. 

The features of the application are:
* Select any combination of variables for the modelling
* Select the level of detail for the output report (without recomputing the model)
* Visualization of the Residuals

In this application, the model uses the `mtcars` dataset to predict mileage as a function of the other available variables. However, this application can be easily modified to use other datasets as the documentation is very clear.

--- 

## How to use

> * When the application is first launched, a default model with only one feature `cyl` is executed. The full output from the lm function is displayed on the main display of the application.

> * The user can modify the model by selecting as my features as desired from the checkboxes shown on the left panel of the application. The user can select any combination of features (with a minimum of 1 feature.)

> * The user can also modify the amount of detail for the report. In addition to the full output, the users can also display selected outputs such as the coefficients, residuals or r-squared values. This is done without re-calculating the model which helps to save computational resources.

> * The display is updated once the Submit button has been clicked.

---

## Example plot of Residuals


```r
library(ggplot2)
data(mtcars)
fit <- lm(mpg~cyl,data=mtcars)
par(mfrow=c(2,2),mar=c(2,2,2,2))
plot(fit)
```

![plot of chunk unnamed-chunk-1](assets/fig/unnamed-chunk-1-1.png)

---

## How to customise this app to your model

To change the model in this application requires edits to just 5 location in the Shiny app. These locations are identified by the following comment prefix which can be found with a simple search.
```
# MODIFY:
```
The requires changes required are:

In ui.R
> * List of predictors
> * Text to provide a description of the model 

In server.R
> * Name of the dataset (2 locations)
> * Name of the dependant variable which is used to build the model equation
