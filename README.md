# Analyzing Housing Data for Insights and Predictive Modelling
![](king-county-wa.jpg)
## Introduction
The aim of this project is to exhibit my skills in analyzing housing data as well as creating predictive models  to determine the price of houses in Kings County, Washington DC using **Jupyter Notebooks, Python, Scikit-Learn (a machine learning module)**, and other relevant modules, libraries and tools.
## Problem Statement
- What is the numerical distribution of houses in King County based on the number of floors?
- Which house features correlate with/ significantly affect house pricing?
- Can we develop a predictive model for house prices based on selected features for new builds or renovations?
## Skills/Concepts Demonstrated
- Python Analytics 
- Machine-Learning 
- Regression Analysis
- Predictive Analysis
## Data Sourcing and Description
### Sourcing
![](dataset_source.png)

The data was downloaded as a CSV file (kc_house_data.csv) from this page’s link address https://www.kaggle.com/datasets/harlfoxem/housesalesprediction in Kaggle.com. Using Python, Jupyter Notebooks, and the code displayed below, the CSV file was **downloaded** into Jupyter Notebooks and **loaded** into a Pandas Dataframe for effective analysis as seen below. 

![](Loaded_into_Pandas.png)
---
### Description
It is a real-world dataset which contains house sale prices for King County, and also includes some houses in Seattle. The dataset contains details of homes sold between **May 2014 and May 2015**. The table consisted of **21** columns before Data Transformation was carried out to make it just **19** columns and **21,613** rows representing **21,613 unique houses or residential buildings**.
Below is a table of the variables and their descriptions in the dataset.
Variable |	Description
:-----------:|:----------------------:
Id |	a special number allocated to each house
date | the date the house was sold
price	 | The price the house was sold for
bedrooms | number/count of bedrooms
bathrooms	| Number/count of bathrooms
sqft_living | the square footage of the home
sqft_lot | the square footage of the lot
Floors | total floors (levels) in the house
waterfront	| identifies if the house has a view to a waterfront (like in the lovely picture of a resident area in King County above☝️😄)
view	| the view rating
Condition | how good the overall condition is
grade	| overall grade given to the housing unit, based on King County grading system
sqft_above | square footage of house apart from basement
sqft_basement | square footage of the basement
yr_built | the year the house was built
yr_renovated | the year when the house was renovated, if at all
zipcode | Zip code
Lat |	Latitude coordinate
long	| Longitude coordinate
sqft_living15 | Living room area in 2015(implies-- some renovations) This might or might not have affected the lotsize area
sqft_lot15	| LotSize area in 2015(implies-- some renovations)

## Methodology
---
![](warnings_libraries.png)

**Pandas** was used to create, edit and analyze data frames, **Matplotib** and **Seaborn** for plotting regression and distribution plots, **Numpy** for statistical analysis, **Scikitlearn** was used to perform machine learning operations for predictive analysis. Of course, all these were done in a **Jupyter Notebook**.
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
### Question/Task 1
To answer the first question of analyzing the numerical distribution of houses according to their number of floors, I wrote a code to count the occurrences of unique values in the 'Floors' column, converting the results into a Pandas data frame as shown below.

![](Floors_and_counts.png)
---
### Question/Task 2
For the next question of which house features in the area correlate with/ significantly affect house pricing, I made a code to extract the R2 values for each feature to show how much each of them affect the house pricing. 0.3-0.4 show weak correlation and 0.5-0.7 show a moderate significant correlation.

![](correlation.png)

From the screenshot one can observe the house features with either low or moderate correlation with the price which at the end of the list has "1" (a perfect correlation) with itself. For illustration, the moderate (0.5 R2) correlation of the square foot of houses (represented as **_"sqft_above"_**) to their respective price is visualized below in a regression plot which shows that the larger the square foot of the house, the higher its price.

![](Regplot.png)
---
### Question/Task 3
The last question is where the real work🛠️ is. I had to create a Pipeline to pass the data through before it was used to train and test the predictive model. The Distribution plot below shows how well the model did in its prediction of prices compared to the distribution of the actual price data. It did not do too well😅.

![](R2_1.png)	![](Dplot_1.png)

Assuming the cause of this case of overfitting is due to multicollinearity (high correlation between two or more features), the predicitive model needs ridge regression. Thankfully, a module in Python can help out. Let's see if the price prediction is any better after the RidgeRegression Module is applied in the code below.

![](R2_2.png)	![](Dplot_2.png)

Eureka! That's much better. The plot above shows that the Model can predict prices almost as accurately as the prices ought to be i.e. based on the original dataset.

---
I went ahead to carry out a 2nd order polynomial transform on the training and testing data but it did not come out any better than the previous model. The code I wrote and the visualization is below nonetheless.

![](2nd_order_polytransform.png)	![](Dplot_3.png)
---
In this final step in **task 3**, assuming the Real Estate Company wants to build a new set of houses at a waterfront, along with other specific features such as the ones in the table below, I simply input these features into the predictive model and watch what the price/output of the house would be.

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

## Findings and Recommendations
### Findings
- Less number of houses have more floors than other most likely due to the costs of building, maintaining and even purchasing such residents
- The size, grade, number of rooms, and location of each house greatly influences thier price.
- The regression model works fine for the housing data. The amount predicted by it—about $1m— is understandable because of the outrageous living room size and other unrealistic features I put for the model to make predictions with.

### Recommendations 
- To save more cost, the Real Estate Company should consider investing in houses with smaller number of floors which would still yield profit and are cheaper to build. The abundance of small houses compared to the scarcity of taller ones shows that conditions in the area favour them more than taller ones.
- For higher prices, the features which affect the price the most (as analyzed above) should be considered so that potential clients do not avoid the company's houses for already existing better and cheaper options.
- The predictive model works with 2015/16 housing data and does not put external factors like economic changes into consideration. Thus, either newer data can be used to augment the model's predictive accuracy, or the Real Estate Company manually predicts the price of each type of house they seek to invest in.
- 
## License
This dataset used in this project is licensed under [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/)
