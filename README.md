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
First, we looked at the response variable Texas Covid Case Count to determine stationarity. Based on teh autocorrelations and the Parzen window, there is strong evidence of wandering and we see some evidence of a seven day periodic trend both causing non-constant mean. We speculate the seven day periodic trend is likely attributed to some sort of reporting bias. The first and second have autocorrelation comparison gives us confidence the autocorrelation is staying relatively constant. Since the data is non-stationary, the data will need to be differenced and/or have the frequency removed in the models to stationarize the data.

<img width="706" alt="image" src="https://user-images.githubusercontent.com/37990637/157996557-1dd21c09-dddc-4d7b-954a-16e351224524.png">

Next, we looked at the included features that could help us model the response. Google mobility trends offer us insight into the reletive activity into different public sectors. Vaccinations contribute to decreasing the rate of spread. Covid testing can be a leading indicator that describes the relative proportion of the population who thinks they may have covid.

<img width="706" alt="image" src="https://user-images.githubusercontent.com/37990637/157996581-22939eac-6d0c-406d-875b-c0980beee62e.png">


[Back to Top](#BackToTop)


---

<a name="Comparing_Models"></a>

## Comparing Models

The team first explored a simple univariate ARIMA model. By differencing the data and finding the lowest ARMA AIC, we were able to identify the ideal ARIMA model.

<img width="706" alt="image" src="https://user-images.githubusercontent.com/37990637/157997288-321870de-ed69-4f95-a23a-d9566b308052.png">

Plotting the 21 day forecast of Texas Covid Case Count with a 95% confidence interval.

<img width="427" alt="image" src="https://user-images.githubusercontent.com/37990637/157997317-9b0b6ce2-2d1c-412a-82f1-b1372065d3da.png">

Next, the team explored a multi-variate Vector Autoregressive (VAR) model. All the exanatory variable were included in this model. Utilizing AIC and BIC, we confirmed a lag of 8 was the ideal lag for this model. Plotted are the 95% confidence intervals for the forecast of all the included variables. To the right, are the features and coefficients in the model along with their significance.

<img width="706" alt="image" src="https://user-images.githubusercontent.com/37990637/157997444-03a944b9-90d5-49c0-86b1-3dcdc4e965d8.png">

Plotting the 21 day forecast of Texas Covid Case Count with a 95% confidence interval.

<img width="466" alt="image" src="https://user-images.githubusercontent.com/37990637/157997459-a3ecddb1-3045-4b8d-a09b-0cdb6cb70f89.png">

Moving into more complex models, the team trialed a Multi-Layer Perceptron (MLP) Model. Below, is a mapping of the network along with the chosen parameters of the model. The model was trained 20 different times and the median value of the different models was used as the forecast. The number of layers and nodes per layer was verified by cross validation.

<img width="706" alt="image" src="https://user-images.githubusercontent.com/37990637/157997503-639e5e6d-9f23-4ce0-82fb-9b65473b9aa4.png">

Plotting the 21 day forecast of Texas Covid Case Count. Colors: Blue - Actual Case Count, Black - Forecast of Case Count, Grey - 20 different trained models

<img width="478" alt="image" src="https://user-images.githubusercontent.com/37990637/157997520-d8b39f6b-0af2-4bf4-b984-c04e8f13288f.png">

With both the VAR and MLP models outperforming the more simplistic ARIMA model, and ensemble model was generated using both models. The mean of the forecast of both models was used to forecast Case Count. The plot shows the 21 day forecast of Texas Covid Case Count.

<img width="706" alt="image" src="https://user-images.githubusercontent.com/37990637/157997558-e4902723-0bf9-4c91-80fd-f427dcef1e5e.png">

To better see how the forecast of the ensemble model is performing, the last 100 observations were included in the plot.

<img width="706" alt="image" src="https://user-images.githubusercontent.com/37990637/157997581-e9e289cc-e59d-4517-adab-dbfa2bfa5ce6.png">

In the final comparison, we can see the RMSE of the ensemble model is the lowest for the short and long term forecast. Therefore, we will move foreward with this as our final model.

<img width="706" alt="image" src="https://user-images.githubusercontent.com/37990637/157997604-5f7d9d67-ab11-4c51-836c-f3616020bbe9.png">


[Back to Top](#BackToTop)



---

<a name="Conclusion"></a>

## Conclusion

The goal here was to forecast Texas Covid Case Count with Time Series analysis. After extracting and cleaning the data for analysis, our team performed a thourough analysis using simple and complex models such as ARIMA, VAR, MLP, and Esembling Techniques. The final model with ensembling VAR and MLP achieved a final RMSE of 903 for the one week forecast and 1032 for the three week forecast. For a state with over 29 million people, this forecast using mobility, vaccinations, and testing data is more than sufficient to give policy makers a clear idea of the upcoming covid case trends. With this information, more informed policy decisions can be made.

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
