# Logistic_Regression_Model_Default
The repository collects all the documents used to apply the Logistic Regression Model on the "Default" dataset.
VI.	DEFAULT DATASET – GETTING STARTED
No missing values have been found when importing the dataset. In addition to the “Default“ dependent variable ( 0 = No default ; 1 = Default) the dataset provides also info about 9 more variables:
•	Gender 0=Male, 1=Female 
•	Age in years
•	Years of education
•	Retired 0=not retired, 1=retired
•	Household income in thousands
•	Credit card debt in thousands
•	Other debt in thousands
•	Marital status 0=unmarried, 1=married
•	Home ownership 0=rents, 1=owns home  
Five of them are dummy variables (0 = no, 1=yes). 
By looking at the summary we see that “age” takes into account adult people from 18 to 79 years old with a mean of 44. The “ed” goes from a minimum of 6 years up to 23 years spent in studying.  
 
The variable income, that goes from 9k to 1073k per year, suffers from outliers. Consequently, to get a good fit of model, it has been decided to drop out from the dataset all the observations with an income greater than 100k.
 
At the beginning, it has been launched a raw model that was comprehensive of all the variables. However, this model missed to meet some assumptions. So, a correlation analysis has been launched and it has been found out that the variables “creddebt” and “othdebt” are highly correlated between them and also with the variable income. Consequently, it has been decided to drop them.
 
VII.	THE LOGISTIC MODEL
Once the data have been cleaned from outliers and correlated predictors, it has been applied the logistic regression model to predict the probability that a customer will fall in a loan default. When launched, the first draft of the model included all the variables. However, some of them were not statistically significant. Keeping them could have led to overfitting. After some attempts, the following one represents the best model found. It predicts the probability of having a loan-default based on the age, the years spent in education and weather the customer owns the home or not:
logit <- glm(default ~ age + ed + income + homeown, data=Data, family='binomial')
 
A.	INTERPRETATION
It can be seen from the output that just 3 out of 10 predictors were significantly associated to the outcome (p-value lower than 0.05). The coefficient estimate for the variable “age” is -0.07. This means that a decrease in age is associated with an increase of the probability to fall in loan default.  The coefficient for “ed” is equal to 0.06, consequently an increase in years spent in education corresponds to an increase in the probability. Instead, owning a home is inversely proportional.  
From that output it is possible to build the logistic equation as:
Default loan = 1.87 – 0.07 * (age) + 0.06 * (ed) – 0.3 8 (homeown).
B.	MAKING PREDICTIONS 
A function has been built to estimate the probability that the event occurs considering some parameters. For example, if we consider an adult 38 years old, with 25 years spent in education who doesn’t own the home, there is a 72.6% of probability that he will fall into a default loan. 
C.	MODEL ACCURACY AND THE CONFUSION MATRIX 
 
The model accuracy is measured as the proportion of observations that have been correctly classified. The classification prediction accuracy is about 73%. 
•	From the confusion matrix we can also summarize the values as follow:
•	1006 true negatives (TN): when the model correctly predicts “No” default
•	744 true positives (TP): when the model correctly predicts “Yes” default
•	362 false negatives (FN): when the model incorrectly predicts “No” default
•	296 false positives (FP): when the model incorrectly predicts “Yes” default
D.	THE ODDS RATIO 
 
The odds ratio table says that the odds of having a loan default increases by a factor of 0.93 for a one-year increase in age and 1.06 for one year increase spent in education. Also the odds of having loan default are multiplied by a factor of 0.74 if owning a house. 
VIII.	CONCLUSIONS
With the first part of this essay, the author walked the reader through different statistic models aimed to predict the forecast for the car registration. Even though an ARIMA model has been tuned with different parameters, the ETS model has been found out to be the best one in predicting future numbers. According to this model the forecast for the period February-July will vary from a minimum of 4908 to a maximum of 23.851 car registered. This forecast is aligned to the one coming from the seasonal Naïve method. With the second part, a statistic model has been applied to a customer behaviour. In the specific it has been built a model that predicts the probability that a customer will have a loan default considering some conditions like the age, the number of years spent in education and whether the customer owns a home or not. This essay represents a starting point for statisticians that would like to apply other models for forecasting and compare them to find the best one in terms of output. 

