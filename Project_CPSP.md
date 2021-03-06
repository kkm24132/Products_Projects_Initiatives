## Project Overview - "Clustering Patients for Specialty Pharmacy"

Key Parameters | Description
:--            |:--
Project Name   | Clustering Patients for Specialty Pharmacy
Client Industry| Healthcare
Nature of project| Revenue Generation
Your primary role on the project| Analytics Track Lead
Technology area | Data Science, Machine Learning, Clustering, Unsupervised ML

I am involved in all stages of CRISP-DM phases and it is iterative and ongoing for multiple experiments / improvements and enhancements.

## 1) Business Environment

The client is one of the largest biotechnology firms in the world specializing in drugs for neurological disorders, autoimmune disorders and various other diseases. The firm has been focusing on various products, key therapies and have been constantly transforming their business to optimize interaction channels with patients, prescribers etc and to offer them appropriate products and services based on their need and applicability. 

As part of their data transformation strategy and journey to data driven decision making, they wanted to get more insights on trends in barriers to getting patients on therapy, look at their products and how are these products being used by patients. Patients are willing to move up their regularly scheduled appointment for specific products, even if their treatment centers are far away because they want to switch to a product sooner.  There is a need to understand specialty pharmacy patient mix by different parameters and demographics and improve overall patient experience. To accomplish that, clustering of patients was performed to group them to identify similar group of patients having similar characteristics.  Based on the group of similar patients, specific product usage can be offered. Identifying similar patients based on their attributes to explore costs, treatments or outcomes will need them to be grouped / categorized accordingly.

We have had multiple rounds of conversations and meetings with client stakeholders to draft and agree on some key objectives –
- To provide an ability to view patient services metrics
- To provide an ability to view weekly patient update based on specific product
- To understand prescriber uptake
- To cluster group of patients with similar characteristics shown to be able to offer specific products and services to those set of patients or group of patients

## 2) Planning

We followed the CRISP-DM methodology and entire life cycle around it. The steps were defined as follows: 
- Business Understanding 
- Data Understanding
- Data Preparation
- Model development
- Model evaluation
- Deployment

I had defined the process steps so that we can address the problem at hand. My responsibilities evolved around entire end to end ownership of driving the solution from analytics lead perspective. I had to work with the business analyst in the team who was an expert in specialty pharmacy and that helped me in getting up to speed and understanding the context as it was more domain intensive. We as a team had explained to client and agreed with all stakeholders on the methodology we proposed and adopted for this solution. We conducted multiple workshops to walk through them about our approach regarding how to go about the solution. 

We prioritized the top product which needs to be analyzed as a first step as per agreement with client and performed analyzing weekly patient update for that product. This includes existing patient metrics (based on patient stages such as “graduations”, “enrollments”, “never starts”, “discontinued ones” etc.) and projected active patients by week for the product. Below figure gives a snapshot view of that analysis.

![Image25](/images/Image25.png)

We also defined various key parameters as KPIs so that patient mix can be analyzed based on those attributes on a weekly basis. Some of them included – patient type by regimen (at prophy stage, at intermittent prophy stage, on demand by patient etc), patient type by age (paediatric and adults), patients by unique dose (IUs per kg and also by dosing frequency) etc.

![Image26](/images/Image26.png)

We analyzed the patient services metrics such as patients enrolled by a program, total calls received from patients as enquiry for the product on a weekly basis, calls by topic (whether it is about product or services or free drugs or copay related enquiries etc.)

We looked at patient cycle time as to how long have pending patients been sitting there and how many are likely to become never starts. This has provided a view on patient onboarding efficiency by week based on past historical data that was available for analysis.

From prescriber point of view, we wanted to analyze top N prescribers, new prescribers that are coming into the picture, discontinued prescribers etc. This is important in dealing with specialty pharmacy products as prescribers play crucial role in influencing patients and in most cases, patients will have to go through prescribers to be able to get into these products and services. Some of the attributes that are used for analysis included: HCP (Health Care Provider) name, territory or province or region, any affiliation to a product specific healthcare provider or not, current product specific patient usage, enrollments by week by those patients, graduations by week by those patients for the product etc.

We used secured gateway channel and visual source safe to collaborate documents, code and share information across relevant stakeholders at regular intervals with restricted access to respective teams. Access to visual source safe and secured gateway were restricted to the respective team members and stakeholders that are supposed to view this information. We also had regular weekly touch points with client SPOC to be able to review progress considering very tight timelines. 

We have used R and Python to leverage exploratory data analysis, model development and evaluation approaches here. The deliverables were:
- First, to provide the report with descriptive data analysis and 
- Second, is to provide report with final clustering approach and model with our recommendations on way forward.

## 3) Solution Development

Post our exploratory analysis on finding out various metrics, we went on to focus on the clustering approach. We tried K-means clustering to help us better characterize the subpopulation since the dataset was large and hierarchical clustering would not have been appropriate in the case.

Our approach involves –
- Formulating the problem and selecting the variables that we wish to use as the basis for clustering analysis
- Computing distance between patients along the selected variables
- Applying the clustering procedure to the distance measures
- Deciding on the number of clusters
- Mapping and interpreting the results 

We looked at various variables – patient id, patient age, sex, patient type (by regimen), unique dose, dosing frequency, territory, Type of syndrome (severity / type of disease), awareness of disease (well aware, average aware, not aware at all), part of a product treatment center or not etc. We transformed some categorical variables such as patient type to numerical values such as Prophy regimen – 1, On demand – 2 and Intermittent Prophy regimen – 3.  Patient age is also bucketed into two categories of paediatrics and adult based on whether they are above or below 18 yrs of age. Dosing frequency was also categorical, and we transformed that as well.  

Post that, we have standardized variables by using formula [{value – mean(value)} / standard_deviation(value)] and tried to use Euclidean distance to get the distance matrix between patient ids along these variables. Since there were categorical data, we used jacquard’s distance method to get distances of binary data values.

In addition to Euclidean distance with standardization, we also tried other method of Gower’s distance (Gower’s dissimilarity coefficient) since there are combinations of numerical and categorical data used.

We plotted “elbow criterion” to determine the cluster value. The k-value or the cluster value we got was 3 and proceeded with 3 clusters. Some common methods that we used to obtain stability of results obtained using K-mean clustering was as follows:
- Running the algorithm multiple time with different starting values. When using random starting points, running the algorithm multiple times will ensure a different starting point each time and model would be robust.
- Splitting data into two random parts and running the cluster analysis separately with k value in both scenarios. For us, size of different clusters obtained in each cases seem to be closer / quite similar to each other and hence that proved robustness.
- We tried running the silhouette score to see if number of optimal clusters are same after dividing into two halves of entire dataset. Somehow within 3 clusters, objects were matched with higher silhouette score of closer to 0.9 which indicated they are well matched to their own clusters and poorly matched to the neighbour clusters.

Then we profiled patients with specific interpretations on the 3 clusters that were created and provided as an outcome as part of the model solution. 

Some of key recommendations that we have were –
- Clustering indicated that adult patients look for details around dosing usage and frequency in the second visit.
- Dosing of most specialty pharmacy products / drugs are occurring on second visit of a patient, which may be several months after the first visit. There is an opportunity to make dosing happen on the first visit itself with additional coaching of both physicians and patients.
- Physicians have a misconception about inhibitor rates of some products, correcting this assumption could lead to much higher rates of enrollment. Increase in enrollments will help increase product usage and direct impact on revenue.

## 4) Solution Implementation

The model / solution was implemented for the firm.  They were able to realize value within few months of implementing actions based on the recommendations shared with them. Additionally, the descriptive statistics that were created as part of analysis helped them a lot in their operational and tactical decision making. This gave them key indicator about what patient types are influencing which products and they were able to act accordingly.

I had played the lead role in driving the solution which we had developed from a holistic approach perspective. This also has resulted in giving us more work as we were able to influence client to help them in their journey which has started as part of this effort here. 

Some of the key lessons learnt as part of this program are as follows:
- Planning and conducting multiple workshops to discuss with client touch points, stakeholders much early and following agile process helped us streamline few aspects. This was a great experience and we wanted to continue this practice for future projects. This has to be defined in the plans clearly and early in the engagement.
- Explaining them about the solution with domain aspect has helped them a lot since this is a very focused area within pharmaceutical category. This type of products / drugs is sold based on referrals, prescriber inputs and very limited manufacturers who produce these products. Hence patient clustering and providing insight on some key metrics help take firm data driven decisions by coordinating with players within the ecosystem.
- Educating stakeholders about the importance of the methodology and aligning to CRISP-DM framework has helped significantly in the overall journey.
- From a planning perspective, considering inclusion of vacation time upfront would have helped better and we could have managed that better from the start of the engagement.

