# Predicting SyriaTel Customer Churn

## Analysis Overview

This project analyzes data from the telecommunication company SyriaTel, to identify patterns that signal when a customer is likely to cancel their service, or "churn". By leveraging predictive models such as logistic regression or decision trees, the company can proactively intervene with targeted offers or improved services to retain at-risk customers.  

## Business understanding

Preventing customer churn is crucial for telecommunications companies due to its direct impact on profitability. High churn rates reflect customer dissatisfaction, which not only results in lost revenue but also increases the cost associated with acquiring new customers. Getting a new customer can cost five to twenty-five times more than keeping an existing customer.  

Studies have shown that even a small reduction in churn can significantly boost the company's revenue. For example, a 5% reduction in churn can increase profits by 25% to 95% depending on the industry context. This substantial effect arises because retained customers are likely to buy more over time and often cost less to serve due to their familiarity with the service and products.  

Additionally, predictive analytics in churn prevention allows telecom companies to identify at-risk customers early on, enabling them to take targeted actions to retain these customers. This proactive approach not only saves money but also improves customer satisfaction and loyalty by addressing their concerns before they lead to defection.  

<img src="images/image2.png" alt="Alt text" width="800"/>

## Data

Syriatel is a telecommunications provider, offering mobile services like domestic and international voice calls, SMS and voice mail to millions of subscribers. The company employs approximately 3,500 employees and serves 8 million customers as of 2016. It is headquartered on Sehnaya Road in Damascus according to [Wikipedia](https://en.wikipedia.org/wiki/Syriatel)

We used [Churn in Telecom's dataset](https://www.kaggle.com/datasets/becksddf/churn-in-telecoms-dataset). The dataset contains 3333 rows and 21 columns, giving details on customers' state, account length, area code, phone number, plans, and statistics on service usage such as calls, minutes, and charges across different times of the day, international usage, and customer service interactions, along with churn status.

## Target Variable: Churn

Our target valiable is churn, which reflects if a customer terminated contract(1) or did not(0). Target variable is imbalanced, about 15% is class 1 and 85% is class 0. We used SMOTE techniques to balance the data.  

![Class Imbalance](images/class_imbalance)

## EDA

In the process of EDA we explored all features, their distributions and their relationship. 

<img src="images/image8.png" alt="Alt text" width="600"/>

## Models

We used three models - Logistic regression, Decision tree and Random Forest. 

<img src="images/image5.png" alt="Alt text" width="600"/>

After comparing perfomance of all three models, we came to the conclusion that with the selected data set the model for prediciting customer churn would be logistic regression.  

Our **Main Metric** for model evaluation was Recall. It measures the proportion of actual positives (churning customers) correctly identified by the model. High recall is crucial in churn prediction because missing out on identifying a customer who might churn (a false negative) can be costlier than mistakenly identifying a non-churning customer as at risk (a false positive).

## Best Model: Logistic Regression (in need of tuning)

Our best model was Logistic Regression, with higher scores predicting churn compared with Random Forest. Our Decision Tree ROC-AUC curve repeatedly indicated some problems in the model's functionality - we'd need more time to assess whether or not that might be a better option through greater tuning.

Though we spent extensive time and effort honing feature selection, normalization, etc...Our logistic regression scores did not improve over the course of this project. Our main metric, **Recall**, is high enough (0.79) that we can suggest this model as a starting point...but more hyperparameter tuning will need to be done to explore the full potential of this model's strengths when predicting churn.

Furthermore, our Logistic Regression model had an **ROC AUC Score** of 0.84, which is very promising.

<img src="images/image7.png" alt="Alt text" width="700"/>

## Feature Selection and Analysis

Most important features for the model:

<img src="images/image3.png" alt="Alt text" width="700"/>

### Geographic Distribution of Churn-Risk

We further distinguished "higher" and "lower" risk states for churn.

<img src="images/image9.png" alt="Alt text" width="600"/>

## Business Conclusions and Recommendations

We recommend using logistic regression as the main model for this prediction as it showed better performance in comparison to other models (desicion tree and random forest, however we'd need more time for further hyperparameter tuning in order to explore the full potential for model improvement with regards to it's scores. 

After a thorough analysis, finding the best predictive models and identyfing most importan features, we can propose following business resommendations to lower customer churn:

**1. Customer Service Calls**
Based on the analysis indicating that the number of customer service calls is correlated to higher churn rates. Customers who frequently call cutomer service are more likely to churn. There is no enough data to explore why those customers calls were made, what problems they were addressing and what were the outcomes - if their issues were solves or not. 
* We suggest collection and analysis of data on customer service calls (reason for call, type of issue, was the issue resolved, customer service experience satisfaction), so we can have a fuller picture of the existing correlation.


**2. International plan**

Customers with an active international plan are more likely to churn. After investigating, we found out that for a cost per international minute costs the same for people with international plan and without. This is our main assumption how international plan affects churn, other factors might include customers frequently travelling abroad and terminating contract every time, customers moving abroad. In general we advise to reassess and restructure the international plan offerings:  
* **Differentiate the international plan** by offering lower rates per minute or additional benefits such as free international texts or reduced rates for calls to popular destinations. This adds clear value compared to standard rates.
* **Gather feedback** from current international plan users to understand their pain points and expectations, which can help in designing a more attractive plan that addresses their needs. 
* Develop **tailored international plans** that benefit international callers, possibly with tiered pricing based on location to provide more flexibility and cost efficiency, e.g. 30 discounted minutes per month to a country of choice.

**3. Total minutes and total day minutes**

Customers with high total minutes and total day minutes are more likely to churn. Customers are charged per time they spend on a call, it's natural for customer to constantly try to reduce their spending. During our analysis we found out that day minutes cost more, compared to other times: day: 0.17, evening: 0.085, night: 0.045, international: 0.27.
Given that daytime minutes are more expensive and affect churn, we suggest the following recommendations to address potential churn related to this pricing structure:
* Evaluate the feasibility of **reducing the rates for daytime minutes**. This could mitigate the financial burden on customers who primarily use their phones during the day, leading to lower churn rates.
* Introduce more **flexible pricing plans** that allow customers to choose or customize their peak hours according to their usage patterns. This personalization can enhance customer satisfaction and loyalty.


**4. Location**

After analysing churn rates by state we indentified states with very high churn rate. There is no enough data to assume reasons and factors that affect churn rate by location. In this case our recommendations are:
* **Churn rate reasons by state analysis:** Collect additional data (feedback from customers) on reasons for churn distinguished by states.

## Data Limitations
* Data set might be outdated and needs updating
* The dataset lacks qualitative insights, such as customer satisfaction levels or reasons for customer service calls, which could provide deeper context for churn reasons.  

## Next Steps
* Introduce new features for analysis, including data usage and data services
* Include qualitative analysis for a deeper dive into customer feedback
* Invest into feedback collection and analysis from customers who churned

#### Authors: Dolgor Purbueva, Emma Scotson
