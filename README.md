# **Capstone: Regression Modeling: Predictors of School Discipline Incidents Across Illinois Schools**
## **Debbie Sim**
---

## Repo Folder Organization
---
|Folder|Type|Description|
|---|---|---|
|README.md|README|README file for Capstone|
|cleaned_datasets|folder|contains the cleaned datasets post data cleaning, post pre-processing, & for modeling|
|datasets|folder|contains raw datasets|
|pickles|folder|pickles of models ran during project| 
|plots|folder|exported graphs from jupyter lab as png files|
|resources|folder|contains resources related to capstone topic|
|01_Capstone_Data Cleaning-0|jupyter notebook|contains jupyter lab notebook with code for data cleaning part I|
|01_Capstone_Data Cleaning-1|jupyter notebook|contains jupyter lab notebook with data cleaning part II|
|02_Capstone_Model 1-Pre-Processing & Feature Engineeering|jupyter notebook|contains jupyter lab notebook with pre-processing of data for model 1|
|03_Capstone_Model 2 - Pre-Processing & Feature Engineering|jupyter notebook|contains jupyter lab notebook with sentiment analysis scores & exploration pre-processing and feature engineering for model 2|
|04_Capstone_EDA & Data Viz|jupyter notebook|contains jupyter lab notebook with EDA & data visualization plots|
|05_Capstone_Modeling|jupyter notebook|contains jupyter lab notebook with modeling & evaluation|
|Debbie Sim_Capstone_Regression Modeling: Predictors of School Discipline Incidents Across Illinois Schools|pdf|Capstone slides presentation|


## Problem Statement
---
In the state of Illinois, there have been requests from local educators requesting the Illinois State Board of Education to change the allocation of Title IV funds to effectively support the implementation of the new suspension and expulsion policy that was passed Funds have typically been allocated based on Title I status, but the board of education wonders if there are other characteristics to consider. **Using a regression model, can we determine which characteristics of a school are most predictive of suspension and expulsions in Illinois schools?**

## Data & Data Dictionary
---
The data was wrangled from two main sources: IL State Board of Education data portal and the National Center for Education Statistics. The data includes a variety of characteristics of schools including demographic and academic performance, funding data, district characteristics, and other indicators such as Title I status and summative designation. Data was extracted for 2017-2018, 2018-2019, and 2019-2020 school years. 

There are datasets included in the [`datasets`](./datasets/) 

* [`18-20-eoy-student-discipline.xlsx`](../Capstone/datasets/18-20-eoy-student-discipline.xlsx): *Links* ([*source*](https://www.isbe.net/Pages/Expulsions-Suspensions-and-Truants-by-District.aspx))([*dictionary*](https://www.isbe.net/Documents/ISBE-Discipline-Business-Rules-SY2022.pdf))
* [`18-20-Report-Card-Public-Data-Set.xlsx`](../Capstone/datasets/18-20-Report-Card-Public-Data-Set.xlsx): *Links* ([*source*](https://www.isbe.net/Pages/Illinois-State-Report-Card-Data.aspx))([*dictionary*](https://www.isbe.net/Documents/2022-Glossary-of-Terms.pdf))
* [`18-20-Public_School_Characteristics.xlsx`](../Capstone/datasets/18-20-Public_School_Characteristics.xlsx): *Links* ([*source*](https://data-nces.opendata.arcgis.com/datasets/nces::public-school-characteristics-2017-18/about)([*dictionary*](https://data-nces.opendata.arcgis.com/datasets/nces::public-school-characteristics-2017-18/about))
* [`18-21-Financial.xlsx`](../Capstone/datasets/18-21-Financial.xlsx): *Links* ([*source*](https://www.isbe.net/Pages/Illinois-State-Report-Card-Data.aspx))([*dictionary*](https://www.isbe.net/Documents/2022-Glossary-of-Terms.pdf))
* [`EDGE-18-20-Poverty-Data.xlsx`](../Capstone/datasets/EDGE-18-20-Poverty-Data.xlsx): *Links* ([*source*](https://nces.ed.gov/programs/edge/Economic/NeighborhoodPoverty))([*dictionary*](https://nces.ed.gov/programs/edge/docs/EDGE_SIDE_PUBSCH_FILEDOC.pdf))

## Background Information
---
- The school-to-prison pipeline is the behavior of funneling students out of schools and into the juvenile justice system mainly due to harsh, zero-tolerance discipline policies. 
- Addressing the school-to-prison pipeline is one of the key issue areas for the ACLU due to this disproportionately impacting students of color across the country
- To address this issue at state-level, the Illinois State legislature passed a bill in 2015 called the SB100 bill which changed the ways schools and districts are allowed to suspend and expel students. At the time it was passed, the bill was considered one of the more far-reaching reform efforts at the state-level to address the issue
- In Illinois, based on a report by the UCLA Civil Rights Project, Illinois reported the highest suspension rate of 25% for African-American public school students during the 2009-2010 school year. This was the highest rate among the 47 states included in the research.

## Modeling
---
For this project, I ran and evaluated two different datasets with slightly different features and target. For both datasets, I tested several different regression models including, but not limited to linear regression, elastic net, random forest, XGBoost, KNN, and ExtraTrees. To parameter tune models, I utilized GridSearchCV and BayesSearchCV. Across both models, the XGBoost was the best model based on RMSE and r2 metrics.
- Model 1 (Target: volume of discipline incidents) - The XGBoost model had a cross validated score of 0.55 and rmse of 71 which is better than the baseline model
- Model 2 (Target: discipline incidents per pupil) - The XGBoost model had a cross validated score of 0.33 and rmse of .15 which is better than the baseline model

## Conclusions & Recommendations
---
Through exploratory data analysis and modeling I was able to surface trends in the expulsion and suspension discipline data. In general we are seeing a decline in suspension and expulsions across the state across the 2018-2020 school years. One interesting highlight is that the percent of expulsions without services is decreasing YoY which is a positive trend. Despite suspensions and expulsions being on the decline, the breakdown by race is fairly consistent YoY. In alignment with research that is already out there, Black and African-American students continue to represent the largest proportion of discipline incidents in Illinois. 

By looking at permutation feature importances, the four features with the highest permutation feature importance were student attendance rate, per pupil spending, % enrollment of Black or African-American students, and % math proficiency of students identifying as low-income. Attendance rate and low-income math proficiency rates also had the highest negative correlation to to incidents per pupil. 

After analysis and modeling, one recommendation I have is for ISBE to investigate further discipline behavior in public charter schools to address continuing inequitable discipline practices that may be present. Furthermore, I believe there’s a need for additional modeling to see if a better-performing model can be built to confirm school characteristics that are stronger predictors of student discipline incidents per pupil. More specifically, I suggest obtaining more data and at a more granular level if possible. In terms of modeling, I suggest additional feature engineering & feature selection and test additional models such as a neural net.

## Resources
---
- *FROM ZERO TO SB100:Teachers’ Views on Implementation of School Discipline Reform'* ([*source*](https://teachplus.org/wp-content/uploads/files/publication/pdf/from_zero_to_sb100-_teachers_views_on_implementation_of_school_discipline_reform_final.pdf))
- *Opportunities Suspended: The Disparate Impact of Disciplinary Exclusion from School'* ([*source*](https://civilrightsproject.ucla.edu/resources/projects/center-for-civil-rights-remedies/school-to-prison-folder/federal-reports/upcoming-ccrr-research))
- *'School-to-Prison Pipeline'* ([*source*](https://www.aclu.org/issues/juvenile-justice/juvenile-justice-school-prison-pipeline))
- *Criminalizing Illinois students flouts law to reduce school-to-prison pipeline'* ([*source*](https://www.reuters.com/legal/government/criminalizing-illinois-students-flouts-law-reduce-school-to-prison-pipeline-2022-05-09/))