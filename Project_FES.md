## Project Overview - "Forecasting Equipment Sales"

Key Parameters | Description
---------------|------------------
Project Name   | Forecasting Equipment Sales
Client Industry| Manufacturing
Nature of project| Revenue Generation
Your primary role on the project| Analytics/Data Science Lead
Technology area | Data Science, Machine Learning, Deep Learning

I am involved in all stages of CRISP-DM phases and it is iterative and ongoing for multiple experiments / improvements and enhancements.

## 1)Business Environment

The client is one of the largest manufacturing firm in the world, focusing around manufacturing in agriculture, and forestry machinery used in heavy equipment spread across multiple geographies. This project was catering to a specific unit and its geography. The firm had shown consistent growth in its revenue from its machinery sales since its inception. Over the years, the firm had struggled to keep its inventory and production cost down because of variability in sales and machinery demand. 

The management of the firm had been under tremendous pressure from the shareholders and board to reduce the production cost. They wanted to see how a solution can be put in place with forecasting abilities for a longer duration (say next 3 years in advance) so that they can plan their decision in advance. Additionally, they were also interested in understanding the impact of analytics and digital transformation towards overall sales. In view of this, they have requested us to help in their data science and analytics journey.

Our objectives were 
-	To develop an approach and solution to forecast sales / demand of their machinery equipment for next 3 years.
-	To be able to provide clarity with exploratory data analysis to understand what is happening.

As a part of this project, we have proposed the client to start this transformation program for one of their key production unit which they prioritized considering their business impact, end user value creation and geographical importance. One of the unit that we were analyzing was completely independent and caters to neighbouring geographies. In 2014, they captured 10%+ of the market share, a 12%~15% increase from the previous year. However, being a new unit, they have very little bargaining power with their suppliers to implement Just-in-Time manufacturing principles that had worked well in firm’s base location. Hence, they wanted to be on top of their production planning to maintain healthy business margins. Monthly sales forecast was the first step we had suggested to this unit towards effective inventory management.

The MIS team shared the month wise sales figures (number of equipment sold) for the last 10+ years in input data file.

## 2)Planning

We followed the CRISP-DM methodology and entire life cycle around it. Since it was a forecasting type of a problem, we went into details and defined it very specific to forecasting process (which is elaborated in Figure 1). It was aligned with primary CRISP-DM steps which are as follows: 
-	Business Understanding 
-	Data Understanding
-	Data Preparation
-	Model development
-	Model evaluation
-	Deployment

I had defined the process steps so that we can address the problem at hand. My responsibilities evolved around entire end to end ownership of driving the solution from an analytics leader perspective. We as a team had explained to client and also agreed with all stakeholders on the methodology we proposed and adopted for this solution. We conducted multiple workshops to walk through them about our approach regarding how to go about the solution. The process for the forecasting was considered in a structured approach as follows:

![Image7](/images/Image7.png)

-	Defining the goal – is the goal descriptive (time series analysis) or predictive (time series forecasting) or a combination of both, what is the forecasting horizon (i.e. how far into the future), how will the forecasting be used (i.e. who will be the stakeholders / personas etc., numerical or event forecast), forecasting expertise and automation (i.e. in-house forecasting or automation expected, how many series, how often, data and software availability etc.)
-	Data collection – data quality is important (data should be same as series to be forecasted), temporal frequency (balance between signal and noise), series granularity (i.e. coverage of the data, should be aligned with the goal) 
-	Explore and visualize series – components (systematic and non-systematic part)
-	Pre-process data (as needed – if there are missing values, unequally spaced series, extreme values, time series – like how far back to be defined and considered concrete)
-	Apply forecasting methods
-	Evaluate and compare performance
-	Implement forecasts

An illustrative snapshot of how equipment sales moved over a period of few years is captured in the figure below.

![Image8](/images/Image8.png)

As part of time series decomposition of the data, we had analyzed to understand systematic and non-systematic part. This covers the trend, seasonality, remainder patterns of equipment sales. There was clearly an increasing trend with some seasonal variations. We have checked stationarity of the data using rolling statistics and dicky-fuller test. We also wanted to test with KPSS test and ensure we observe the differencing stationary and trend stationary. As part of null hypothesis, we looked at dicky-fuller test to look at whether the process has a unit root (difference stationary) and we looked at KPSS test to look at whether the process is trend stationary.

While looking at month wise moving average, we observed that 12-month moving average produced a wrinkle free curve with amount of smoothness as expected. This is noticeable as we are looking at month wise distribution of sales data and there is monthly seasonal effect. 

![Image9](/images/Image9.png)

As a next step we had plotted rolling mean and standard deviation for a month of 12 month window. Though the variation in standard deviation was relatively small, rolling mean was clearly increasing with time and this was not a stationary series. Also, the test statistic is way more than the critical values when we looked at the dicky fuller statistics.

![Image10](/images/Image10.png)

As part of next step, we have analyzed to see if number of equipment sold vary on a month to month basis. We have used stacked annual plotting to observe the seasonality. Some data explorations demonstrated below facts:
-	Sales have been increasing on a regular basis
-	July and August are peak months where sales have been higher. Mean and Variance in these months are also higher than other months relatively.
-	We can observe a seasonal cycle of twelve months where the mean value of each month starts with an increasing trend in the beginning of the year and drops down towards the end of the year. We can notice this seasonal effect with a cycle of twelve months.

![Image11](/images/Image11.png)

Post our initial data observation, we had planned for a workshop with client to go through these details and present them with an update in current progress and set expectations as we move forward. We used GitHub, slack channel to share information across relevant stakeholders at regular intervals. Access to GitHub and slack channel were restricted to the respective team members and stakeholders that are supposed to view this information. This helped follow an agile data science program and driving communications in an optimal setup manner.

We have used R and Python to leverage exploratory data analysis efforts here. The deliverables were – one to provide report with exploratory data analysis and second is to provide report with final forecasted output sales numbers with a confidence interval and provide our recommendations as part of the solution.

## 3)Solution Development

To decipher underlying patterns in equipment sales, we have proposed to build a multiplicative time series decomposition model with equation such as:

Y(t) = Trend(t) * Seasonality(t) * Remainder(t)

However, these are plain vanilla decomposition models which provided an understanding of underlying patterns in temporal data to use in more sophisticated experiments which we had performed later such as Holt-Winters seasonal method or ARIMA etc.

![Image12](/images/Image12.png)

Key observations from multiplicative model provided insights into various aspects such as a) Trends: Twelve-months moving average looks quite like a straight line hence we could have easily used linear regression to estimate the trend in this data; b) Seasonality: Seasonal plot displays a consistent month-on-month pattern. The monthly seasonal components are average values for a month after removal of trend; c) Remainder portion: is the residual left in the series after removal of trend and seasonal components. It looked like a noise which was like no pattern at all. However overall series residual show pattern with high variation at certain years.

We decided to move on to ARIMA model where we can get an idea of estimates of p, d, q (which is nothing but the autoregression part, differencing part and moving average part).
We wanted to make the data stationary (differenced data to make data stationary on mean). This is as per figure below.

![Image13](/images/Image13.png)

Above figure is the differenced sales analysis.

Then we did try to make stationary on mean and variance both by computing log transformations. This is shown in Figure below.

![Image14](/images/Image14.png)

We experimented to plot ACF (Auto correlation factor) and PACF (Partial auto correlation factor) plots to see the following in figure 9. Initial observations with the experiment indicated that there are some observations which are outside of the upper and lower limits. Objective is to refine the model to have residuals are within the lower and upper limits as per ACF and PACF plots.

![Image15](/images/Image15.png)



## 4)Solution Implementation

