# Introduction

For our final project, we sought to better understand the drivers of rental price for various real estate properties across the US. To that end, we selected five datasets.

1. The primary dataset, termed `real_estate_dataset_df`, comprises an array of variables such as rental pricing, geographic loaction, the number of available bedrooms & bathrooms, amongst other pertinent attributes of rental listings.
2. The second dataset, `crime_data_df`, encompasses crime rate statistics across all U.S. states and territories, serving as a proxy for the regional safety.
3. The third dataset, `state_gdp_df`, encapsulates the Gross Domestic Product (GDP) per capita for each state, which we posited as an indicator of the local economic status.
4. The fourth dataset, `weather_score_df`, quantifies the climatic livability, particularly temperature.
5. The final dataset, `spending_merged_df`, conveys the government expenditures across various sectors within each state for the year 2022.

Aggregating, pre-processing these results and merging them with our previous dataset, we are able to develop a holistic understanding of both the intrinsic factors (e.g., room type, facilities available etc) and external factors (crime levels, weather condition, etc.) that drive rental price.

These results are detailed below in my notebook. Above or beneath each relevant visualization or finding, we take care to explain the motivation for the analysis, the key takeaways, and how our findings serve to inform our understanding of the relationships between various internal and external factors and listing price.

I hope you find our findings insightful, and  I am eager to answer any questions you may have.

> You can straightly run the `.ipynb` file without downloading any extra datasets in **Google Colab**. If you want to check out the datasets, please refer to the `Datasets` folders.

# Hightlights

1. Detailed comments and markdowns.
2. Web Scraping using `XPath.`
3. Advanced and interactive visualization.
4. ML models (Linear Regression, Random Forest, XGBoost & FNN) with defined tuning and great outcomes.

# Conclusion

## Main takeaways

1. As the baseline model, linear regression apprears to predict the rental price better when we dropped those outliers, without performing PCA. The $R^2$ value of this model is around **3.89**, indicating linear regression cannot predict the rental price very well.
2. The best model was the RandomForestRegressor which produced a test $R^2$ value of **0.81**, following by the XGBoost Regressor performing equally well with test $R^2$ value of **0.80**.
3. The Neural Network Model however performed less aplausible on our data. We tried different node number of hidden layers and different parameters of adam optimizer. The best $R^2$ value we achieved is around **0.53**. However, with a growing trend, we believe the fnn model will become increasingly better with a larger epoch number and further hyperparameter tuning.
4. We see that the factors that most influence Real Estate Prices (from the XGBoost and RandomForest outputs) somewhat align with the results from our covariance matrix generated from dataset without outliers during the EDA stage.
5. Most influential factors as we can see from the XGBoost model's output :

-`Spending on Police`,

-`GDP`

-`bath`

-`laundry_options`

6. Most influential factors as we can see from the RandomForest model output:

-`Spending on Police`

-`sqfeet`,

-`lat`

-`laundry_options`

-`parking_options`

-`bath`

7. From both the model outputs we can conclude that among the social economic factors, Spending on Police (which can be used to represent the safety of the state) and GDP of the state are the most influential features
8. Among the house properties, laundry options, parking_options and bath seem to be the most influential factors in deciding the rental prices.

## Evaluating the Performance of Models

-**Linear Regression**:

  Because we have datasets with multifaceted relationships and variables influencing rental prices (such as crime rates, GDP, weather conditions), Linear Regression's assumption of linearity limits its ability to capture these complex interactions which is probably why we have a low R^2 score.

-**RandomForestRegressor**:

  This model excels in handling diverse datasets with complex and non-linear relationships, like the variety of complex relationships found in our real estate data encompassing economic, geographic, and socio-demographic factors. Its ensemble approach effectively captures the multifaceted nature of such data.

-**XGBoost Regressor**:

  Also particularly suited for datasets with mixed types of variables and intricate patterns, XGBoost efficiently manages the diverse range of features from real estate, economic, and environmental datasets, leveraging its gradient boosting mechanism to improve predictive accuracy.

-**Neural Network Model**:

  While theoretically capable of modeling complex, non-linear relationships in multifaceted datasets, its performance heavily relies on appropriate network architecture and hyperparameter tuning. This is something we can consider as future work to see if trying out different architecture and tuning will imporve results.

## Future Work

1. Experimenting more with Neural Network architecture and hyperparameters to see if it can improve model performance.
2. Considering a smaller geographic location like county or region to better account for region specific social economic factors like Crime Rate, Education, Hospitals, Weather etc.
3. Trying different business rules for attributes to see which one works the best for our data and consulting domain experts.
