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

#### 
lm(mpg ~ vehicle_length + vehicle_weight + spoiler_angle + ground_clearance + AWD, data=mechaCar_mpg)

#### 
summary(lm(mpg ~ vehicle_length + vehicle_weight + spoiler_angle + ground_clearance + AWD, data=mechaCar_mpg))

![image](https://user-images.githubusercontent.com/94234511/158046879-0e5380c9-1317-427e-92d3-b192f33b04ce.png)

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

![image](https://user-images.githubusercontent.com/94234511/158046916-32532c1b-e31f-4d95-92c0-a36863f4d4a4.png)


#### The suspension coil’s PSI continuous variable across all manufacturing lots

![image](https://user-images.githubusercontent.com/94234511/158047046-09cd014b-09f0-4f34-a2a6-e96967ce4d8b.png)

total_summary dataframe should look like this:
![image](https://user-images.githubusercontent.com/94234511/158047190-b76cd3d5-4541-486e-8872-edc8b1dc8eea.png)

#### The following PSI metrics for each lot: mean, median, variance, and standard deviation.
lot_summary dataframe should look like this:
![image](https://user-images.githubusercontent.com/94234511/158047209-6da957dd-5d98-4b54-adfc-9352229116e2.png)

### Summary Statistics on Suspension Coils

The design specifications for the MechaCar suspension coils dictate that the variance of the suspension coils must not exceed 100 pounds per square inch. Does the current manufacturing data meet this design specification for all manufacturing lots in total and each lot individually? Why or why not?

The variance of manufacturing lots 1 and 2 meet the design specification of a variance less than 100 psi.  However, the data for lot 3 shows some drift and the variance was 170.29 psi.  Therefore, lot 3 is out of specification.  Parts should be sequestered and a root cause investigation initiated.

![image](https://user-images.githubusercontent.com/94234511/158047442-6f316441-2b1c-4a25-b1f8-101caa75c7ac.png)

### Deliverable 3: T-Tests on Suspension Coils
perform t-tests to determine if all manufacturing lots and each lot individually are statistically different from the population mean of 1,500 pounds per square inch.

#### T-Tests on Suspension Coils

#### In your MechaCarChallenge.RScript, write an RScript using the t.test() function to determine if the PSI across all manufacturing lots is statistically different from the population mean of 1,500 pounds per square inch (psi).

![image](https://user-images.githubusercontent.com/94234511/158047538-70139f63-4c08-46ea-9340-62fdc337b9a1.png)

t.test(mecha_coil$PSI,mu=1500)

The true mean of the sample is 1498.78, see also the summary statistics above. With a p-value of 0.06, which is higher than the significance level of 0.05, there is not enough evidence to reject the null hypothesis. This analysis indicates that the mean of all three manufacturing lots is statistically similar to the presumed population mean of 1500 psi.

#### Next, write three more RScripts in your MechaCarChallenge.RScript using the t.test() function and its subset() argument to determine if the PSI for each manufacturing lot is statistically different from the population mean of 1,500 pounds per square inch (psi).

lot1 <- subset(mecha_coil, Manufacturing_Lot=="Lot1")
lot2 <- subset(mecha_coil, Manufacturing_Lot=="Lot2")
lot3 <- subset(mecha_coil, Manufacturing_Lot=="Lot3")

![image](https://user-images.githubusercontent.com/94234511/158047672-d343432d-4442-4158-a1af-1449f7e80fc0.png)

![image](https://user-images.githubusercontent.com/94234511/158047695-5e62319f-5063-4426-8150-15b3988629be.png)

![image](https://user-images.githubusercontent.com/94234511/158047711-5f7db020-dac9-4866-b764-4aa8a10bed67.png)

A summary of the individual lot data can be seen below:

Lot 1 has a true sample mean of 1500psi, again as we saw in the summary statistics above. With a p-value of 1, clearly we cannot reject the null hypothesis that there is no statistical difference between the observed sample mean and the presumed population mean as both are equal to 1500psi.
Lot 2 has essentially the same outcome with a sample mean of 1500.02, a p-value of 0.61; the null hypothesis cannot be rejected.  The sample mean and the population mean of 1500psi are statistically similar.
However, the data for Lot 3 illustrates a different hypothesis.  Here, the sample mean is 1496.14psi and the p-value is 0.04, which is lower than the stated significance level of 0.05. Therefore, we would reject the null hypothesis that the lot 3 sample mean and the presumed population mean are not statistically different.

### Deliverable 4: Design a Study Comparing the MechaCar to the Competition

### Study Design: MechaCar vs Competition

Write a short description of a statistical study that can quantify how the MechaCar performs against the competition. In your study design, think critically about what metrics would be of interest to a consumer: for a few examples, cost, city or highway fuel efficiency, horse power, maintenance cost, or safety rating.

#### In your description, address the following questions:

What metric or metrics are you going to test?
The average highway fuel efficiency (hmpg) is 10% higher for the MechaCar than all other cars in the same price range. 

What is the null hypothesis or alternative hypothesis?
On average the MechaCar has a 10% higher highway fuel efficiency than other models in the same price range ($19,000-$22,000)
The average fuel efficiency of the MechaCar is statistically similar to all other models in the same price range.

What statistical test would you use to test the hypothesis? And why?

A one sample t-test to compare the MetaCar highway fuel efficieny to the average of all competitors in the price range.
![image](https://user-images.githubusercontent.com/94234511/158049500-856855fe-c109-44fb-be9e-b46df9491c36.png)

What data is needed to run the statistical test?

The price of the MechaCar and all other cars or at least one other model in the same price range for comparison (assume range is base price($) +/- $1000.00) 

The highway fuel efficieny in miles per gallon (mpg) for the MechaCar and at least one other car to be compared. 
Note: The methods for collecting and calculating highway fuel efficiency is presumed to be the same and enough data is available for both samples (models of cars) to calculate an average.   

If data is available from more than one model, the mean highway fuel efficiency could be compared across models using a two sample t-test.
![image](https://user-images.githubusercontent.com/94234511/158049550-2998d062-a54c-43a3-ad66-8234bcd32fc5.png)

