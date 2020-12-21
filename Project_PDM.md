## Project Overview

Key Parameters | Description
---------------|------------------
Project Name   | Predictive Maintenance – Failure Prediction Solution
Client Industry| Banking and Financial Services (BFS)
Nature of project| Revenue Generation and Expense Reduction
Your primary role on the project| Senior Data Scientist

I am involved in all stages of CRISP-DM phases and it is iterative and ongoing for multiple experiments / improvements and enhancements.

## Business Environment

The customer is the largest banking organization in the world in terms of market capitalization, total assets, deposits, loans, number of customers and number of employees. This project was intended for one of their division in Latin America in Argentina.  ATM and branch operations has been a key area of focus for the bank and they wanted to embark on a transformational journey to leverage Data Science and Analytics for better return on investment, optimize their costs, improve customer satisfaction by ensuring increase in availability of install bases.

Customer wanted to implement Predictive Maintenance solution to identify upcoming hardware failures before they arise and prevent them.

Some of the key benefits expected are as follows:
* Reduce service related downtime and increase install base availability
* Reduce service cost through logistics optimization and reduction of reactive tickets
* Increase lifetime of assets, their components for better end-customer satisfaction
* Improve management of failure risk exposure
 
There was no method or system available to optimally predict failure of ATM devices and its components using machine learning by considering multiple algorithm approaches and providing the most effective approach to address the problem. Secondly, manual prediction based on historical data or trend only, leads to inaccurate result, incorrect decisions, thus impacting availability issues of a device and huge loss to firms that impacts “availability of business” and leading to customer dissatisfaction. Thirdly, IT support taskforce of any firm will have multiple levels of support and there is a tremendous need to determine optimal deployment of field engineers to tackle problems related to devices that are installed across various geographies based on effective prediction.

I have been involved as a Senior Data Scientist for more than a year in this offering / program, responsible for delivering solution / predictions in production on a monthly basis for the client. This solution has been in production for multiple quarters. This has been an ongoing journey for our firm where we have multiple teams located across various geographies. My collaboration with data analysts, program managers and all stakeholders have been fundamental throughout the entire life cycle of the program. I have worked closely with team in Europe geography and we as a team have provided solutions which has impacted significant client value. We used to provide our inputs and solution to local teams based out of Argentina from IBM and they used to interact with clients to deliver the solution to them.

## Planning

We followed the CRISP-DM methodology and entire life cycle:

* Business Understanding 
* Data Understanding
* Data Preparation
* Model development
* Model evaluation
* Deployment

From a business objective and understanding standpoint, we analyzed the need and data sources which are available and considered as base – 
- Service Tickets (logged for a problem of a specific component of an ATM device), 
- Event information or Error codes (for a problem against a particular component in the device), 
- Inventory data (ATM Device level information regarding it’s make, model, component list, configuration parameters etc.), 
- Transaction information (number of transactions, type and amount of transactions etc.), 
- Priority usage etc. (Priority based on type of usage for business need) as input and determines likelihood of failure at a device and its component level within a stipulated future time-period with certain accuracy and precision for financial clients.
- TAR Codes (Translation Activity Report) – These are extremely crucial and are part of service tickets which tells about the module or component of the ATM (such as Cash Dispenser, Card Reader, Receipt Printer etc.), the problem determination, the action performed by the service engineer while attempting to serve the ticket.

![Image1](/images/Image1.png)

From data understanding standpoint, exploratory data analysis performed to understand the data sources in particular. We used to get data from client uploaded via EcuRep to IBM secure environment and made available in DB2 database repository.

We used R to write programs to analyze the data sources – primarily service ticket information including TAR codes, asset or inventory information of ATM machines, model, installation date etc. and error code / event codes.

Detailed exploratory analysis performed to understand some aspects such as –
- Total number of service tickets by month and trend
- ATM device count and ticket count by model (WINCOR, NCR etc.)
- Top N problematic ATMs with ticket counts
- Total downtime by failure reason
- TAR code spread by module/ component of ATM devices

![Image2](/images/Image2.png)

We have used dplyr, tidyr, data.table, caret, purr, lubridate, jsonlite, stringr and some other libraries in R to leverage data wrangling, data manipulation, date handling etc capabilities and prepare dataset for the machine learning algorithms.

A method and approach is created to optimally predict failure of devices at a component level (such as Cash Dispenser, Card Reader, Receipt Printer etc.). The system will consider a machine learning approach of algorithm to determine the probability of failure at every
component level:
- based on a fixed time window
- based on dynamic time window

and will provide an optimal prediction output in terms of probability of failure from 0 to 1.

The system can be executed at a monthly level or bimonthly level or weekly level (depending on frequency chosen) to provide predictions for a device and against each
and every component / module as applicable. Based on these predictions, resources or field engineers will be allocated optimally to perform maintenance tasks, they can also be allocated depending on number of preventive tasks required for a region.

![Image3](/images/Image3.png)

As part of initial versions of solution roadmap, various parameters and features are used to come up with the model and the same is deployed in production for clients. (e.g. parameters and input data related to inventory of device/asset, service ticket information, error / event log information, transaction information). In case of conflict, we have used best practices and agreed on experiments based on outcomes.  We used Github significantly to collaborate, maintain and track our code base, data pipeline routines, issues in a structured manner and agile data science was followed. The development environment is where we used to train our models and test various experiments. Post model evaluation, we used to select the best model and use that as a pretrained model to execute for new data for generating predictions.

## Solution Development

The solution that I come up with along with the team is a “predictive engine” that looks at various parameters such as Service Tickets, Event Code / Error Codes relating to a component of the device, Inventory of the device, Installation date, Age of device, Number of Transactions till date for a particular device, Type of transactions performed etc. to provide a quantitative understanding of device health check and accurately provide when the device will break down and more importantly provides an ability to predict component of the device going to fail and underlying causes that may potentially occur in future.

As part of Data preparation approach, which is the most critical aspect of any end to end data science program, below approach was followed.

The data is prepared based on fixed and dynamic time window. The approach takes errors / events as inputs and predicts for a component level failure as target variable. Binary classification is performed on prediction outcome and target variable is either 0 or 1 (either a failure occurs for a device for a component or no failure). For every device, for each component, number of errors are counted for every error code from the last ticket raised for that device and that particular component. This way datasets are stacked up month wise backwards. For fixed time window, the error count is computed considering last 30 days and for dynamic time window, it is the last ticket from which the error counts are computed.

There are three windows – observation window, transition window and predictive window which are defined to prepare features accordingly. For example, we have used predictive window of 4 weeks (around 1 month in future) for generation of prediction, transition period of 1 week to ensure when the predictions are generated every month the
input data received, and actual predictions generated have a gap of few days to factor that delay. The observation window is the past historical data which is a minimum of 9 to 12 months.

The feature engineering process involves the following:
- Errors or event codes are used as features, 
- Every error id would represent a type of problem area, 
- Count of errors are computed for a particular device id, for a specific time window.

Additionally, other features such as age of device (based on purchase date, installation date), make / model of device, no of transactions, count of transactions etc. are also included in entire feature set in addition to these Error / Event features.
There are around 380 features which we have used out of which 360 are Error/Event id related features.
The results evolved as our journey progressed based on multiple experiments. Experiments in machine learning modelling phase involved stepwise evolution of approach (but not limited to what is shown in a diagrammatic fashion in enclosed document).

![Image4](/images/Image4.png)

- First model experiment: All Errors / Events considered as feature set
-	Second model experiment: Errors / Events that are categorized as Warnings are removed from the feature set
-	Third model experiment: Regularization approach applied. RRF model used
-	Fourth model experiment: Less frequent tickets are removed (whose count <= 50), this is to ensure less frequent service tickets are ignored since they do not impact much on overall prediction outcome
-	Fifth model experiment: 1st step - involved all feature set, 2nd step - involved top 30~35 features based on variable importance derived from the RRF

Precision will tell what portion of time we will be correct about our prediction that device x is going to fail during the predictive window. Recall indicates that, out of all devices that are going to fail during the predictive round, what is the portion we will correctly identify. Precision and Recall were used. The cutoff point is computed using Youden J statistic at ATM level.

The confusion matrix around prediction or no prediction will be as follows:


Model Output sample:

The precision and recall chart below is derived after several steps of experiments that are performed and mentioned to refine the performance of the model.  The feature importance graph is derived from the regularized random forest model (for top 30~35 features) based on the Gini coefficient. The chart is shown below for reference.
