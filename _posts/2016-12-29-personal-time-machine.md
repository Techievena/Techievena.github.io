---
layout: post
section-type: post
title: Personal Time Machine
category: machine_learning
tags: [ 'ARIMA', 'Time Modelling', 'Prediction via Analysis' ]
---

### GOING AHEAD OF TIME
Time is the most influential factor in this world. It is abstract. Everything in this world is commanded and decided by time. Nobody can escape the hold of time.
Then came the all-time classic of H.G. Wells, in which a scientist invents a machine that transports him far into the future where he discovers a changed world inhabited by two unusual races, the Eloi and the Morlocks. From then... or even back, human race has been fantasizing about gaining control over time; because it is the time which gives us the opportunity to make use of it. Those who make best use of time and avail those opportunities grow and rise in life. He is the wisest who makes the best use of time in his hand.
But what if I say now you can see your future!!!! Sounds kinda interesting right?? Ya you read it right. Now with the advancement of modern technology we can see ahead of time and be prepared for the same. With the recent developments going on in the sector of AI and machine learning now we have come to a stage where we can forecast what's going to happen the next day, a day after or even a month after; **all by ourself.**
This is called Time-series modelling in which we collect a dataset of events that have happened over a period of time and predict the future by analyzing such dataset.

**This winter I was pondering over how to continue learning Data Analytics and Machine Learning; when a senior of mine, (Raj Anand) suggested that he'd give me a series of problems to work-out and it proved to be the best way to be in touch with the algorithms and commands in R as Data Analytics is a application-based field. So, this was one of them. Here is the <a href="https://github.com/Techievena/Retail-Analysis/blob/master/data.txt" target="\_blank">problem</a> and here is the [dataset](https://github.com/Techievena/Retail-Analysis/blob/master/Retail-Analytics.xlsx) I was given to workout upon. So here I will describe all the concepts about time-series modelling while I workout the problem.**

<br>**NB:-First thing to realise when you get such a dataset is to realise that this is a time-series before we proceed further processing the data.**

#### TIME-SERIES
A time series can consist of the following components:
**Trend** refers to the long-term movement. Shows if the values are increasing or decreasing over time.
**Seasonality** report the periodic fluctuation and it’s often related to the calendar.
**Cyclic** component also refer to a periodic fluctuation but not fixed as the seasonality. For instance the price of many product are influenced by the inflation but these fluctuations are different than seasonality one.
**Random** component is what remains after accounting for the other three components listed above. It’s itself composed of noise with underlying structure that needs to be modelled to forecast future values.

**To model any kind of time-series first of all we need to stationarize it.....**
#### STATIONARY TIME-SERIES
A random variable that is a time series is stationary if its statistical properties are all constant over time. Every time series can be made to be “stationary” by differencing, perhaps in conjunction with non-linear transformations such as logging or deflating. A stationary series has no trend, its variations around its mean have a constant amplitude, and it wiggles in a consistent fashion, i.e., its short-term random time patterns always look the same in a statistical sense. The latter condition means that its autocorrelations (correlations with its own prior deviations from the mean) remain constant over time, or equivalently, that its power spectrum remains constant over time. 
![stationary time-series](https://github.com/Techievena/Retail-Analysis/blob/master/stationary-time-series.jpg)

### THE PROCESS
##### Box-Jenkins methodology:
<ol>
	<li>Condition data and select a model</li>
	<ul>
		<li>Identify and account for any trends or seasonality in the time series</li>
		<li>Examine the remaining time series and determine a suitable model</li>
	</ul>
	<li>Estimate the model parameters.</li>
	<li>Assess the model and return to step 1 if necessary.</li>
</ol>

Now on to data processing .... Our first job will be to complete the empty rows in the dataset and store it in a different file which will be handy for further processing.
**N.B.:- Handling csv files are much faster in R. Even if no processing is required, kindly make it a habit to convert your xlsx file into csv file when handling large datasets**

<pre><code data-trim class="r">
{% raw %}
setwd("~/R/Working Directory/Retail Analysis")
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

😉

## Coloring

You can define the colors that you want in your { Personal } website by setting
the following variable sin the /_sass/_variables.scss file:

<pre><code data-trim class="scss">
// Main color
$primary-color: #000;

// Anchor color
$secondary-color: #00cdff;

// Font color
$font-color: #fff;
</code></pre>

### Emoji support

You can add emojis to your posts by simply typing their [emoji code](http://www.emoji-cheat-sheet.com/) :wink:

<pre><code data-trim class="bash">
cd <your { Personal } repo>
./scripts/newpost hello-world
</code></pre>

<i>italics</i>
