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



![Arrays](/images/arrays_ind.JPG)    

No one array was dragging the power plant down, but to double check we compared each array to the average for each day and found, once again, that no one array was under or overperforming.   

![Array 1 Compared to Average](images/array_v_average.JPG)    

**Nominal Operating Cell Temperature**    

Halfway through the exploratory data analysis, we learned about the equation for Nominal Operating Cell Temperature, which can be used to predict the temperature of the solar cells and also analyze their overall efficiency.

![NOCT Calculation](images/NOCT_calculation.JPG)

Using this, in addition to finding out which variables were most important through a correlation heatmap, we were able to determine that the most important features for creating our model were:

- DC Power (kW)
- Ambient Temperature (C°)
- Module Temperature (C°)
- Solar Irradiation (W/m²)

**Modeling**

This time around we tried three different models, and because we already had the equation to tell us exactly what our power output values should be, we had very good testing/train splits. The three models we tested were as follows:

- **Linear Regression:** A simple, normalized linear regression with a test size of 0.25. This worked really well because many of the relationships between variables were already linear. With a high model score and a low Mean Absolute Error this looked like a great pick at first.

- **Random Forest Model:** This model was imputed with the mean and with 12 estimators for our data pipeline. The results were underwhelming, with a much lower score than the linear regression and higher MAE.

- **Gradient Boosting:** Initially this model yielded a MAE of around -10, but with some improvements to the hyperparameters, notably increasing the number of trees to 70, we eventually got a great model score and an even lower MAE.

To properly determine which model would most accurately predict the daily power output, we decided to make two random sets of data and compare each model against a control using the same random data. On the far left you'll see the "real" data, meaning what the power output should look like, and to the right you'll see how each model performed.

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
