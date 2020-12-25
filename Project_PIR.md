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

Post our initial data observation, we had planned for a workshop with client to go through these details and present them with an update in current progress and set expectations as we move forward. We used secured gateway channel and visual source safe to manage and track code and share information across relevant stakeholders at regular intervals with restricted access to respective teams. Access to visual source safe and secured gateway were restricted to the respective team members and stakeholders that are supposed to view this information. This helped follow an agile process and driving communications in an optimal setup manner.

We have used R and Python to leverage exploratory data analysis, model development and evaluation approaches here. The deliverables were – one to provide the report with exploratory data analysis and second is to provide report with final predictions for insurance renewal and computation of incentives for agents as per our recommendations as part of the solution.

## 3) Solution Development

We started with manipulating some of the features which were needed to prepare our Machine learning dataset as an input to model experiments.
Sourcing channel types were categorical with 5 types and we have encoded them to spread across 5 additional parameters for the dataset – one each for every category. Based on the value one of them will be set to 1 and rest all parameters will be set to 0 for that row.
Amount paid column is added with computation by multiplying “number of premiums paid by user” and the “premium amount”.
Age in days in policy has also been recoded (as one hot encoding) to reflect 1/2/3/4 based on range from 0-10000, 10001-20000 and so on.

Training dataset has been split further into 80% and 20%. Objective was to create a data partition so that we build models using the 80% of the training data and test our model using the remaining 20% to gauge the model performance and feature set considered for the model.

We used multiple experiments to predict renewal since it was a binary classification problem. The key was to perform feature engineering and selecting features based on importance and their influence on target variable.

Regression, Random forest, Decision tree approaches were used. We also used LightGBM which is essentially a fast, distributed high performance light gradient boosting framework based on the simple decision tree approach. Since it is based on decision tree algorithm, it splits the tree leaf wise with the best fit. Therefore, while growing on the same leaf in Light GBM, the leaf-wise algorithm can reduce more loss than the level-wise algorithm and hence results in much better accuracy. Boosting mechanism is automatically used to handle the overfitting of data here as the class was highly imbalanced set.

Feature importance plot is drawn to get an understanding of the feature set for refinement.

![Image28](/images/Image28.png)

AUC score was used to measure the performance. Training of model was iterated until validation scores don’t improve for 200 rounds. Hyper parameter tuning were done based on specific assumptions. (learning rate of 0.02, max depth of 8, max bin size of 100, boosting was performed as per gradient boosting decision tree method). Seed was set to a specific value to compare the AUC scores. Finally getting an AUC of around 0.849 was high-performance model. This was on the training set. The predictions were generated on the test set later. 

![Image29](/images/Image29.png)

Post this differentiation was used to maximize incentives for agents considering given parameters. We have had discussions with key stakeholder from client side to determine the benchmark to be considered while computing the agent incentive.

Finally for each user, renewal probability and incentive amount was computed and provided as the final output. Final output was saved to a csv file and shared with client for their further consumption.

A sample file of prediction file will look as follows. Below is an illustrative and masked data created to give a feel of the output file that was generated.

![Image30](/images/Image30.png)


## 4) Solution Implementation

The model / solution was implemented for the insurer.  They were able to realize value within 3 months of implementing actions based on the predictions shared with them. 
- Client used the prediction probability to take better informed decisions about their end customers – who are more likely to renew the insurance.
- Computing the incentive amount for agents helped them strategize entire process and how to allocate agents accordingly and manage their incentives. Effort towards campaigns were managed better after implementation of the solution. 
- Client wanted to perform this as an ongoing effort (generating prediction monthly for their business) for next few quarters to see the impact and leverage from it.

I had played the lead role in driving the solution which we had developed from end to end perspective. This also has resulted in giving us more work as we were able to influence client to help them in their journey which has started as part of this effort here. Recommending them to look at a solution with continuous prediction had been appreciated as client have seen the impact.

Some of the key lessons learnt as part of this program are as follows:
- Planning and conducting multiple workshops to discuss with client touch points, stakeholders much early and following agile process helped us streamline few aspects. This was a great experience and we wanted to continue this practice for future projects. This need to be defined in the plans clearly.
- Educating various stakeholders about the importance of the methodology and aligning to kind of a CRISP-DM framework helped.
- Adding exploratory data analysis report as a deliverable was key and walking customer in a workshop based on the findings helped in the overall success of the project.

