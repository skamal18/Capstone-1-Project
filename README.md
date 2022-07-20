# Carbon-Dioxide-Emissions
# ☀️ Carbon-Dioxide Prediction Model ⚡️
## Data Science Project
- For code go to [Notebooks](/notebooks)
- For raw data go to [Data](/Data)

**Problem Statement**   

Carbon dioxide (CO2) is the primary greenhouse gas emitted through human activities. CO2 accounted for about 79% of all U.S. greenhouse gas emissions from human activities. A typical passenger vehicle emits about 4.6 metric tons of carbon dioxide per year. Every gallon of gasoline burned creates about 8,887 grams of CO2.

This project aims to predict the Carbon Dioxide emissions from cars based on their features such as engine size(L),number of cylinders, fuel type,fuel consumption, transmission type, make and model. A regression model will be developed to predict the emissions based on the most important/relevant features selected from the dataset.

**Context**     

Over 7000 vehicle data has been gathered and their CO2 emissions(g/km), fuel consumption(L/km), No. of cylinders, Engine size(L), Make, Model and Transmission Type has been recorded.

**Goal**

After analyzing this data we should be able to: 
- Predict the Carbon dioxide emissions(g/km) based on the most relevant features presented in the dataset
- Test our prediction against the real data to determine its accuracy

**Method**

Discover if there is any relationship between different features

- Perform Exploratory Data Analysis to discover patterns,spot outliers, test hypothesis and check assumptions with the help of summary statistics and graphical representations
- Analyze individual features and its impact on the model performance in predicting the CO2 Emissions.
- Determine the best model for predicting the CO2 Emissions based on the model score


![CO2 Emissions](https://user-images.githubusercontent.com/98712279/179902500-b4addd4a-6607-4976-8465-3391d566c6ca.png)
 This graphs shows the mean CO2 Emissions from each car brand used in Canada. 


![Fueltype_comb](https://user-images.githubusercontent.com/98712279/180002377-dd4daf12-bdf6-4e37-bf10-0b3d6b52a867.png)
Ethanol has the lowest CO2 Emissions in comparison to other fuel types and highest fuel consumption. E85 contains 83% ethanol content and has about 27% less energy per gallon than gasoline so therefore it would consume more fuel in comparison to gasoline to go the same distance(L/km). In the city, vehicles make many stops and starts. Accelerating a vehicle from zero to even a slow speed like 30 or 40 km/h several times takes quite a bit more energy than accelerating a vehicle to 60 km/h and maintaining it. Using more energy means using more fuel to generate it, hence the city has higher fuel consumption.



**Modeling**
Nine different models were tried and test. Fine hyperparameter tuning on each of them was performed to obtain high coefficient of determination and low Mean Average Error and prevent overfitting of the training dataset. The data was split into 30% testing and 70% training. The nine models that were tested are as follows:

- **Lasso Regression:** This model introduced a new hyperparameter, alpha, the coefficient to penalize weights. The alpha chosen was 10 and cross validation was performed. 

- **Ridge Regression:** This model penalizes for the sum of squared value of the weights. Thus, the weights not only tend to have smaller absolute values, but also really tend to penalize the extremes of the weights, resulting in a group of weights that are more evenly distributed. After performing k-fold cross-validation fit to the trainining set, the optimal alpha obtained was 10. 

- **Elastic Net Regression:** The absolute value penalization and squared penalization are included in this model. The l1_ratio parameter(elastic net mixing parameter chosen was 0.95.

- **Linear Regression:** This model is not penalized for its choice of weights therefore during the training stage, if the model feels like one particular feature is particularly important, the model will place a larger weight to that feature which may lead to overfitting. To our surprise, the model gave the same score as the ridge regression model. This maybe because some features are important than others in predicting C02 Emissions in the dataset given.

- **Decision Tree Regression:** Grid Search was performed and the max_depth selected from this grid search was 12. 

- **Random Forest Regression:** Random Search with cross validation was performed and the best parameters obtained for this model when performing hypertunig are:
- {'n_estimators': 600,
 'min_samples_split': 2,
 'min_samples_leaf': 1,
 'max_features': 'sqrt',
 'max_depth': 100,
 'bootstrap': False}

- **Gradient Boosting:** With this model, the best parameters we obtaine were maximum depth of 6 and number of estimater=200. 

- **Support Vector Machine:** After performing gridsearch, the best parameters obtained for hyptertuning the model were:
SVR(C=100, degree=2, epsilon=0.5, gamma=1, kernel='linear')

- **K-Nearest Neighbors Regression:** Constructed an Elbow plot to determine the optimal value of K that yields lowest MSE. From the elbow plot, we deduced that the k-value of 7 yielded the lowest MSE.



![Model Performances](images/model_test.JPG)

As you can see, the Gradient Boosting model was closest. To further verify this we made a new, much larger set of random data and compared the two again:

![Model Larger Performances](images/model_large.JPG)

The Gradient Boosting Model was the most accurate for predicting power output!

**Conclusion**

Using the model, we calculated the power output for the past 20 years in Gandikota, India using historical meteorological data. With this we were able to determine a good estimation for how much power the plant should generate in 2021: 

![Predictions](images/model_predictions.JPG)

To further validate our model and the importance of machine learning in general, we also calculated a "simple sum" of the plant's power output by taking the power it generated over ~31 days and multiplying it by 12. This graph shows the difference that machine learning can make in prediction models: 

![Machine Learning Performance](images/simple_sum.JPG)

The last thing we tested was how much extra power the Gandikota plant could generate by upgrading its solar arrays. While analyzing, we determine the arrays currently have a NOCT value around 18, while industry average is around 48 today. I replaced the plant's NOCT to see how big of a difference it would make:

![Upgrade](images/upgrade.JPG)

If the Gandikota power plant upgraded they would generate an additional:

- 191,388,153.45 kW/hrs
- $6,315,809.06 in revenue

in just one year after upgrading. I recommend that the Gandikota Solar Power Plant invests into upgrading their arrays so that they can improve overall efficiency and generate more revenue for better salaries, expansion opportunities and more green energy!
