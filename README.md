Project Description: The aim of this project was to get a hands-on experience on coding and using data mining techniques on a dataset in order to get some valuable insights. We decided to go with the Uber & Lyft Analysis dataset that was available to us on Kaggle.

Background:

The initial area of the analysis that we started with was to see which cabs are booked the most, whether Uber or Lyft. On further analyzing the data that we have available with us we changed the area of analysis from predicting the most of number of bookings to which type of cabs are booked the most.

Introduction:

- In the modern world, consumers are provided with a plethora of options to choose from when seeking on-demand, efficient transportation such as Uber, Lyft, and traditional taxis.
- The emergence of ride-hailing technology companies such as Uber & Lyft have revolutionized the transportation services industry – the presence of these companies has made it more efficient than ever for consumers to find an efficient means of travel to-and-from any location, and for heading to work
- Despite their efficiency, these services tend to be quite expensive, which in turn can make these services a less feasible option for travel

For many employees,  being forced to incur hefty travel costs when commuting to and from work can have detrimental impacts on their personal finances and livelihood

- This analysis aims to provide various models for accurately classifying which trips are provided by “Lyft,” a popular rideshare company who offers the industry’s lowest hourly rate for time of travel

The insights generated by our analysis will serve as a valuable asset for employees to use when ***determining cost efficient travel options,*** which in turn will help facilitate operations within the business by the ***reducing cost and boosting efficiency of travel for employees***

Describing the dataset:

• The data for this analysis has been derived from **Kaggle** and it contains two datasets, “cab_rides.csv” and “weather.csv” which together outline critical information regarding rideshare services & weather for Uber, Lyft, and Taxi rideshare transactions.

- The **variables** contained in the “cab_rides.csv” and “weather.csv” dataset include:

○**distance** - the distance traveled (in miles)

○**cab_type** - the  rideshare company responsible for a service

○**time_stamp** - time that service is started

○**destination** - endpoint location for a service

○**source** - starting point location  for a service

○**price** - price of the transaction

○**surge_multiplier** - multiplier responsible for calculating pricing amounts for riders and drivers

○**product_id** - the type of rideshare service

○**name** - distinguishes the type of vehicle being used to complete the service

○**temp** - temperature (in Fahrenheit) at start of service

○**location** - location (start point) of service where weather is recorded

○**clouds** - cloudiness index during a service reflecting level of cloudiness

○**pressure** - pressure index during a service reflecting level of atmosphere pressure

○**rain** - rain index for a service reflecting level of rain

○**humidity** - humidity index  for a service reflecting level of humidity

○**wind** - wind index for a service reflecting level of wind

- Our **input variables** for the analysis are:

○**distance**

○**destination**

○**source**

○**surge_multiplier**

○**product_id**

○**name**

○**temp**

○**location**

○**clouds**

○**pressure**

○**rain**

○**humidity**

○**Wind**

- Our output variables for analysis are:

○**cab_type**

○**price**

Data Preprocessing:

- Due to the numerical variables in our dataset not following a normal distribution, we felt it was appropriate to **standardize** the data.
- We also proceeded with encoding our categorical variable so that they were in the proper format to be incorporated into our models.
- We ultimately determined that the time_stamp was irrelevant for our analysis, thus we removed the variable entirely
- We created a new variable, merge_date, which contained the year, month, day of month, and hour of day for each service recorded in “weather.csv”

This allowed us to incorporate such factors into our analysis when classifying strictly “Lyft” services

- We created a new variable, cab_status, which specifies whether a service was completed by “Lyft” with a value of 1 or 0 if it was completed by “Uber”
- In our product_id variable we identified several levels, “Black,” “BlackSUV,” and “WAV” which did not correspond to any rideshare services offered by “Uber” or “Lyft”, thus we removed rows which contained these levels as they would be irrelevant for our analysis going forward.
- Due to the imbalance observed in our cab_status outcome variable, we proceeded with balancing our data using SMOTE.

Model Fitting:

- We fit four models over the course of the analysis; **Logistic Regression, Decision Tree, Random Forest,** and **K-NN**

We utilized the default parameters for each of our models given that we were already provided with a desirable AUC curve We assessed each of our models based on **Accuracy, Sensitivity, Specificity** metrics  and **ROC/AUC Curve**

- Based on the results of our assessment criteria, we identified the **Decision Tree Model** to be most appropriate when classifying “Lyft” rideshare services

Both our Random Forests Model and Decision Tree Model provided us with an AUC of 0.97

Given the Decision Tree Model provides us with better metrics for Accuracy, Sensitivity, and Specificity values, we went with the Decision Tree Model as our best model (see Fig. 8)

The **top-3 most important features** identified for the model are **“age,” “hour,”** and **“source_North Station”** (see Fig. 7)

Insights:

- Based on the analysis we can say that the price of a ride is influenced by the distance of the ride and the surge multiplier applied, which are likely to be the main factors affecting the price
- The time of the day does not seem to have a significant effect on the price or surge multiplier – this insight can be useful for ride-sharing companies to better understand the factors that drive ride pricing and to develop pricing strategies that optimize profits while remaining competitive.
- We can see that from the data that the prices are not increasing when it rains – this could be due to consumers not wanting to travel when it rains heavily and being subjected to paying substantial costs
- Based on the data we can see in terms of location, source and destination that the majority of locations which offered “Lyft” services are Back Bay, Boston University, Financial district,North , Theatre District – thus it would be appropriate to add additional locations
- We also found the most important features for our Decision Tree Model – price, hour and the source North station played a key role in determining our insights, and should prioritized for consideration by employees when seeking “Lyft” as their rideshare service

Model Limitations:

- ***Limited Data:*** The data set has limited information on the Lyft Line service and the weather conditions, which could lead to inaccurate predictions
- ***Data Quality:*** The data set had some missing values, and some data may have been inaccurate information, which altogether can, and did, affect the accuracy of the model
- ***External Factors:*** External factors such as road closures, traffic congestion, and accidents can affect the accessibility of “Lyft” services, and these factors are not captured in the data set
- ***Changing Market:*** The demand for Lyft Line may change over time due to changes in customer preferences, competition, or macroeconomic conditions
- ***Missing Variables:*** The data set may not include all the relevant variables that affect the demand for Lyft Line, such as customer demographics, promotions, or events in the area.
