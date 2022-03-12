<a name="BackToTop"></a>

# Time Series Forecasting of Texas Covid Cases

**Contributors: Cameron Stewart and Ana Glaser**

>The goal of this project was to utilize a multivariate time series model to forecast Covid-19 Case Count in Texas both one and three weeks ahead. By providing a sufficiently accurate model of Texas Covid Case Count, Texas government leaders could use this model to make informed policy decisions regarding the public's health. This project pulls in data from Texas Department of State Health Services and Google Mobility Trends between March 2020 - November 2021 to model the data. Using R packages lubridate and tidyverse, the team was able to merge the data from the multiple sources as consistent time series objects in a dataframe. Once merged, a through analysis of stationarity was reviewed for the response variable of Case Count. Finally, the team built and compared models ranging from simple univariate ARIMA to more complex ensemble models which combine multi-variate Vector Autoregressive and Multi-layer Perceptron models. Utilizing the ensembled model and one step ahead forecasting, our team was able to reach a one week forecast RMSE 903 Cases and a 3 week forecast RMSE of 1032 Cases.

[Youtube Presentation of Final Analysis](https://www.youtube.com/watch?v=aE3cgkNjZpw)

[Presentation Slides](../main/PPT_Files/Final%20Project%20Presentation.pptx)


---


## Table of Contents
- [Data Description](#Data_Description)
- [Exploring Variables](#Exploring_Variables)
- [Comparing Models](#Comparing_Models)
- [Conclusion](#Conclusion)
- [References](#References)


---


<a name="Data_Description"></a>

## Data Description
<img width="706" alt="image" src="https://user-images.githubusercontent.com/37990637/157994781-70e46845-b80d-4ac9-b466-678e813ab224.png">

All links in [References](#References)

<a name="Exploring_Variables"></a>

## Exploring Variables
<img width="1030" alt="image" src="https://user-images.githubusercontent.com/37990637/157996557-1dd21c09-dddc-4d7b-954a-16e351224524.png">


<img width="1039" alt="image" src="https://user-images.githubusercontent.com/37990637/157996581-22939eac-6d0c-406d-875b-c0980beee62e.png">


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

[Youtube Presentation of Final Analysis](https://www.youtube.com/watch?v=aE3cgkNjZpw)

[Presentation Slides](../main/PPT_Files/Final%20Project%20Presentation.pptx)

[COVID-19 Case Data](https://www.arcgis.com/apps/dashboards/45e18cba105c478697c76acbbf86a6bc)

[Vaccination Doses Administered](https://www.arcgis.com/apps/dashboards/45e18cba105c478697c76acbbf86a6bc)

[COVID Test Data](https://www.arcgis.com/apps/dashboards/45e18cba105c478697c76acbbf86a6bc)

[Google Mobility Data](https://www.google.com/covid19/mobility/)

##### Technologies
R Studio  
R version 4.1.2

[Back to Top](#BackToTop)
