# The Price is Right: Selecting the Correct Home Selling Price
## By: Matthew Nykaza

![Home_Picture](https://github.com/MxCxSxN/the-price-is-right/blob/main/images/home_selling_pic.jpg)

# Overview 
For this project I was given, by the Flatiron school, a dataset consisting of the King Country Housing sales over a period of May 2014 to May 2015. I was tasked with finding a relevant business problem and conducting analysis using the given data and conducting statistical models to answer the business question. I decided to try and help basic homeowners find the appropriate price to list their home at, given basic variable (bedrooms, bathrooms, lot size etc.). I began this process by preprocessing the data by taking out unneccesary variables (i.e. views, sqft basement, etc.) and changing some of the variables (changing basement size to whether or not the home has a basement for example). Once this basic data cleaning was complete I set out to create a base model just to see what the correlations, r2 score and other relevant testing metrics looked like before doing any standardization techniques. With that subpar model complete I began to change the data using standardization and normalizing techniques. This started with log-transforming the target variable (selling price) which turned that variable into a much more normal distribution. Following that I used a standard scaler from sklearn which removed the mean from the independant variables and scaled to the variance. This did not necesarily make the data "more normal", but it did bring center the data around a mean of 0 with a standard deviation of 1. This did improve on my model somewhat, but overall did not make my prediction power (as read by R2 score) any stronger. My final model featured log-transformed, and Standard Scaled data, which did not improve the R2 score, but did provide the least error, and gives me confidence that there is something strong to go on here. I recommend that a home seller not use this model quite yet, but with more time I am confident that there can be a great conclusion reached, and a accurate home selling model. 

# Business Problem
Selling a home can be an exceedingly stressful process. One of the biggest pain points for home sellers is selecting the correct listing price for that home. Pick a price that is too low, and you run the risk of losing out on a lot of potential earnings. To high and you can wind up with a house that remains on the market for a long time, potentially hamstringing efforts to move into that new house. With this dataset, and statistical knowledge I intend to create a model that will assist with people knowing the right price to list their home at. 

# King Count Housing Dataset

Data can be found in the `data` section of this GitHub repository.

- In this modeling I used data provided to me by Flatiron School. It consists of a single dataset that include relevant information about housing sales from May 2014 to May 2015 in King County, WA. 
- There are many variables in this dataset and they include home ID (a simple identifier unique to each sold home), selling price, number of bedrooms and bathrooms, square feet of the living space, squarefeet of the total lot, number of floors, whether the home is on the waterfront or not, whether the home has been viewed or not, a overall condition rating, a King County Housing grade, year built, year remodeled, zipcode it is in, the latitude and longitude of the location, and the square feet of the 15 surrounding homes lots and living space. 
- The target variable for this modeling will be the selling price ('price' in the data).
- The feature variables that I will be using for this project will be bedrooms, bathrooms, sqft_lot, floors, waterfront, condition, grade, and year built. 

# Analysis

Throughout data preprocessing was performed. This includes reviewing any duplicates, appropriately handeling outliers, creating new variables from existing data, and removing unnecessary data. 

Once that was completed various vizualizations including histograms, heatmaps and scatterplots. These were completed to view normality and correlations amoung the datasets. One-Hot-Encoding was completed for categorical variables, this ensured that they were properly understood by the future modeling processes. 

# Modeling

First a basic model was completed that had no scaling or transformations done to the data. That was followed by log-transforming the dependant variable (price). After that process was completed a Standard Scaler from sklearn was applied. This can be sensitive to outliers, but as we have already mitigated those I am not too concerned about that, what it will do is bring all of our data to a mean of 0 with a standard deviation of 1. This centers the data and brings it to a Gaussian standard normal deviation, which helps with any modeling. Following a series of other modeling techniques were used, each trying to achieve the best results for the R2 score, MSE and other relevant datapoints. 

# Final Model

- R2 Score:
    - Ultimately despite our best efforts at scaling the data, the original model managed to perform the best for the percentage of variance explained by the model, but this effort at right around 61% isn't awful.
    - Test R2 was about 1.5% better than the train R2 indicating some mild over-fitting, but nothing out of the ordinary
- P-values: 
    - We had 13 variables above the alpha level, meaning that there was a lot of reason to believe that many of these were not having an effect on our target variable
- Mean Squared Error (MSE):
    - This is where we saw the greatest effect on our model, we did not have a whole lot of errors and overall our regression line was pretty close to the actual values
    - It wasn't 0 (indicating an overfit perfect line), but there wasn't any indication of overfitting when comparing the train and test data
- JB Test:
    - We also performed very well here and showed that we were able to get very normal data out of this set, especially since it started so far off
    - This was also absolutely confirmed in our Q-Q plot
- Overall:
    - This wasn't a terrible model, and essentially can account for roughly 60% of an accurate home price (in layman's terms)
    - We didn't have any significant overfitting, and were able to get very normal data, there is more work that needs to be done to achieve a more accurate model, but we can get into that in the conclusion
    
# Conclusions

I think this is a great starting point to assist with someone in setting a selling point for their home. with this current model I was able to predict roughly 60% accurate home prices, which leaves a lot to be desired for the homeseller, but there is more work that could certainly be done to improve this further. There is a lot that goes into home selling and unfortunately, due to time constraints, we were not able to model with one of the most important sets of variables...location. I think that a lot of our errors in the modeling came as a result of not having location data and you could see that in some of the outliers. A small home in the Downtown Seattle will be far more expensive than a large home in the furthest reaches of King County. In some ways the issue with this data set was that it was too large, and some future work would be breaking it down by zipcode or geographic area (using latitude and longitude). 

# Further Work

- As I stated in the conclusions section, I think the most important aspect would be breaking down the zipcode and/or longitude and latitude to make smaller models based on more relevant data
- Another thing I would like to do is to break down and seperate some of the larger homes and larger lots
    - Many of these are likely on large plots of cheaper land, and really shouldn't be compared with homes in more desireable locations
