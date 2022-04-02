# Inspiration
During my stay in Banglore while pursuing a Data Science course, I came across usage of app like 'SIMPL' and 'LazyPay' where Credits are given without any proper verification. Therefore I wanted to dive deeper into such usecases. But the problem associated with this problem was finding a dataset representing the scenario. With further research I found 'Taiwan Bank Credit Card Dataset' from UCI repository where a customer paying habits are observed for six months before considering him/her as default.
# Insights from Exploratory Data Analysis
  Around 24% of male customers and around 20.8% of female customers are defaulting, which suggests a customer being a male has more likelihood to default.
  Customers having 'High-School' as highest education have high probability of defaulting next month.
  Customers from "Younger Age" group are making more default than "Older Age" group which can be indication of stable income for later.
  Various customers are assigned different Limit Balance i.e. 'LIMIT_BAL in our dataset according to analysis done before. It was found that customers with lower      'LIMIT_BAL' are more probable of defaulting.
  All of the above conclusions are tested Statistically using ttest for independence and chi-square test for independence depending upon the datatype we are tring to find independence of.
  ![image](https://user-images.githubusercontent.com/102746816/161371196-ab84277f-3d33-49f8-9140-f814040c6c38.png)
  Most of the customers are paying the partial bill amount and duly paying. And when payment is delayed more than 2 months, the chances of default goes higher than 50%