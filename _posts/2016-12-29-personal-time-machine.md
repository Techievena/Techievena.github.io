---
layout: post
section-type: post
title: Personal Time Machine
category: machine_learning
tags: [ 'ARIMA', 'Time Modelling', 'Prediction via Analysis' ]
---

## GOING AHEAD OF TIME
Time is the most influential factor in this world. It is abstract. Everything in this world is commanded and decided by time. Nobody can escape the hold of time.  
We all must have read or at-least heard of the all-time classic of H.G. Wells, in which a scientist invents a machine that transports him far into the future where he discovers a changed world inhabited by two unusual races, the Eloi and the Morlocks. From then... or even back, human race has been fantasizing about gaining control over time; because it is the time which gives us the opportunity to make use of it. Those who make best use of time and avail those opportunities grow and rise in life. He is the wisest who makes the best use of time in his hand.  
But what if I say **now you can see your future!!!!** Sounds kinda interesting right?? Ya it's true. Now.... with the advancement of modern technologies, we have come to a stage where we can see ahead of time and if required, be prepared for the same. With the recent developments, going on in the sector of AI and machine learning; Now we can forecast what's going to happen the next day, a day after or even a month after; **all by ourselves.**

This is called Time-series modelling, in which we collect a dataset of events that have happened over a period of time and predict the future by analyzing such a dataset.


**This winter while I was pondering over how to continue learning Data Analytics and Machine Learning; a senior of mine, (Raj Anand) suggested that he'd give me a series of problems to work-out and it proved to be the best way to be in touch with the ML algorithms and programming in R as Data Analytics is a application-based field. So, this was one of them. Here is the [problem](https://github.com/Techievena/Retail-Analysis/blob/master/data.txt) and here is the [dataset](https://github.com/Techievena/Retail-Analysis/blob/master/Retail Analytics.xlsx) I was given to workout upon. So here I will describe all the concepts about time-series modelling while I workout the problem.**  
So, lets see the future!!!  
**NB:-First thing to realise when you get such a dataset is that, this is a time-series before we proceed further processing the data.**


## TIME-SERIES
A time series can consist of the following components:  
- **Trend** refers to the long-term movement. Shows if the values are increasing or decreasing over time.  
- **Seasonality** report the periodic fluctuation and it’s often related to the calendar.  
- **Cyclic** component also refer to a periodic fluctuation but not fixed as the seasonality. For instance the price of many product are influenced by the inflation but these fluctuations are different than seasonality one.  
- **Random** component is what remains after accounting for the other three components listed above. It’s itself composed of noise with underlying structure that needs to be modelled to forecast future values.  
![time-series](https://github.com/Techievena/Retail-Analysis/blob/master/timeseries.jpg?raw=true "Decomposing the data into its components..")

**To model any kind of time-series first of all we need to stationarize it.....**

## STATIONARY TIME-SERIES
A random variable that is a time series is stationary if its statistical properties (mean, variance, autocorrelations, etc.) are all constant over time. Every time series can be made to be “stationary” by differencing, perhaps in conjunction with non-linear transformations such as logging or deflating. A stationary series has no trend, its variations around its mean have a constant amplitude, and it wiggles in a consistent fashion, i.e., its short-term random time patterns always look the same in a statistical sense. The latter condition means that its autocorrelations (correlations with its own prior deviations from the mean) remain constant over time, or equivalently, that its power spectrum remains constant over time. 
![stationary time-series](https://github.com/Techievena/Retail-Analysis/blob/master/stationarytimeseries.png?raw=true)

## THE PROCESS

#### Box-Jenkins methodology:
1. Condition data and select a model
  - Identify and account for any trends or seasonality in the time series
  - Examine the remaining time series and determine a suitable model
2. Estimate the model parameters.
<br><br>3. Assess the model and return to step 1 if necessary.

Now on to data processing .... Our first job will be to complete the empty rows in the dataset and store it in a different file which will be handy for further processing.  
**N.B.:- Handling csv files are much faster in R. Even if no processing is required, kindly make it a habit to convert your xlsx files into csv files when handling large datasets**

<pre><code data-trim class="r">
{% raw %}
setwd("~/R/Working Directory/Retail-Analysis")
library(xlsx)

retailanalytics <- read.xlsx("Retail Analytics.xlsx", sheetIndex = 1)
retailanalytics<-retailanalytics[!is.na(retailanalytics$Item.code),]
test<-retailanalytics
retailanalytics$Date<-as.Date(retailanalytics$Date, "%d/%m/%Y")
dates<-as.vector(test$Date)
dates<-as.numeric(dates)
dates<-as.Date(dates, origin = "1899-12-30")
for(i in 1:length(retailanalytics$Date)){
  if(is.na(retailanalytics$Date[i])){
    retailanalytics$Date[i]=dates[i]
  }
}
date<-NULL
customer<-NULL
for (i in 1:length(retailanalytics$Customer.code)) {
	data<-retailanalytics$Customer.code[i]
	if(is.na(data)){
		retailanalytics$Date[i]<-date
		retailanalytics$Customer.code[i]<-customer
	}
	date<-retailanalytics$Date[i]
	customer<-retailanalytics$Customer.code[i]
}

write.csv(retailanalytics,"Retail Analytics.csv", row.names=F)
{% endraw %}
</code></pre>

So, now we have a complete dataset to workout with. I have stored the above code in a file (datacompletion.R), and will further work on different files reading from **Retail Analytics.csv**  
So we have four columns namely:-  
__Date__  
__Customer.code__  
__Item.code__  
__Units__

## PROCESSING THE TIME-SERIES

## ARIMA

##### AR:- Auto-Regressive (Terms containing lags of the stationarized series in the forecasting equation)

##### I:- Integrated (Version of a time series which needs to be differenced to be made stationary)

##### MA:- Moving Average (Terms containing lags of  of the forecast errors in the forecasting equation)
A time-series can be viewed as a combination of signal and noise, and the signal could be a pattern of fast or slow mean reversion/sinusoidal oscillation/rapid alternation in sign, and it could also have a seasonal component.  An ARIMA model can be viewed as a “filter” that tries to separate the signal from the noise, and the signal is then extrapolated into the future to obtain forecasts.  
The ARIMA forecasting equation for a stationary time series is a linear (i.e., regression-type) equation in which the predictors consist of lags of the dependent variable(p) and/or lags of the forecast errors(q).

To identify the ARIMA model, first we must get acquainted with the tools for model determination...

## ACF AND PACF PLOTS
**ACF PLOTS**  
The autocorrelation function (ACF) plot shows the correlation of the series with itself at different lags  
*The autocorrelation of Y at lag k is the correlation between Y and LAG(Y,k)*  
**PACF PLOTS**  
The partial autocorrelation function (PACF) plot shows the amount of autocorrelation at lag k that is not explained by lower-order autocorrelations  
*The partial autocorrelation at lag k is the coefficient of LAG(Y,k) in an AR(k) model, i.e., in a regression of Y on LAG(Y,1), LAG(Y,2), .. up to LAG(Y,k)*
![acf and pacf plot](https://github.com/Techievena/Retail-Analysis/blob/master/acfpacf.png?raw=true)

The ARIMA model is the general class of model for time-series forecasting and there are systematic set of rules for determining the model of ARIMA(p,d,q) forecasting equation, i.e. predicting *p(AR term)*, *d(I term)* and *q(MA term)*........ 

## RULES FOR DETERMINING ARIMA(P,D,Q) MODEL

>__(i)__ First determine whether a nonlinear transformation such as logging or deflating is necessary to straighten out exponential growth curves  and/or stabilize the variance (i.e., to make the local random variations in the series roughly the same in magnitude from beginning to end).  
>If so, then apply the transformation.    

>__(ii)__ If the series looks non-stationary at this point i.e., if it displays a trend or random-walk behavior —> set the order of nonseasonal differencing to 1.  
>If it still displays a trend or is only slowly mean-reverting after one order of differencing, don’t immediately apply another order of differencing, but keep it in mind for later on (step(vi) below).    

>__(iii)__ Look  at the ACF and PACF plots of the series  you have  at this point. If you don’t see any significant autocorrelations, then stop. You’re done!  
>You’ve identified either a mean model or a random walk model, depending on whether you used 0 or 1 order of differencing in getting to this point.    

>__(iv)__ If you do see some significant autocorrelations, and if the first one or two bars on the ACF plot are significant and negative, followed by a fairly sharp cutoff, while the PACF plot shows a more gradual decay pattern from below, that is a clear sign that you need at least one MA term (i.e., q=1 or q=2).  
>On the other hand, if the first one or two bars on the PACF plot are significant and positive, followed by a fairly sharp cutoff, while the ACF plot shows a more gradual decay pattern from above, that is a clear sign that you need at least one AR term (i.e., p=1 or p=2).  
>If you see one of these two patterns, enter a 1 in the MA box or the AR box, depending on which one it is. If you already have a 1 there, make it a 2.  
>Fit the model and look at the ACF and PACF plots and time series plot of the residuals. If any of the first one or two bars are significant in the ACF or PACF plot, apply the same reasoning as above to determine whether to increase the MA order or AR order by one more. You should not go above 2 except in very rare circumstances.  
>**N.B.:- You should use only AR coefficients or only MA coefficients except in very rare circumstances, i.e., either the MA order will be zero or the AR order will be zero. (Occasionally one of them will be 2 and the other will be 1, but not very often.)**    

>__(v)__ Do not pay any attention to isolated spikes in the ACF or PACF plot beyond lag 3 if you are working with nonseasonal data. You are mainly interested in the first few autocorrelations and partial autocorrelations.  
>Beyond that, don’t look at individual autocorrelations; you just look to see if there is some systematic pattern.(for seasonality)    

>__(vi)__ If the residuals of the model you converged on in step(iv) do not look quite stationary; e.g., if there is a sort of “wave” pattern or other non-random pattern in the residuals, then you may want to increase the order of differencing.  
>Also, if you have one or more AR coefficients in the model at this point, add their values together and check to see if it is very close to 1 (say, on the order of 0.95 or more). If so, that is also a sign that you should try a higher order of differencing.  
>If you see either of these patterns, set the MA and AR orders back to zero and increase the order of differencing by 1 if the current value is 0 or 1. If you have 2 differences at this point, remove any constants in model.  
>Fit this model (which will have only differences and no AR or MA coefficients) and look at the ACF and PACF of the residuals. Go back to steps (iii) and (iv) at this point and apply the same reasoning to determine whether you need to add AR or MA coefficients.    

>__(vii)__ Each time you fit a model, you should look at the t-stat and p-value of the highest-order AR coefficient and highest-order MA coefficient, in order to check their significance. For example, if there are two AR coefficients, you should only check the significance of the AR(2) coefficient. If it is not significant by the usual regression standards (i.e., if its t-stat is less than 2), you should probably decrease the AR order by 1 or decrease the MA order by 1, as the case may be.    

>__(viii)__ Beware of “overdifferencing” as well as “underdifferencing”.  If you have one or more MA coefficients in the model, add their values together and see if it is very close to 1 (say, greater than 0.95). If so, that is a sign that you may have taken higher order of differencing. If so, reduce the order of differencing by 1 and also reduce the MA order by 1 and re-fit the model.    

>__(ix)__ Ideally you will end up with a fairly simple model whose highest-order coefficients are significant and which has no significant residual autocorrelations and shows no signs of under-differencing or over-differencing. Also, you should check the residual normal probability plot to make sure it looks OK, as with any type of forecasting model.

😉