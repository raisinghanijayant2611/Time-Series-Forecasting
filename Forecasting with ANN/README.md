
# AIM OF THE PROJECT

The problem we are solving here is to forecast the sales of Peanut Butter in the Chicago Region. As a part of our assignment in the fall semester, we solved this using XGboost techniques. Here however, I want to try using ANN to see the power of Sequential models and if we can improve the accuracy

The personal aim of this project is to build a flow of EDA when coming across store datasets, learning on how to use sequential models, what can be the proper procedure for selecting number of layers, units, regularization parameters, evaluation and loss matrices.

Even though, for time series generally models like RNN and LSTM are used, still since we are taking cross-sectional data assumptions, for practice I am going ahead with simple ANN



# ABOUT THE DATA

Data consists of total weekly sales of the peanut butter for a supermarket chain and not for the individual stores. It consists number of combination of brands and labels. Following is the key:

VEND: Number identifying the product vendor (ex. 48001 corresponds to Unilever)
UPC: The product’s universal product code (bar code)
UNITS: Sales volume
DOLLARS: Dollar sales revenue
VOL_EQ: Weight in pounds of a units sold
PPU: Price per unit ($/lb)
F Factor: specifying advertising in the store weekly flyer:
     F = “A” Large size ad.
     F = “B” Medium size ad.
     F = “C” Small size ad.
D Factor: specifying In-Store Display
     D = 0 No In-Store Display
     D = 1 Minor In-Store Display
     D = 2 Major In-Store Display
EST_ACV : estimated all commodity volume which represents the total volume of estimated annual sales in a single store



# TIME SERIES DATA V/S CROSS SECTIONAL DATA

We know that talking in very technical terms, if there is a time series, you generally don't model it like a normal prediction or classification problems due to lags present, i.e. in a time series, what happened today is correlated with events (seasonal or non-seasonal) events of past and thus, treating it as a cross sectional data and doing cross validations, sampling etc. are not recommended.

However, in practical, some problems become really hard to solve if obeying time series rules and thus people try to predict future values by considering the time series data as a cross sectional data and then taking lags and predicting the value based on them. Such a process is also totally valid given that you are following the cross sectional assumptions.




# EDA

- Checking the data structure: Type of columns, missing values, general statistics about numerical columns, duplicates
- Distribution of Data across classes and Categories 
- Outer detection and implementation 
- Multicollinearity detection and correlation with dependent variable 
- Model Implementation: Used 3 layers. Reason being that you should always start from minimum number of layers to avoid overfitting. Based on experiences of different Data Scientists as well, it has been proven that for majority of problems, only one hidden layer is sufficient. Following link provides a very good explaination about this problem: 
https://stats.stackexchange.com/questions/181/how-to-choose-the-number-of-hidden-layers-and-nodes-in-a-feedforward-neural-netw
However, there is no as such fixed procedure for deciding the number of layers. One has to take a look into the data, whether is it linearly seperable or have some positive and strong correlations, or if the validation evaluation is increasing due to addition of layers (overfitting) 



# Result

Forecasting using ANN technique produced a loss of 0.49, which is significant improvement as compared to the RMSE of 0.99 in XGBoost model 
