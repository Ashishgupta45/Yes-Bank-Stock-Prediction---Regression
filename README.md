# Yes-Bank-Stock-Prediction---Regression
Analyzing the data of yes bank stock price. data from 2005 to 2020.
We have been given the data of Yes Bank stocks prices. Our first aim to understand the, what is stock market? How it works actually? And basic terminologies like stock opening price, closing, high, low etc. Our second aim is to identify actionable insights from our data and use basic analysis to give conclusions about key aspect of our data.
      Our problem statement was, "Yes Bank is a well-known bank in the Indian financial domain. Since 2018, it has been in the news because of the fraud case involving Rana Kapoor. Owing to this fact, it was interesting to see how that impacted the stock prices of the company and whether Time series models or any other predictive models can do justice to such situations. This dataset has monthly stock prices of the bank since its inception and includes closing, starting, highest, and lowest stock prices of every month. The main objective is to predict the stock’s closing price of the month".
      Our approach towards problem statement was well decided by all three of us. We have been decided that we will divide the complete project into sub categories  that is read data, fill missing  values, drop NA values and duplicates, univariate  analysis, bivariate  analysis  correlation of our data, implementing different algorithms etc.
     We started with importing libraries needed for entire project, after importing we 
did some basic analysis like head, tail, describe and info of our data and Shape of our data is 185 rows and 5 columns and there are zero null values in our dataframe.Then we checked for null and duplicate data we had zero null and duplicate values in our data frame . Our data frame is now clean. We can perform our other algorithms. Doing this we get some knowledge about data. we have 5 columns i.e. Date, Open, High, Low, Close. we had monthly stock price, The opening price is the price at which a security first trades upon the opening of an exchange on a trading day i.e. buyers and 
sellers meet to make deals with the highest bidder, the opening price may not have to be the same as the last day's closing price, The high is the highest price at which a stock traded during a period, The low is the highest price at which a stock traded during a period, The closing price is a stock's trading price at the end of a trading day. This makes it the most recent price of a stock until the next trading session. The closing price is calculated as the weighted average price of the last 30 minutes, i.e. from 3:00 PM to 3:30 PM in case of equity. 
     The date column needs to be converted into a date time object. This is achieved by using strptime of the date time library. The Given Date format MMM-YY was converted to proper date of YYYY-MM-DD. Then we set date as our index of data. Then we plot a graph to know how price is moving. We found that up until 2018, the stock prices more or less, kept increasing but there was a sudden dip after that. This can be attributed to the Yes bank fraud case against Rana Kapoor.
     Then we performed univariate analysis for dependent and independent variable. When we plot distribution plot for univariate we saw that our data is positively skewed. Then we perform log transformation to convert skewed data to normal distribution. Why do we want data to be normally distributed?
It is the most important probability distribution in statistics because it fits many natural phenomena. Why is skewed data bad? When these methods are used on skewed data, the answers can at times be misleading and just plain wrong. Even when the answers are basically correct, there is often some efficiency lost; essentially, the analysis has not made the best use of all of the information in the data set. We had to convert it into normal distribution using log Transformation. Why we are using log transformation? We are using LOGARITHMIC TRANSFORMATION Because it is Most frequently used transformation is logarithmic transformation. Logarithmically transforming variables in a regression model is a very common way to handle situations where a non- linear relationship exists between the independent and dependent variables.log transformation improves linearity between our dependent and independent variables. It boosts validity of our statistical analyses. Now our all columns are almost normally distributed. Then we did for bivariate analysis Here we saw Close vs. High correlation is 0.98, Close vs. Low correlation is 0.99, Close vs. Open correlation is 0.97. Our all the independent variables are linearly related to our dependent variable. Then we plot correlation plot for our data. We saw that our data is highly correlated with the low and close column and followed by high and close column.
    Then we split our data in test and train. Our splitting ratio was 70%-30%. Our dependent variable in data was Close column and independent variable was
Open, high and low. after splitting we transform our data using minmaxscaler.after this we performed four models of regression are 
following:
1) Linear regression.
   >>score on train was 0.9943
   >>MSE : 19.9885 
   >>RMSE : 4.4708
   >>R2 : 0.9978 
   >>Adjusted R2 :  0.997645
2) Lasso 
   >>lasso score was 0.9943
   >>The best fit alpha value is found out to be : {'alpha': 0.01}
     Using  {'alpha': 0.01}  the negative mean squared error is:  -62.90049172560616
   >>MSE : 20.878651216190214
   >>RMSE : 4.569316274475889
   >>R2 : 0.9977451271971334
   >>Adjusted R2 :  0.997540
3) Ridge 
   >>ridge score was 0.9920
   >>The best fit alpha value is found out to be : {'alpha': 0.001}
     Using  {'alpha': 0.001}  the negative mean squared error is:  -59.333737891184775
   >>MSE : 20.095425485603688
   >>RMSE : 4.48279215284444
   >>R2 : 0.9978297147684337
   >>Adjusted R2 :  0.997632
4) Elastic net regression
   >>The best fit alpha value is found out to be : {'alpha': 0.0001, 'l1_ratio': 0.3}
     Using  {'alpha': 0.0001, 'l1_ratio': 0.3}  the negative mean squared error is: -62.32590181197605
   >>MSE : 21.250552258088767
   >>RMSE : 4.6098321290572795
   >>R2 : 0.9977049622680845
   >>Adjusted R2 :  0.997496

      In the end we have did metrics comparison of linear regression, lasso regression, ridge regression and elasticnet regression. We sort our conclusion by MSE because MSE is used to check how close estimates or forecasts are to actual values. Lower the MSE, the closer is forecast to actual. Our linear regression model best fit because it has less mse value compare to other.

 Conclusion:
1) From price graph we can see until 2018 stock price was increasing but in next year July month suddenly falls. Because of rana kapoor fraud case. 
2) From linear regression we can conclude that there is affect of that fraud news. Because we are getting high accuracy on linear regression.
3) In our data doesn't contain perfect Multicollinearity among independent variable. We can't remove any variable from our data because each of the variables are important for our model.
4) Target variable is highly dependent on input variable.
5) All regression model has given the best result with lowest MSE, RMSE values and highest r2, adjusted 
 r2 value. 
