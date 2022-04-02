# Inspiration
During my stay in Banglore while pursuing a Data Science course, I came across usage of app like 'SIMPL' and 'LazyPay' where Credits are given without any proper verification. Therefore I wanted to dive deeper into such usecases. But the problem associated with this problem was finding a dataset representing the scenario. With further research I found 'Taiwan Bank Credit Card Dataset' from UCI repository where a customer paying habits are observed for six months before considering him/her as default.
# Insights from Exploratory Data Analysis
  
  * Around 24% of male customers and around 20.8% of female customers are defaulting, which suggests a customer being a male has more likelihood to default.
  * Customers having 'High-School' as highest education have high probability of defaulting next month.
  * Customers from "Younger Age" group are making more default than "Older Age" group which can be indication of stable income for later.
  * Various customers are assigned different Limit Balance i.e. 'LIMIT_BAL in our dataset according to analysis done before. It was found that customers with lower      'LIMIT_BAL' are more probable of defaulting.
  * All of the above conclusions are tested Statistically using ttest for independence and chi-square test for independence depending upon the datatype we are tring to find independence of.
  ![image](https://user-images.githubusercontent.com/102746816/161371196-ab84277f-3d33-49f8-9140-f814040c6c38.png)
  * Most of the customers are paying the partial bill amount and duly paying. And when payment is delayed more than 2 months, the chances of default goes higher than 50% where 2 in y-axis indicates 2 months delay.

# Feature Engineering
Three new features are created from the existing data which can be considered as six-month summary of customer paying habits.
  * Highest_Delay
    * This represents maximum delay in payments made by customer in duration of six months while paying bill for each month. e.g. If a customer delayed 2 months for paying first month bill and 4 months delay in paying 3rd month bill, the content of this column will be 4.
    
  * ![image](https://user-images.githubusercontent.com/102746816/161371718-22b27e43-2cf6-42df-8a7b-5b5b241a3efe.png)

  * Count_of_Delay
    * This column consists of sum of all delays in payment of bill during six months.
  * Payment_Mean
    * This column represents average of payment made by customers with respect to their bill amount.

# Base Model Fitting
* Various base models are fit and data is prepared according to their assumptions. e.g. Data is scaled for KNNClassifier whereas data is Transformed for LogisticRegression.
* For ensemble techniques, validation_curve is plotted in a semi-log graph to find the appropriate range using values around elbow-point before going for GridSearchCV to make hypertuning of parameters faster.
* Various model evaluation metrics are compared for various models to later find that GBClassifier giving the best recall value. Also feature_importance for various models are found out to observe the predictor deciding most in classification.

 * ![image](https://user-images.githubusercontent.com/102746816/161372666-5f83d221-c977-47da-9a9b-7b3498a5c504.png)

# Why we are interested in recall value of minority class(defaulters in our case) ?
* Detection of defaulting customers became more bussiness worthy than predicting wether that customer will default or not.
* Increasing recall score helps in decreasing the FN of our model which is makes more sense in decreasing default rates. After all above steps further research is carried out to increase the recall of minority class while sacrificing precision in the process.
# Handling Imbalance in dataset
* Due to lesser number of minority class instances, our model is not learning much about them, giving a near perfect precision and recall for non-defaulters compared to defaulters.
* Various SMOTEs are used to improve the recall of model, but the problem associated with SMOTE was creating artificial datapoints which led to overfitting of minority class.
* SMOTE+ENN gave the best result while considering recall as it considers both oversampling of minority class while deleting majority class which are unnecessary to our analysis(which can be considered as undersampling of majority class).

 * ![image](https://user-images.githubusercontent.com/102746816/161372732-d9f94660-a0f2-49f6-8e55-a523751ed207.png)

# Precision-Recall model evalution metric instead of traditional ROC-AUC.
* As most of interests fell into detecting defaulters, ROC-AUC looses its vitality as it a measure for detection both majority and minority class. Though it was performed while selecting best base model. So more optimisation was carried out for minority class which effectiveness can be seen visually using a precision-recall curve.

  * ![image](https://user-images.githubusercontent.com/102746816/161372703-4bd0b851-2586-4d61-b8bf-d15529b973ae.png)

    
  
