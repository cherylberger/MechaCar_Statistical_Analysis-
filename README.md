# MechaCar_Statistical_Analysis-
Module 15 - Statistics and R

## Overview

## Results
### Deliverable 1: Linear Regression to Predict MPG (30 points)
Using your knowledge of R, you’ll design a linear model that predicts the mileage (mpg) of MechaCar prototypes using several variables from the MechaCar_mpg.csv file. Then, you’ll write a short interpretation of the multiple linear regression results in the README.md.
### Linear Regression to Predict MPG

#### Create a new Rscript file and name it MechaCarChallenge.R

#### Install the required libraries
library(dplyr)
library(tidyverse)

#### Load in the csv file from the correct directory and name the data mechaCar_mpg
mechaCar_mpg <- read.csv(file="./Resources/MechaCar_mpg.csv", check.names =F, stringsAsFactors = F)
#### lm(mpg ~ vehicle_length + vehicle_weight + spoiler_angle + ground_clearance + AWD, data=mechaCar_mpg)
#### summary(lm(mpg ~ vehicle_length + vehicle_weight + spoiler_angle + ground_clearance + AWD, data=mechaCar_mpg))

![image](https://user-images.githubusercontent.com/94234511/158045755-c271e870-7404-4a91-9019-69db22931d16.png)

![image](https://user-images.githubusercontent.com/94234511/158045789-01dc89cf-90b1-464d-9cc9-1ca67e0129a0.png)

#### Which variables/coefficients provided a non-random amount of variance to the mpg values in the dataset?
Judging by the Pr(\t\) values for Vehicle Length and Ground Clearance, these varaiables are statistically likely to provide a non-random amount of variance to the model for mileage in this dataset.  In other words, the probability is high that the vehicle length and vehicle ground clearance have a significant impact on miles per gallon (mpg) achievable with the MechaCar prototype. Conversely, the variables for Vehicle Weight, Spoiler Angle, and All Wheel Drive (AWD) have p-values of 0.078, 0.31 and 0.19 respectively, these are above the signifigance level of 0.05 which indicates a random amount of variance with the dataset.

![image](https://user-images.githubusercontent.com/94234511/158046737-e74bb766-b605-4f50-8be2-a3006c922365.png)

#### Is the slope of the linear model considered to be zero? Why or why not?

If the values are expressed in standard notation, the equation for the linear model can be written as:

y = mx + b:
mpg = (6.267)vehicle_length + (0.0012)vehicle_weight + (0.0688)spoiler_angle + (3.546)ground_clearance + (-3.411)AWD + (-104.0)

The p-value: 5.35e-11 is much smaller than the assumed significance level of 0.05%. This indicates there is sufficient evidence to reject our null (H0) hypothesis, which further indicates that the slope of this linear model is not zero.

![image](https://user-images.githubusercontent.com/94234511/158046625-8c6bcad3-d9de-4f63-96db-5ddcba4d2470.png)

#### Does this linear model predict mpg of MechaCar prototypes effectively? Why or why not?
This linear model has an r-squared value of 0.7149. Therefore, approximately 71% of all mileage predictions will be determined by this model. Although the dataset is fairly small, this multiple regression model predicts mileage (mpg) of MechaCar prototypes effectively.

![image](https://user-images.githubusercontent.com/94234511/158045966-cd0b95f3-9b44-4f73-b644-d9787d85e1db.png)

### Deliverable 2: Create Visualizations for the Trip Analysis 
The MechaCar Suspension_Coil.csv dataset contains the results from multiple production lots. In this dataset, the weight capacities of multiple suspension coils were tested to determine if the manufacturing process is consistent across production lots.

#### The suspension coil’s PSI continuous variable across all manufacturing lots
total_summary dataframe should look like this:


#### The following PSI metrics for each lot: mean, median, variance, and standard deviation.
lot_summary dataframe should look like this:


### Summary Statistics on Suspension Coils

The design specifications for the MechaCar suspension coils dictate that the variance of the suspension coils must not exceed 100 pounds per square inch. Does the current manufacturing data meet this design specification for all manufacturing lots in total and each lot individually? Why or why not?


### Deliverable 3: T-Tests on Suspension Coils
perform t-tests to determine if all manufacturing lots and each lot individually are statistically different from the population mean of 1,500 pounds per square inch.

#### T-Tests on Suspension Coils

#### In your MechaCarChallenge.RScript, write an RScript using the t.test() function to determine if the PSI across all manufacturing lots is statistically different from the population mean of 1,500 pounds per square inch.

#### Next, write three more RScripts in your MechaCarChallenge.RScript using the t.test() function and its subset() argument to determine if the PSI for each manufacturing lot is statistically different from the population mean of 1,500 pounds per square inch.

### Deliverable 4: Design a Study Comparing the MechaCar to the Competition

### Study Design: MechaCar vs Competition

Write a short description of a statistical study that can quantify how the MechaCar performs against the competition. In your study design, think critically about what metrics would be of interest to a consumer: for a few examples, cost, city or highway fuel efficiency, horse power, maintenance cost, or safety rating.

#### In your description, address the following questions:

What metric or metrics are you going to test?
What is the null hypothesis or alternative hypothesis?
What statistical test would you use to test the hypothesis? And why?
What data is needed to run the statistical test?



