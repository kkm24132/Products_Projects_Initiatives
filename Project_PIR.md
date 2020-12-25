## Project Overview - "Predict Insurance Renewal"

Key Parameters | Description
---------------|------------------
Project Name   | Predict Insurance Renewal
Client Industry| BFSI (Insurance)
Nature of project| Revenue Generation and Risk Mitigation
Your primary role on the project| Analytics Lead
Technology area | Data Science, Machine Learning, Classification, Supervised ML

I am involved in all stages of CRISP-DM phases and it is iterative and ongoing for multiple experiments / improvements and enhancements.

## 1) Business Environment

The client is one of the largest insurance service providers in the world. As part of their transformation strategy, they wanted to deal with drivers pertaining to key business areas evolving around customer loyalty, attaining single view of customer, handle regulatory and compliance effectively, manage falling interest rates, tackle with commoditized products, improvise on agent productivity and so on.  They wanted to prioritize on some key initiatives revolving around their customers / end users and hence have partnered with our team to embark on an ambitious journey. They wanted to build a solution which will have the ability to predict the propensity to pay renewal premium and build an incentive plan for its agents. This will maximize the net revenue (i.e. renewals – incentives given to collect renewals) collected from the policies post their issuance.

There was information available about past transactions from the policy holders along with their demographics. The client had provided aggregated historical transactional data like number of premiums delayed by 3/ 6/ 12 months across all the products, number of premiums paid, customer sourcing channel and customer demographics like age, monthly income and area type.

In addition to the information above, we also had the following relationships:
- Expected effort in hours put in by an agent for incentives provided
- Expected increase in chances of renewal, given the effort from the agent

Hence our objectives were 
- To develop an approach and solution to predict the propensity of insurance renewal.
- To be able to create an incentive plan for agents (at policy level) to maximize the net revenues from these policies.

The input data file that were provided had test and train set. Train dataset had the target variable as “renewal” which is a binary parameter having values 0 and 1. (0 – policy not renewed and 1 – policy renewed). After reading the data, we performed exploratory analysis to understand the data better and manipulate wherever needed. Some of the parameters involved age in days of policy holder; no of premiums paid late by 3 to 6 months slab, 6 to 12 months slab and 12+ months slab; percentage of the premium amount paid by cash or credit card; Underwriting Score of the applicant at the time of application (No applications under the score of 90 are insured); Total premiums paid on time till now; Sourcing channel for application; Area type of Residence (Urban/Rural); Monthly premium amount etc.

## 2) Planning

We followed the CRISP-DM methodology and entire life cycle around it. The steps were defined as follows: 
- Business Understanding 
- Data Understanding
- Data Preparation
- Model development
- Model evaluation
- Deployment

I had defined the process steps so that we can address the problem at hand. My responsibilities evolved around entire end to end ownership of driving the solution from an analytics leader perspective. We as a team had explained to client and agreed with all stakeholders on the methodology we proposed and adopted for this solution. We conducted multiple workshops to walk through them about our approach regarding how to go about the solution. 

Some of the key data analysis provided below insights:
- Training data set had highly imbalance dataset for target variable (93%~7% split)
- There were 5 sourcing channels such as A/B/C/D/E and two of them constitute 75% of data.
- Customer residence area type split between rural and urban were at 40% - 60%
- Missing values for some columns  
- Age in days of policy holder spread across which was recoded as a one hot encoding to numeric labels from categorical range segment. 
- Analysing the spread of target variable (which is “renewal” as 0 or 1) with regards to parameters such as – policy age in days category, count all late (3-6 months late, 6-12 months late and 12+ months late cases), residence area by rural/urban, sourcing channels by 5 categories etc.

![Image27](/images/Image27.png)

