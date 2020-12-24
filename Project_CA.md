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

