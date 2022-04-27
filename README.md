<h1 align="center"> Yes-Bank-Stock-Prediction </h1>

<h3 align="center"> AlmaBetter Verfied Project - <a href="https://www.almabetter.com/"> AlmaBetter School </a> </h5>

<p>In this project i have developed Auto ARIMA model in Python which predicts the stock closing price of yes bank.</p>

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<h2> :floppy_disk: Project Description</h2>

Analyzing the data of yes bank stock price. data from 2005 to 2020.
We have been given the data of Yes Bank stocks prices. Our first aim to understand the, what is stock market? How it works actually? And basic terminologies like stock opening price, closing, high, low etc. Our second aim is to identify actionable insights from our data and use basic analysis to give conclusions about key aspect of our data.
      Our problem statement was, "Yes Bank is a well-known bank in the Indian financial domain. Since 2018, it has been in the news because of the fraud case involving Rana Kapoor. Owing to this fact, it was interesting to see how that impacted the stock prices of the company and whether Time series models or any other predictive models can do justice to such situations. This dataset has monthly stock prices of the bank since its inception and includes closing, starting, highest, and lowest stock prices of every month. The main objective is to predict the stock’s closing price of the month".
      
 <img target="_blank" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQTRv3JihQuhGdRxFQGzt5mvuc6QGuQ_q_hkw&usqp=CAU.jpg" width=1000; height=300>
 
 ![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)
 
 <h2> :floppy_disk: Dataset Overview</h2>

What is stock?

A Stock or share (also known as a company’s 'equity') is a financial instrument that represents ownership in a company. Units of stock are called "shares." Stocks are bought and sold predominantly on stock exchanges, though there can be private sales as well, and are the foundation of many individual investors' portfolios.

Since, we've the YES BANK Stock price dataset which has the monthly stock prices. It contains the following features:

Open - The opening price is the price at which a security first trades upon the opening of an exchange on a trading day i.e. buyers and sellers meet to make deals with the highest bidder, the opening price may not have to be the same as the last day's closing price.

High - The high is the highest price at which a stock traded during a period.

Low -The low is the highest price at which a stock traded during a period.

Close -The closing price is a stock's trading price at the end of a trading day. This makes it the most recent price of a stock until the next trading session. The closing price is calculated as the weighted average price of the last 30 minutes, i.e. from 3:00 PM to 3:30 PM in case of equity.

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<h2> :book: LSTM </h2>
Long short-term memory (LSTM) is an artificial recurrent neural network (RNN) architecture used in the field of deep learning (DL). Unlike standard feedforward neural networks, LSTM has feedback connections. It can process not only single data points (such as images), but also entire sequences of data (such as speech or video). For example, LSTM is applicable to tasks such as unsegmented, connected handwriting recognition, speech recognition and anomaly detection in network traffic or IDSs (intrusion detection systems).

A common LSTM unit is composed of a cell, an input gate, an output gate and a forget gate. The cell remembers values over arbitrary time intervals and the three gates regulate the flow of information into and out of the cell.

LSTM networks are well-suited to classifying, processing and making predictions based on time series data, since there can be lags of unknown duration between important events in a time series. LSTMs were developed to deal with the vanishing gradient problem that can be encountered when training traditional RNNs. Relative insensitivity to gap length is an advantage of LSTM over RNNs, hidden Markov models and other sequence learning methods in numerous applications.

for detail information read this:

https://www.analyticsvidhya.com/blog/2017/12/fundamentals-of-deep-learning-introduction-to-lstm/

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<h2> :book: Auto ARIMA </h2>

Just to give a brief about how Auto ARIMA works. Auto ARIMA is like a grid search for time series models, it tries ARIMA, SARIMA, SARIMAX, all ARIMA related models depending on the parameters that are applied to it. The auto_arima function seeks to identify the most optimal parameters for an ARIMA model, and returns a fitted ARIMA model. This function is based on the commonly-used R function, forecast::auto.arima

The auto_arima function works by conducting differencing tests (i.e., Kwiatkowski–Phillips–Schmidt–Shin, Augmented Dickey-Fuller or Phillips–Perron) to determine the order of differencing, d, and then fitting models within ranges of defined start_p, max_p, start_q, max_q ranges. If the seasonal optional is enabled, auto_arima also seeks to identify the optimal P and Q hyper- parameters after conducting the Canova-Hansen to determine the optimal order of seasonal differencing, D.

Here's the link to its documentation and User Guide, if you want to know about it in detail:

https://alkaline-ml.com/pmdarima/0.9.0/modules/generated/pyramid.arima.auto_arima.html

The main idea is that you don't really need to worry about differencing orders and keep trying different orders or look at ACF charts to come to the correct fitted parameters, Auto ARIMA would do that for you automatically.

Here, the parameters which are supplied are: m= 12 indicatinng monthly range of Date

seasonal True, which we saw from the decomposed chart

and max iterations is set to 200 so that it analyses as many possible combinations of parameters before sticking to a local minima. Usually 200 works, However, higher the better, though that may take longer time.

Basic steps to use Auto ARIMA include:

Using the Auto_Arima funtion on the series to obtain Model Parameters (p,d,q) (P, D, Q, m) Using the parameters obtained, running a model through statsmodels ARIMA/SARIMA on your training set Obtaining predicted values on the test set based on the model run in Step 2 Comparing and Plotting predictions to expected values Evaluating the model through MSE OR MAE

for detail information read this:
https://www.analyticsvidhya.com/blog/2018/08/auto-arima-time-series-modeling-python-r/

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<h2> :books: Conclusion:</h2>

1) For LSTM train test split was 70% training & 30% testing. RMSE value is 91.1222 & MSE value is 8,303.2553. that means it is far away from our actual value. 
   
2) Auto ARIMA before removing trend and seasonality:
(we want hieghest Log Likeliohood and lowest information criteria (AIC))
      
i) dataset from 2005 to 2020
Using auto arima model i got SARIMAX model as best model.

Log likelihood:-812.490

AIC: 1630.979
      
ii) dataset from 2005 to 2018
we can see that our log likelihood and aic are improved.

Log likelihood: -699.260

AIC: 1404.520
      
iii) dataset from 2018 to 2020

SARIMA MSE Error: 17585.44134

SARIMA RMSE Error: 132.6101102
      
iv) After plotting graph, the expected and predicted values,initial few are correct but ARIMA is unable to predict the Dip that happened because of the fraud. The MSE was extremely high and not acceptable for prediction models.

3) Auto ARIMA before removing trend and seasonality:

To check if Auto ARIMA works well if the data isnt influenced by 
Frauds or such sudden dips, data from 2018-2020 was neglected for 
trial. data for 2017 was then considered to be test and the remaining
 data before that was considered to be train, the model and the results 
that were obtained as follows:

i) from 2005 to 2017 dataset
we can see that our log likelihood and aic are improved for SARIMAX.

Log likelihood: -585.994

AIC: 1175.988
      
ii) train dataset 2017 dataset
we can see that our log likelihood and aic are improved.

Log likelihood: -502.581

AIC: 1007.162
      
iii) test dataset 2017

SARIMA MSE Error: 7744.831967

SARIMA RMSE Error: 88.0047

R2 : -10.372904694067783

As can be seen by this Model, the 2017 model predictions 
are still very poor. Though MSE is much better than the one 
with all data, it is evident that even with infraudulent data, 
something is wrong.

4) Auto ARIMA after removing trend and seasonality from 2005 to 2017:
This model is MUCH MUCH better than the original 2017 model without detrending.
SARIMAX MSE Error:  578.399636
SARIMAX RMSE Error:  24.0499405

5) Auto ARIMA after removing trend and seasonality from 2005 to 2020:

SARIMAX MSE Error: 989.4628516

SARIMAX RMSE Error: 31.45572844

R2 : 0.9390712571002944

6) After performing different model my best model is SARIMAX model after removing trend and seasonality.getting 93% accuracy. 
 

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)
<h2> :books: References</h2>
<ul>
  <li><p>Medium.com, 'what is auto ARIMA?' [Online].</p>
      <p>Available: https://medium.com/featurepreneur/what-is-auto-arima-b8025c6d732d</p>
  </li>
  <li><p>Wikipedia.org, 'LSTM'. [Online].</p>
      <p>Available: https://en.wikipedia.org/wiki/Long_short-term_memory</p>
  </li>
  <li><p>Wikipedia.org, 'Auto ARIMA'. [Online].</p>
      <p>Available: https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average</p>
  </li>
  <li><p> 'Time series analysis'. [Online].</p>
      <p>Available: https://michael-fuchs-python.netlify.app/2020/10/19/time-series-analysis-working-with-dates-and-times/</p>
  </li>
  <li><p>Manisha-sirsat.blogspot.com, 'What is Confusion Matrix and Advanced Classification Metrics?'. [Online].</p>
      <p>Available: https://manisha-sirsat.blogspot.com/2019/04/confusion-matrix.html</p>
  </li>
  <li><p>analyticsvidhya.com, 'machine learning & deep learning approachr'. [Online].</p>
      <p>Available: https://www.analyticsvidhya.com/blog/2018/10/predicting-stock-price-machine-learningnd-deep-learning-techniques-python/</p>
  </li>
</ul>

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<!-- CREDITS -->
<h2 id="credits"> :scroll: Credits</h2>

< Ashish Gupta > | Data Scientist | Machine Learning Engineer | Deep Learning enthusiast | Statistic Student | Storyteller

<p> <i> Contact me for Data Science Project Collaborations</i></p>


[![LinkedIn Badge](https://img.shields.io/badge/LinkedIn-ashishgupta45?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/ashishgupta45)
[![GitHub Badge](https://img.shields.io/badge/GitHub-Ashishgupta45?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Ashishgupta45)
[![Medium Badge](https://img.shields.io/badge/Medium-1DA1F2?style=for-the-badge&logo=medium&logoColor=white)](https://ashishgupta45.medium.com)


![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)
