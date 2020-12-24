## Project Overview - "Customer Analytics Solution"

Key Parameters | Description
---------------|------------------
Project Name   | Customer Analytics Solution
Client Industry| Banking (BFSI)
Nature of project| Revenue Generation
Your primary role on the project| Senior Technical Manager
Technology area | Data Science, Machine Learning, Classification

I am involved in all stages of CRISP-DM phases and it is iterative and ongoing for multiple experiments / improvements and enhancements.

## 1) Business Environment

This program was to implement customer analytics solution for one of leading global financial services firm in the world. Consumer Banking, which is one of the largest divisions in the firm, provides financial services to consumers and small businesses including, banking, investments and lending products including business loans, mortgages, and credit cards. The financial major was facing challenges profiling their customers that are vulnerable to churn and devising retention strategy to those customers for retention. i.e.
- Ability to offer personalized product and services to customers to improve customer satisfaction and brand value
- Identify loyal customers and target specific promotions to retain them
- Reduce customer churn and thus manage risk

I have been involved as an analytics track lead for entire duration of the program. This was part of a solution that was built on top of the universal banking solution of the firm that was already implemented at customer environment and focus was to develop analytics layer from customer analytics perspective. I had to collaborate across multiple teams located across various geographies. My collaboration with programmer analysts, business analysts and all stakeholders have been fundamental throughout the entire life cycle of the program. I have worked closely with the global team and we as a team have provided solutions which has impacted significant client value and benefits. We did multiple workshops with customer subject matter experts, stakeholders to agree on specific scope from the broad roadmap they had as part of their larger strategy and mission.

The roadmap as part of broader engagement was defined to move from a customer acquisition scenario to customer development and then to customer retention phase. An illustrative snapshot of this is shown in the figure below.

![Image20](/images/Image20.png)

Input data sources were – Core banking system, CRM system, e-Banking system.

Some of the key KPI themes that were defined are as follows (as part of broader roadmap):
- Campaign Performance – To analyze campaign activities based on the customers/opportunities created and converted, responses received etc.
- Customer Life Time Value and profitability – Identify customers and products that bring more revenue to the firm. Also to analyze how long customers are with the bank.
- Attrition and Loyalty – To identify customer level attrition. This will help in analysing attrition trends and risks with attrition.
- Cross-sell and product holding - To analyse and identify the product holding status of the customer, predict next best product that suits the customer and sell new products to them. 
- Transaction behaviour analysis - To generate and analyse recency, frequency and monetary value of the customer transaction and also analyse transaction behaviour.
- Service request analysis - To identify customers and products with high volume of complaints. To analyze service competency of the bank in terms of SLA and TAT management. 

Scope – There was complexity involved here since we have to look at larger roadmap, align to vision and then discuss with customer to agree to specific scope. The agreed scope and focus were to segment customers, look at their retention rate, perform life time value analysis and primarily predict if they are going to churn or not. Based on the information, the firm will take plan of action to tackle their customers who are at a high profitable band and would like to move out, formulate retain strategies for key customers and to propose personalized offers for them. There has been challenge in terms of complexity and various industry parameters with considerations from core banking, CRM and e-banking systems. We defined approach to drive the entire transformation in a step wise manner by looking into the scope, sub-setting into smaller tasks, templates for data attributes that are needed for analysis to solve the primary goal.

## 2) Planning

We have understood the broader holistic roadmap of customer from their strategy and vision perspective which is already captured in “business environment” section above. The objectives based on the scope have been outlined in business terms in above section as well, mentioning key scope that we have arrived at after discussing with customer through multiple sessions. We have emphasized stakeholders about the data quality, availability of data from input sources and importance of the same for success of the project. 

We discussed with customer and explained them our approach of following a methodology like the CRISP-DM and entire life cycle in a step wise manner as follows:
- Business Understanding 
- Data Understanding
- Data Preparation
- Model development
- Model evaluation
- Deployment

Key responsibilities included - converting business problem into data requirements and KPIs to be developed, formulating strategy for activities as per steps in CRISP-DM methodology, exploratory data analysis, data preparation, model development, model evaluation, review within team and outcome presentation.

As the lead, I guided team to follow objectives, phase wise milestones/goals that we have understood and defined for ourselves, we referred to best practices as per our need, collaborated with SMEs from application teams who provided inputs on various parameters across different sources, data team aggregated data from various sources to consolidate in a database for us to consider and analyze on. For us, it was mostly structured datasets as they are in relational database tables.

We performed missing value analysis, checking for any duplicates, one hot encoding wherever needed for categorical variables in the data. Then, we checked correlation between variables to see if we need to keep or remove any variables. We plotted bar charts for categorical variables against the target variable which is the “churn” variable. We performed bar charts as we wanted to see if variables seem to possess reasonably broad distribution. All variables had that and we kept them for further analysis.

Some of the exploratory data analysis that were used are as follows:
- Number of products hold by customers 
- New account by product type (products are typically – loans, cash credit, current accounts, savings accounts, wealth management – structured products etc.)
- Account attrition by product
- Profitability distribution by time and product
- Write off distribution by time and product

![Image21](/images/Image21.png)

Above are illustrative data just to show an idea of the exploratory data analysis performed in most cases.

We have used R to leverage data analysis efforts.
As part of data preparation process, key historical data aggregated:  
- Customer demographics information (e.g. Age, Income, Region)
- Transactional information, Vintage data and RFM scores (e.g. number of transactions, transaction value, Age on book), Recency is based on when customer has started using the product, Frequency is based on number of transactions on product type, Monetary value is based on the average transaction value for the product. While lower recency score is better, higher Frequency and Monetary scores are desirable
- Product holding information (# of active accounts, # of loans, # of credit cards etc.),
- Delinquency data (# of days delinquent, amount delinquent), etc. 
- Relationship size (Tenure from a category – 0-12 months, 12-36 months and so on) and few others

To identify loyal customers from the customer pool, customers with higher age on book and better profitability has been identified. Tenure categories were defined like 0-12 months, 12-36 months etc.

![Image22](/images/Image22.png)

In order to prepare data for feature engineering, we prepared data looking at cohort time windows i.e. historical data window (Cohort month to prior 12 months) and performance data window (Cohort month to post 12 months) have been considered. We checked and cleaned missing data if any based on every customer ids. Any duplicate data also has been removed. Cohort month wise time intervals considered and analyzed. This indicates product holding pattern of the customer over a period of time. We have added new variables such as “IsActiveCustomer” based on this input to our overall feature set.

For example, a user/customer who is using a particular product such as Term Deposit Account, Current Account, Savings Account, Structured Product, Mutual Fund etc. over a period of time can be analyzed to see the life time of that product type over a period of time by the user/customer.  We have used heat maps to get visualization of retention rate over a period of time to indicate whether user/customer is active or not. The retention rate indicates percentage of active users compared to total number of users available. 

To get the attrition probability of the customer, significant factors causing attrition has been found out. Scoring mechanism done to generate a threshold of attrition rate.

![Image23](/images/Image23.png)

## 3) Solution Development

Data Science Structure of the solution – CRISP-DM methodology was used as described earlier. The overall journey and roadmap strategy was to move from customer acquisition to customer development to customer retention. The scope for this project was to segment customers, look at their retention rate, perform life time value analysis and predict if they are going to churn or not. Based on this, the firm would like to take plan of action to tackle customers who are at a high profitable band and would like to churn, and to propose personalized offers for them as a retention strategy. There has been challenge in terms of complexity and various industry parameters. We defined to drive the entire transformation in a step wise manner by looking into the scope which is outlined above.

Data analysis approaches – We performed missing value analysis, checking for any duplicates, one hot encoding wherever needed for categorical variables in the data. Then, we checked correlation between variables to see if we need to keep or remove any variables. We plotted bar charts for categorical variables against the target variable which is “churn” variable. We performed bar charts as we wanted to see if variables seem to posses reasonably broad distribution. All variables had that and we kept them for further analysis.

We used multiple experiments using supervised machine learning - logistic regression, decision tree and random forest algorithms. Rationale of experimenting with these was due to the type of problem of churn / no churn that we are trying to solve this, which is kind of a binary classification problem. Also, to start with something like logistic regression will give us information on how various variables / features have impact on “target” variable and so on. Then we thought of moving to tree-based model like decision tree and random forest.

Logistic regression: We have splitted data into train and test set with 70%-30% split. We tried fitting the model. Top relevant features were noted. We analyzed the deviance table, assessed predictive ability of the model by using ROC / AUC, confusion matrix. Then precision, recall rates were computed. 

Then we tried running simple decision tree and then moved on to run the Random Forest model. AUC plotted and confusion matrix computed.

Random Forest: We have used same split ratio of train and test dataset of 70%-30%. We tried finding error rates – which is higher for “churn cases” and lower for “no churn cases”. We looked at mean decrease gini to look at features of importance. AUC is drawn which is better than other models. Precision, recall rates were computed.

Some of the interpretations that we were able to analyze – 
- Customers with shorter tenure (0-12 months, and to some extent 12-36 months) are expected to churn more compared to those which have stayed with long term relationship with the bank.
- No matter whatever is the Age and Gender churn may happen. So, Age and Gender have limited impact on target variable.
- Customers owning more number of products (# of product holding pattern) have less churn rates. E.g. those who have savings account, current account, term deposit account and mutual funds tend to stay longer and may not churn.
- From a product type standpoint, those customers having loan accounts or structured products have less churn rates.

Model evaluation has been performed using K-S Lift charts, ROC curve, AUC. Accuracy of 83% was achieved. Precision gave us how many instances we were able to predict actual churn cases correctly and Recall gave us how many instances we were able to predict non churn cases accurately. Both were important and hence F1 score was computed for every experiment and basis that, model was considered.

![Image24](/images/Image24.png)

From a deployment perspective, we have generated the model predictions and provided probability of churn by customer id as a spreadsheet to customer. This is a one time activity. Recommendation was to execute this, on a monthly basis to generate predictions based on new data / updated data.


## 4) Solution Implementation

Yes the solution was implemented. My role was to lead the analytics track for entire duration of the program. This was part of an analytics solution that was built on top of the universal banking application of the firm that was already implemented at customer environment and focus was to develop analytics layer from customer analytics perspective. I had to collaborate across multiple teams located across various geographies. My collaboration with programmer analysts, business analysts and all stakeholders have been fundamental throughout the entire life cycle of the program. I have worked closely with the global team and we as a team have provided solutions which has impacted significant client value and benefits. The project was a success as the solution has met intended objectives that was laid down at the start of the engagement. The model and solution that was used for the financial client and has a strong proven success story. Key business outcomes accomplished are as follows:
- Reducing churn rates by approximately 8%~10% and amplifying service offerings.
- Anticipating and managing risks associated with customer churn better.
- Key segments of high net worth customers were offered with personalized product / service offerings

