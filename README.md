## Problem Statement
Gross domestic product (GDP) is the value of all products produced in a country. It is also widely used to assess whether a country's economic situation is healthy. The gross domestic product includes all industries, and we can study the economic structure of a country through data analysis of industry contribution to GDP. 

The government hired me to predict the GDP for helping them plan for making the policy change. I chose quarterly real GDP as my data because real GDP is GDP that has adjusted price change(i.e. inflation and deflation).

## Executive Summary 
The entire modeling process is divided into three distinct parts. The first part is the data collection. The Organisation for Economic Co-operation and Development (OECD) has more open historical data than the US government. The data can track back to 1949, but I was not sure of its accuracy. For verification, I compare the data with the real gross domestic product from the Bureau of Economic Analysis data. After approving the two data frames show the same result, I can use the real GDP from 2019-01-01 to calculate all the real GDP data back to 1949.

The second part is the exploratory data analysis. I used the line chart to see the trend of GDP data and plotted ACF and PACF to check the autocorrelation of past GDP. Then, I used seasonally decompose figure to see if the data is seasonal or not. Applied the rolling mean and standard deviation and dicky-fuller test to see if the data meet the stationary.  

The third part is modeling, which can be divided into feature selection and model selection. During feature selection, I split the training and testing data in two ways. The first one is to simply split the data by 80% and 20%. The second one is to split the data in the first quarter of 2009. In the model selection, I have tried AR, SARIMAX, and Holt-Winter’s model. Then I applied the mean square error and visualized the accuracy of the models. The score is high, so I check all the other features in the new data frame. Finally, I chose three and five features to build the models and make predictions.

## Conclusions 
First of all, the real GDP growth has been over 1200% since 1949. The huge decline in 2009 was because of the financial crisis that began in the United States and the global economic recession that caused the world’s economic recession. Second, the dropped of the GDP in 2009 is nonpredictable by only the historical GDP data. After I set the testing data to start in the first quarter of 2009, all models have a momentous increase in prediction accuracy. Finally, the best model is the AR model with a testing set split in the first quarter of 2009. It has the train MSE score as 0.1212842274098629 and the test MSE score as 0.442737046695025 which make it become a slightly overfit but acceptable model.

## Source
- GDP:
    - BEA: https://apps.bea.gov/iTable/iTable.cfm?reqid=19&step=2#reqid=19&step=2&isuri=1&1921=survey
    - OECD: https://stats.oecd.org/index.aspx?queryid=350
- Economic drop:
    - https://www.marketwatch.com/story/us-exports-fall-in-2015-for-first-time-since-recession-2016-02-05
    - https://www.forbes.com/2009/01/14/global-recession-2009-oped-cx_nr_0115roubini.html#49d387e5185f
- Model:
    - https://www.youtube.com/watch?v=e8Yw4alG16Q
    - https://www.biaodianfu.com/acf-pacf.html
    - https://machinelearningmastery.com/time-series-forecasting-methods-in-python-cheat-sheet/
    - https://machinelearningmastery.com/sarima-for-time-series-forecasting-in-python/
    - https://medium.com/datadriveninvestor/how-to-build-exponential-smoothing-models-using-python-simple-exponential-smoothing-holt-and-da371189e1a1