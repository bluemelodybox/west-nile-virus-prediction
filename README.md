# Project 4: West Nile Virus Prediction

### Problem Statement

The intent of this project is to analyze weather data and train data to predicting the presence of the West Nile virus, for a given time, location, and species. In addition, a cost benefit analysis is done to give recommendations on where and when to spray to reduce the most amount of mosquito with the least cost. 

### General approach

- Data Cleaning
- Data Analysis and Merging
- Feature Engineering
- Modelling
- Validation
- Cost Benefit Analysis

### Data Source

[train.csv](assets/train.csv) | [test.csv](assets/test.csv) | [spray.csv](assets/spray.csv) | [weather.csv](assets/weather.csv)

### Data Cleaning

- Impute missing weather based on nearest location
- Convert object type to numeric type
- Assign mosquito species to just 4 categories with the last category as others
- Remove duplicated train data

### Data Analysis and Merging

- Merged weather to train and test data based on closest station and date

- Remove colinearity features from visualization 

### Feature Engineering

- Finding location with highest WnvPresent 

```
Coordinates with highest WnvPresent: 
Latitude   Longitude Count
41.974689  -87.890615    29
41.673408  -87.599862    15
41.954690  -87.800991    15
41.964242  -87.757639    14
41.743402  -87.731435    11
```

- Created a new feature called Dist_0 and Dist_1 fromt train and test data which are the distance away from the location of highest WnvPresent using harvesine function

- Added features like rolling mean of different periods for temperature, dewpoint and precipitation

  

### Modelling and Validation

The 2 models used are random forest and SVM

| Model         | Kaggle Score |
| ------------- | ------------ |
| Random Forest | 0.78         |
| SVM           | 0.75         |

### Cost Benefit Analysis

There are 4 recommendation options.

|        | Option 1                                                                           | Option 2                                                                                   | Option 3                                                                                      | Option 4                                                                                                     |
|--------|------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| **Method** | Spray all Wnv Positive Areas                                                       | Spray based on community areas                                                             | Spray based on distance from 3 key points                                                     | Release genetically modified mosquitos                                                                       |
| **Pros**   | Wnv positive mosquito can be dramatically reduced, thereby reducing Wnv human case | Reduce Wnv positive mosquitos in area of high risk while saving cost of spraying           | Cost\-effective method that only target high risk Wnv positive area based on train datasets   | Long term solution that can address future moquito problems, which are bound to worsen due to global warming |
| **Cons**   | Spraying all positive Wnv areas can be very costly                                 | Singular traps with only 1 Wnv positive mosquito will be missed out despite potential risk | Assume that most Wnv positive mosquitos came from these 3 areas while missing out other areas | Require a significant R&D investment cost & time to implement                                                |


### Conclusion

Based all the 10 weeks plot of spraying & Wnv positive trap of Chicago in 2013, we can conclude that spraying does have a positive effect on controlling Wnv human cases. However, as the spray strategy seems to be based on current week's trap data, the spraying areas are always lag by 1 week and made the spraying effort sometimes useless. 

Our random forest classification model is able to predict the presence of Wnv positive in each mosquito trap, with an accuracy of (score). Using the classification model, we can predict next week's Wnv presence based on this week's data and plan the spraying strategy with the 4 options given above. 

More information would be required to make the model more accurate at predicting, such as 

1) Number of mosquito in test dataset

2) Number of Wnv human cases and area of infection

3) More spray area data other than 2011 and 2013

Nevertheless, we conclude that our random forest classificaion model has performed up to expectation in predicting Wnv presence in Chicago. 