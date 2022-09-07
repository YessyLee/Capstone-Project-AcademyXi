# Capstone-Project-AcademyXi

![Capstone-Project-AcademyXi](./image/Seoul_Bike_Rental2.jpg)

# Analysis for BT Seoul Bike Rental Service in Seoul, South Korea

**Author:** Yessy Rayner
***

## Business Overview
Since COVID-19 pandemic, bike rental businesses in Seoul are booming. This is an unexpected result for BT Seoul Bike Hire, so they would like some analysis on:

1. How many extra staff members require during busy period. It is estimated by the management that 1 staff member required to service every 200 bikes/customers
2. Quiet time of the day, so they can service their bikes with less disruption. They are currently close 1 day per month to service their bikes
3. BT Seoul Bike Hire also would like to expand their business to other major metropolitan cities such as Busan and Incheon using the same business model and staffing method.

## Data Understanding and Preparation
The dataset contains rented bike count at each hour with the corresponding weather data and date information for the six months period (From March to October 2018). In total there are 7890 rented bike data counts with 10 features, which being grouped as follow for the testing and validation:

- Base variables: Temperature (C), Dewpoint (C), Solar radiation (MJ/m2) due to apparent linear relationship
- Continuous variables: Humidity (%), Windspeed (m/s), Visibility (10m), Snowfall (cm) and Rainfall (mm)
- Discrete variables: Date and Hour
- Categorical variables: Seasons and Holiday

## Preprocessing / Data Cleaning
Here are some of the data preprocessing and cleaning methods being performed:

Checked if all data are in correct data types
Checked any missing data
Added 2 additional categorial variables: Day_of_week (Monday to Sunday) and Shift(Early morning, Morning peak, Mid day, Evening peak) – This will help with predicting the staffing requirements
Drop ‘Functioning Day = No’ (Close down due to bike servicing day), removed the ‘No’ value as it skews the overall data.

## Modelling
Upon reviewing the above datas and their value, here are my breakdown on the features or variables. So we can model it approriately on the next step using linear regression model to predict property prices based on below features:

Categorical: Waterfront, zipcode
Discrete: condition, grade, bedrooms, bathrooms, floors, view
Continuous: yr_build, yr_renovated, lat, long, ALL of sqft_

The data also split into a train data (75%) and a test data (25%) to ensure accuracy, also using random_state and shuffle to avoid any biases.

## Regression Results

1. Model 1: Build a base model based on 3 features that have the highest correlation to the price. However the R2 score is only 0.564. 
2. Model 2: Added 5 continuous features which bring the R2 score up to 0.756.
3. Model 3: Added 5 discrete features to Model 2, which bring the R2 score to 0.775 (Pretty good score with 13 features altogether)
4. Model 4: Using Recursive Feature Elimination method, the RFE picked 10 of the most important features and the score is on par with model 3 at 0.772
5. Final Model: Adding 2 more categorial features, improved it using OneHotEncoder which increased the R2 score to 0.876

Here are some graphs for comparison (Base Model vs. Final Model):

![BEFORE MODELLING BASE VARS](https://user-images.githubusercontent.com/107485501/185570357-05a329d6-4f69-4c2c-bce8-e2aa5dbeddd0.png)
![AFTER MODELLING TRAIN SET](https://user-images.githubusercontent.com/107485501/185570385-3058a63d-e9fc-4f38-ad75-b9aa22028961.png)

Plotting data against predictions/final model to check on the accuracy: (Pretty good result!)

![FINAL MODEL GRAPH ACTUAL VS PREDICTION](https://user-images.githubusercontent.com/107485501/185570507-6382c42f-6428-4ece-8ab4-d28729c67440.png)

## Summary
Here are some of the important findings based on the results from above testing and modelling on different features and methods:

1. Initially only 3 features stands out that have strong linear regression, which we used to build our base model (base_vars = 'sqft_living', 'grade', 'sqft_above')
2. However the R2 result wasn't that great (at 0.56) when using the base variables only
3. We know that there are other factors/parameters that will affect the overall house price
4. So we used the RFE (Recursive Feature Elimination) method to calculate the most important variables. The results are 10 variables as follow: 'yr_built', 'lat', 'long', 'sqft_living', 'grade', 'condition', 'bedrooms', 'bathrooms', 'floors', 'view'
5. The R2 score from RFE method increased from 0.56 to 0.77 (increased of 19%, pretty impressive just by adding 7 more features)
6. The final step is to add the categorical variables (zipcode and waterfront features) using OneHotEncoder, the result jumped from 0.77 to 0.87
7. Great result, as we hear it all the time 'LOCATION, LOCATION, LOCATION' in real estate, and the modelling above proven by adding the location (zipcode) to the parameter/feature make a huge different on the R2 score and to minimise the MSE (Mean Square Error)

## Next Steps and Recommendation
1. The linear regression model is now build, and we can implement the linear regression calculation into client's preferred interface, so the team at KC Financial Investment can drop in these features/parameters then it will calculate the predicted house price automatically
2. The simple interface and calculation can be build into Microsoft Excel, Power BI, or Intranet (Internal site) for ease of use by the staff members. This is a great tool if you only have a handful of houses to analyse
3. However as a starting point, we can analyse all of the properties available for sale in Kings County by scraping the data from multiple websites (such as realtor.com, homes.com etc) currently over 500 houses available in the market.
4. Then we will present list of houses that are under the predicted price for KC Financial Investment to consider purchasing to start maximising their profit earnings.

![DAT_Project2_Presentation_Yessy](https://user-images.githubusercontent.com/107485501/185571391-0b1e3866-a8a7-417b-9951-728142e9f5e8.png)

## For More Information

See the full analysis in the [[Jupyter Notebook](./Yessy Project 2.ipynb)](https://github.com/YessyLee/Yessy-Project-2/blob/9b4dd5531d7552dbf9ba153a313ecf33946fb4dc/Yessy%20Project%202.ipynb)

For additional info, contact Yessy Rayner at [yessy.rayner@gmail.com](mailto:yessy.rayner@gmail.com)


## Repository Structure

```
├── data
├── images
├── DAT_Project2_Presentation_Yessy.pdf
├── README.md
├── Yessy Project 2 - Jupyter Notebook in PDF.pdf
└── Yessy Project 2.ipynb
