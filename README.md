# Analyzing Housing Data for Insights and Predictive Modelling
![](king-county-wa.jpg)
## Introduction
The aim of this project is to exhibit my skills in analyzing housing data as well as creating predictive models  to determine the price of houses in Kings County, Washington DC using **Jupyter Notebooks, Python, Scikit-Learn (a machine learning module)**, and other relevant modules, libraries and tools.
## Problem Statement
- What is the numerical distribution of houses in King County based on the number of floors?
- Which house features in this area correlate with/ significantly affect house pricing?
- Can we develop a predictive model for house prices based on selected features for new builds or renovations?
## Skills/Concepts Demonstrated
- Python Analytics 
- Machine-Learning 
- Regression Analysis
## Data Sourcing and Description
### Sourcing
![](dataset_source.png)

The data was downloaded as a CSV file (kc_house_data.csv) from this page’s link address https://www.kaggle.com/datasets/harlfoxem/housesalesprediction in Kaggle.com. Using Python, Jupyter Notebooks, and the code displayed below, the CSV file was **downloaded** into Jupyter Notebooks and **loaded** into a Pandas Dataframe for effective analysis as seen below. 

![](Loaded_into_Pandas.png)
---
### Description
It is a real-world dataset which contains house sale prices for King County, and also includes some houses in Seattle. The dataset contains details of homes sold between May 2014 and May 2015. The table consisted of 21 columns before Data Transformation was carried out to make it just 19 columns and 21,613 rows representing 21,613 unique houses or residential buildings.
Below is a table of the variables and their descriptions in the dataset.
Variable |	Description
:-----------:|:----------------------:
Id |	A special number allocated to each house
date | the date the house was sold
price	 | This is the prediction target
Bedrooms | Number/count of bedrooms
bathrooms	| Number/count of bathrooms
sqft_living | Square footage of the home
sqft_lot | Square footage of the lot
Floors | Total floors (levels) in the house
waterfront	| House which has a view to a waterfront
view	| Has been viewed
Condition | How good the condition is overall
grade	| overall grade given to the housing unit, based on King County grading system
sqft_above | Square footage of house apart from basement
sqft_basement | Square footage of the basement
yr_built | Built Year
yr_renovated | Year when house was renovated
zipcode | Zip code
Lat |	Latitude coordinate
long	| Longitude coordinate
sqft_living15 | Living room area in 2015(implies-- some renovations) This might or might not have affected the lotsize area
sqft_lot15	| LotSize area in 2015(implies-- some renovations)

## Methodology
---
![](warnings_libraries.png)

**Pandas** was used to create, edit and analyze data frames, **Matplotib** and **seaborn** for plotting regression and distribution plots, **Numpy** for statistical analysis, **Scikitlearn** was used to perform machine learning operations for predictive analysis. Of course, all these were done in a **Jupyter Notebook**.
## Data Transformation
### The following transformations were made to the dataset:
- Missing values detected in the columns "bedrooms" and "bathrooms" were replaced with the mean values in eacn column.
![](removing_unwanteds.png)
---
- Using Pandas to_datetime function I formatted values in the 'date' column to their proper format.
- unwanted columns 'Unnamed:0' and 'id' were removed

Table with improper date format and unwanted columns |	Transformed table
:-----------------:|:----------------------:
![](a_look(1).png) |	![](adjusting_dataset(1).png)

## Analysis
To answer the first question of analyzing the numerical distribution of houses according to their number of floors, I wrote a code to count the occurrences of unique values in the 'Floors' column converting the results into a data frame as shown below.

![](Floors_and_counts.png)
---
For the next question of which house features in the area correlate with/ significantly affect house pricing, a code was written to extract the R2 values for each feature to show how much each of them affect the house pricing. 0.3-0.4 show weak correlation and 0.5-0.7 show a moderate correlation.

![](correlation.png)

The moderate (0.5 R2) correlation of the square foot of houses **_"sqft_above"_** to their respective price is visualized below in a regression plot which shows that the larger the square foot of the house, the higher its price.

![](Regplot.png)
---
The last question is where the real work🛠️ is. I had to create a Pipeline to pass the data through before it was used to train and test the predictive model. The Distribution plot below shows how well the model did in its prediction of prices compared to the distribution of the actual price data...not too well😅.

![](R2_1.png)	![](Dplot_1.png)

Assuming the cause of this case of overfitting is due to multicollinearity (high correlation between two or more features), the predicitive model needs ridge regression. Thankfully, a module in Python can help out. Let's see if the price prediction is similar after the RidgeRegression Module is applied in the code below.

![](R2_2.png)	![](Dplot_2.png)

Eureka! That's far better. The plot above shows that the Model can predict prices almost as accurately as they ought to be i.e. based on the original dataset.
---
I went ahead to carry out a 2nd order polynomial transform on the training and testing data but it did not come out any better than the previous model. The code I wrote and the visualization is below nonetheless.

![](2nd_order_polytransform.png)	![](Dplot_3.png)
---
In this final step, assuming the Real Estate Company wants to build a new set of houses at a waterfront, along with other specific features such as the ones in the table below, I simply input these features into the predictive model and watch what the price/output of the house would be.

Total number of floors (levels) in each house | 3.5
:-----------:|:----------------------:
House must have a view to a waterfront (represented by) | 1
Location | 47.5
Number of bedrooms (in each house) | 4
Basement square footage | 400
Number of bathrooms | 2
Living room area (in sqft.) | 2000
Grade | 8

![](Price_Prediction.png)

## Conclusions and Recommendations
### Conlusions
- Less houses have more floor than other most likely due to the costs of building, maintaining and even purchasing such residents
- 
---
