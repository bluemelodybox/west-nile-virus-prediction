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

There are 3 recommendation options.

<u>Option 1:</u>  Spray on all infected area

<u>Option 2:</u>  Spray based on community area

<u>Option 3:</u>  Spray on location closest to the highest infected area

### Conclusion

From our analysis we recommend spraying on all only if we have the budget