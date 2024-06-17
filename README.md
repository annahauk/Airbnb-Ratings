# PREDICTING RATING SCORE ON AIRBNB NYC DATA🚀

For my final ML project for Cornell Tech, I used NYC Airbnb 2020[^1] data to predict the rating scores of different properties. In addition to using common ML packages, I also included *accuracy score* and *roc_auc_score* and *RMSE* to 
analyze our regression models: ***Linear, Decision Tree, and Random Forest***. 

## **Our Objectives:**
- [ ] Exploratory Data Analysis
- [ ] Data Cleaning
- [ ] Model Creation
- [ ] Hyperparameter Tuning
- [ ] Performance Comparison

> [!NOTE]
> Our data contains 28022 rows and 50 columns.


## **EDA**
When first looking at our data, you can see that there are a lot of object-type columns with information like the title of the place, reviews (comments), host info, etc. You could use *NLP sentiment 
analysis* in the future to do rating predictions; more positive buzzwords would contribute to a higher predicted rating.

I did look at the 'host_total_listings_count' column for how many unique values there were(to gauge the variance and decide whether it would be as influential). I did this cause if there are hosts with more listings, 
they would probably have higher ratings since they're more successful.
I also looked at the 'host_location' column and found 1,364 unique values (variations on the NYC area) but, I found the 'neighbourhood_group_cleansed' column was the 5 boroughs of NYC so that played into the decision
of choosing whether to drop that column or not.

- [X] Exploratory Data Analysis
- [ ] Data Cleaning
- [ ] Model Creation
- [ ] Hyperparameter Tuning
- [ ] Performance Comparison

## **Data Cleaning**
In this section, I will clean my data by:
+ Feature selection for relevant columns
+ Addressing missingness, such as replacing missing values with means
+ Renaming features and labels
+ performing winsorization
+ Performing one-hot encoding on categorical features (feature extraction)

Using the information from the EDA and some further data exploration, I selected 31 columns of the 50. I didn't get a chance to see whether you get better results with more/less feature 
and I never learned any methods with mathematical feature selection techniques. 

There were columns about availability, number of reviews, review scores (based on aspects of the stay), and numerical measures of the host that could influence a rating. For example, less availability correlates with
a more popular/high-rated property, more reviews -> more stays -> high-rating and so on.

For missing/NaN values, there were only float64 columns. I just replaced the NaNs with the mean using .mean() and .fillna().

I renamed the 'neighbourhood_group_cleansed' to 'neighbourhood' for ease of reference. Then, I one hot encoded that column since there were only 5 unique values: *Brooklyn, Manhattan, Bronx, Queens, Staten Island*.

I windsorized the price column because I thought the upper quartile priced properties might have an inherently higher rating since it might be more 'luxurious' and reduced any impact outliers would have.

- [X] Exploratory Data Analysis
- [X] Data Cleaning
- [ ] Model Creation
- [ ] Hyperparameter Tuning
- [ ] Performance Comparison


## **Model Creation**
I chose regressor models because we are predicting a continuous variable (can take values from 0.00-5.00) and we want to be able to estimate the strength multiple variables have on a dependent variable; in our case,
the property ratings.

I split my data into y = df['review_scores_rating'], X = df_rate.drop(columns = ['review_scores_rating'], axis =1) and used train_test_split with a test_size of .3. Then, I decided to use a linear regressor,
a Decision Tree Regressor, and a Random Forest Regressor. 

- [X] Exploratory Data Analysis
- [X] Data Cleaning
- [X] Model Creation
- [ ] Hyperparameter Tuning
- [ ] Performance Comparison


## **Hyperparameter Tuning**

TODO 
I analyzed the alphas for linear regression.

I performed grid-search on the Decision Tree Regressor to find the best parameters.

I tested different n_estimatos for the random forest regressor.

- [X] Exploratory Data Analysis
- [X] Data Cleaning
- [X] Model Creation
- [X] Hyperparameter Tuning
- [ ] Performance Comparison


## **Performance Comparison**
TODO
- [X] Exploratory Data Analysis
- [X] Data Cleaning
- [X] Model Creation
- [X] Hyperparameter Tuning
- [X] Performance Comparison

## **Recap**
Overall, even though the cause for the project was for the final assignment, I combined all that I learned and discovered what techniques work and others that don't. There are some things I would like to experiment with:
+ Changing the number of columns
+ Changing which columns are used
+ Using NLP for sentiment analysis in columns like 'amenities' and 'reviews'
+ Trying more models like ensemble
+ Doing more hyperparameter tuning

Altogether, this data can be used by the company, Airbnb, or the host to discover what leads to higher ratings for properties and use that for advertisements and personal improvements. This can be extended to all sorts
of scenarios with a reviewing system.

### Thanks for reading and go ahead and check out my other repositories if you're interested in my work!
[^1]: Data found in the repository under "airbnbListingsData.csv.zip".
