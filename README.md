# 🚲 Seoul Bike Sharing Demand Prediction

[![forthebadge](https://forthebadge.com/images/badges/made-with-python.svg)](https://forthebadge.com) [![forthebadge](https://forthebadge.com/images/badges/not-a-bug-a-feature.svg)](https://forthebadge.com)

<img src=https://user-images.githubusercontent.com/63778269/148300465-182486bc-4102-4370-9a8f-0e81a1f76567.jpg width=400/>

Bike sharing is one of the ways to reduce urban traffic. It also reduces air pollution by reducing the number of cars on the road. The bike sharing system is a new generation of traditional bike rental systems, and the entire process has been automated. Users can borrow bicycles for free or for a fee and return them to another place.

The hypothesis in the research is that the bike sharing is highly related with the time of the day, season, and weather conditions. The research will try to predict the bike shares in the future. We are going to try to understand the factors on which the demand for these shared bikes depends.

This dataset contains the hourly and daily count of rental bikes between in 2017-2018 in in Seoul with the corresponding weather and seasonal information.

## Data set

Currently Rental bikes are introduced in many urban cities for the enhancement of mobility comfort. It is important to make the rental bike available and accessible to the public at the right time as it lessens the waiting time. Eventually, providing the city with a stable supply of rental bikes becomes a major concern. The crucial part is the `prediction of bike count` required at each hour for the stable supply of rental bikes.

The dataset contains weather information **(Temperature, Humidity, Windspeed, Visibility, Dewpoint, Solar radiation, Snowfall, Rainfall)**, the number of bikes rented per hour and date information.

We have `8760` instances with `14` different variables to work on.

### Variables

* **Date** - year-month-day
* **Rented Bike count** - Count of bikes rented at each hour
* **Hour** - Hour of he day
* **Temperature** -Temperature in Celsius
* **Humidity** - %
* **Windspeed** - m/s
* **Visibility** - 10m
* **Dew point temperature** - Celsius
* **Solar radiation** - MJ/m2
* **Rainfall** - mm
* **Snowfall** - cm
* **Seasons** - Winter, Spring, Summer, Autumn
* **Holiday** - Holiday/No holiday
* **Functional Day** - NoFunc(Non Functional Hours), Fun(Functional hours)

<br/>
<br/>

## Content of the notebook

### 1.Data analysis

First of all,I try to read and understand the data set to know with what i'm dealing with. I look at the statistics of our features. I check if there are any duplicated or NaN values or values that we may need to ged rid of.

Then I use the seaborn and pyplot library to make some vizualisations 


<p align="center"> 
  <img src=https://user-images.githubusercontent.com/63778269/148302308-76b2ae98-69df-4160-92e4-5724d8a08809.png width=600/>
</p>
<p align="left"> 
  <img src=https://user-images.githubusercontent.com/63778269/148302249-4235a177-35c9-409b-b2dd-dadd588a0305.png height=300/>
  <img src=https://user-images.githubusercontent.com/63778269/148302361-2c89f117-5e6a-439a-873e-dc4cb87c8d18.png height=250/>
</p>

### 2.Preprocessing

Then i encode the categorical columns into integer values.

I look at what variables i can create.

I use the Gradient Boosting Regressor model to calculate the import for each attribute in the dataset. This model construct boosted trees, and the most important features are the ones which help the most constructing the boosted decision trees, the most useful and valuable features.

I split the dataset into training and testing set.

I chose to standardize the values because it more efficient to compare measurements that have differents units.

### 3.Models and predictions

I tried differents models to try to have the best score (the best r2 squared) . I used the GridSearchCV method seen in class to optimize my hyperparameters.

The results obtained are pretty satisfying, the tree first ones are very closed from eachother with a score of :
- LightGBM : 0,8838
- XGBRegressor : 0,8822
- RandomForestRegressor : 0,8808

![image](https://user-images.githubusercontent.com/63778269/148303479-59401654-9a72-4195-a6c2-0beb35f61f2e.png)
![image](https://user-images.githubusercontent.com/63778269/148303539-1b4fae48-65c8-4448-99a9-27ff14e067dd.png)

With the LightGBM model the best achieved RMSLE score is 219.367 for a R² equal to 0.88.

We arrived at a very decent model for the the demand for shared bikes with the significant variables. Our model is capable to capture the trend and the extreme values, as we can see on the second plot, which is a really good thing. So, we can say that the overall perfomance is good.

### 4. API - Streamlit

Finally, i have made an API with StreamLit which allows you to select (with sliders and element boxes) the values of the time and weather conditions and predict the number of rented bikes necessary.



<br/>
<br/>

## Note

The python code is in english so do not hesitate to contact me if you want more details in French.

### Relevant Papers / Citation Request

>[1] **Sathishkumar V E, Jangwoo Park, and Yongyun Cho**. _'Using data mining techniques for bike sharing demand prediction in metropolitan city.'_ Computer Communications, Vol.153, pp.353-366, March, 2020
>
>[2] **Sathishkumar V E and Yongyun Cho**. _'A rule-based model for Seoul Bike sharing demand prediction using weather data'_ European Journal of Remote Sensing, pp. 1-18, Feb, 2020


### Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

<br/>
<br/>
