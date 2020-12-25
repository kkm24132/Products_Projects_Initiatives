## Project Overview - "Clustering Patients for Specialty Pharmacy"

Key Parameters | Description
---------------|------------------
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

We have used R and Python to leverage exploratory data analysis, model development and evaluation approaches here. The deliverables were 
– One to provide the report with descriptive data analysis and 
- Second, is to provide report with final clustering approach and model with our recommendations on way forward.

## 3) Solution Development


