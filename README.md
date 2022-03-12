<a name="BackToTop"></a>

# Time Series Forecasting of Texas Covid Cases

**Contributors: Cameron Stewart and Ana Glaser**

>The goal of this project was to utilize a multivariate time series model to forecast Covid-19 Case Count in Texas both one and three weeks ahead. By providing a sufficiently accurate model of Texas Covid Case Count, Texas government leaders could use this model to make informed policy decisions regarding the public's health. This project pulls in data from Texas Department of State Health Services and Google Mobility Trends between March 2020 - November 2021 to model the data. Using R packages lubridate and tidyverse, the team was able to merge the data from the multiple sources as consistent time series objects in a dataframe. Once merged, a through analysis of stationarity was reviewed for the response variable of Case Count. Finally, the team built and compared models ranging from simple univariate ARIMA to more complex ensemble models which combine multi-variate Vector Autoregressive and Multi-layer Perceptron models. Utilizing the ensembled model and one step ahead forecasting, our team was able to reach a one week forecast RMSE 903 Cases and a 3 week forecast RMSE of 1032 Cases.


---


## Table of Contents
- [Data Description](#Data_Description)
- [Exploring Variables](#Exploring_Variables)
- [Comparing Models](#Comparing_Models)
- [Conclusion](#Conclusion)
- [References](#References)


---


<a name="Data_Description"></a>
[Final Presentation]: https://github.com/C-Stewart-GH/Forecasting_Texas_Covid_Case_Count/blob/main/PPT_Files/Final%20Project%20Presentation.pptx

## Data Description
<img width="706" alt="image" src="https://user-images.githubusercontent.com/37990637/157994781-70e46845-b80d-4ac9-b466-678e813ab224.png">
All links in [Final Presentation](https://github.com/C-Stewart-GH/Forecasting_Texas_Covid_Case_Count/blob/main/PPT_Files/Final%20Project%20Presentation.pptx).

<a name="Exploring_Variables"></a>

## Exploring Variables
The dataset consisted of 36 total variables, with a mix of both quantitative and qualitative types. Some initial findings included: no null values, several features of all one level, and correlations up to .95 (from monthly income and job level). "Job roles" produced large differences in attrition rates with the highest being 45% from the sales reps and lowest at 2% from the director roles.  

730 rows consisted of "no" for attrition and 140 rows of "yes". When I first ran my model, the accuracy for just the "yes" attrition level was less than 50%. I then integrated the ROSE package which allowed me to oversample the "yes" class by generating synthetic data based off feature space similarities. ROSE uses a smoothed-bootstrap approach.  

For my ensemble model, I used hard voting to make the final decision between my three meta-algorithms - bagging, boosting, and stacking. The first algorithm used random forest, followed by C5.0. The third algorithm, stacking, used naive_bayes, knn, rpart, svmRadial, and glmnet from the Caret package. My ensemble model produced an accuracy of 87.6%, with a 88.2% sensitivity and 85% specificity. Some of the top features included JobIsaDirector, JobIsSalesRep, Divorce, JobInvolvementScore, and Overtime. 

This plot illustrates some interesting relationships regarding attrition and job roles  

![Job Roles and Attrition](https://github.com/MichaelMazel/Ensemble_Classification_of_Employee_Attrition/blob/main/Employee_Attrition_Prediction_files/figure-gfm/unnamed-chunk-55-1.png)


[Back to Top](#BackToTop)


---

<a name="Comparing_Models"></a>

## Comparing Models
Leadership roles were comprised of 91 females and 98 males, with monthly incomes being 11,993 and 12,672 dollars, respectively. There was not enough evidence to suggest male incomes were significantly different than female incomes (p-value .37). I used a two sample t-test, and corresponding graphs can be found below:  

![Female Incomes](https://github.com/MichaelMazel/Ensemble_Classification_of_Employee_Attrition/blob/main/Employee_Attrition_Prediction_files/figure-gfm/unnamed-chunk-53-3.png)  
![Male Incomes](https://github.com/MichaelMazel/Ensemble_Classification_of_Employee_Attrition/blob/main/Employee_Attrition_Prediction_files/figure-gfm/unnamed-chunk-53-4.png)   


[Back to Top](#BackToTop)



---

<a name="Conclusion"></a>

## Conclusion

The goal here was to predict monthly incomes with linear regression. I used just the quantitative variables, and to meet the assumptions, I log transformed several features, including the response variable. After the assumptions were improved, I used LASSO for variable selection.  Job Level, Total Working Years, and Job Involvement were selected for the model. These achieved a .873 adjusted r-squared, or in other words, 87.3% of the variation in employee monthly incomes could be explained by these three features.
    

[Back to Top](#BackToTop)


---


<a name="References"></a>

## References  

Ensembling methods: https://github.com/kmutya/Ensemble-Learning-in-R   
ROSE: https://www.analyticsvidhya.com/blog/2016/03/practical-guide-deal-imbalanced-classification-problems/   
LASSO: https://rstatisticsblog.com/data-science-in-action/machine-learning/lasso-regression/   

##### Technologies
R Studio  
R version 4.1.2

[Back to Top](#BackToTop)
