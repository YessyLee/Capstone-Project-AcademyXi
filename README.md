# Capstone-Project-AcademyXi
Final Data Analytics Project
![Capstone-Project-AcademyXi](./image/Seoul_Bike_Rental2.jpg)

# Analysis for BT Seoul Bike Rental Service in Seoul, South Korea

**Author:** Yessy Rayner
***

## Business Overview
KC Financial Investment would like to expand their business portfolio to include property buy and sell investment. They would like to invest in the property buy and sell market in the Kings County, California. According to Realtor.com homes for sale in Kings County spend an average of 50 days on the market, so it is quite a lucrative market in term of the short sales turn around. Also the outgoing fees for buying and selling in Kings County are relatively low (under 1%) as long as they don't engage the real estate agent services due to high commission.

Their goal is to maximise profits through the buy and sell, and would like the Business Analyst (myself) to build a model that predict the house prices based on the sales database in the past two years.

Once the prediction model is built, they will then analyse all of the available houses that are currently for sale in the market and purchase the properties that are under predicted asking price. They will resell after a few weeks.

## Data Understanding and Preparation
I will analyse Kings County's property sales datas in the past two year to build a regression model. There are approximately 21,000 sales in the past 2 years.
This is a good size for analysis.

The datat cleaning process will ensure the datas are in correct data types, checking missing value and fill it with approriate value.
Once datas are cleaned, I will separate them into 3 variables or features as follow for testing and validation in order to get the best model:

1. Continuous variables (A continuous variable can be of any value in a range, for example: sqft living and lot sizes)
2. Discrete variables (certain number of particular values that can be counted, for example: number of bedrooms)
3. Categorical variables (descriptive categories instead of numerical or measured categories, for example: zipcodes)

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
