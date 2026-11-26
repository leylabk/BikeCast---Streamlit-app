# 🚲 BikeCast – Forecasting Bike-Sharing Demand 

Welcome to our machine learning project that predicts hourly bike-sharing demand!  

It covers Berlin, Cologne, and Dresden, and uses weather and calendar information to evaluate how many bikes will be needed on a given day at a given hour.

## 📌 Project Overview

With climate crisis becoming an increasingly urgent issue, it is the right time to think about the ways we can reduce our impact on the environment 🌱

**[UN Act Now](https://www.un.org/en/actnow/ten-actions)** lists **biking** among 10 things that each of us can do to move towards this goal, but biking does come with its difficulties:               
A comfortable bike is quite expensive, it might get stolen, and it might require some technical skills should anything break down. Not to mention a miserable biking experience in the rain 🌧️

**Bike-sharing companies** help us with many of these difficulties: A shared bike does not require a big one-time investment, it does not get stolen from you personally, and you don't need to worry about its maintenance. Rain is still gonna be there though! 

What can be really annoying about a bike-sharing service, however, is when you really need a bike but so do all of your neighbours - and there are **no free bikes available**.

To help solve this problem, we designed **an interactive web app** that would allow **bike-sharing companies** to **predict the demand** and prepare enough bikes, so that their customers do not get stranded.

Our app predicts bike-sharing demand in **Berlin, Cologne, and Dresden**, based on **weather forecasts** (*Is it cold and rainy or sunny and warm?*), **time** (*Is it the dead of night or a busy commuting hour?*) and **calendar** factors (*Is it July or December? It is a working day or not?*)

Behind our app is **a machine learning model** (CatBoost, see below) trained on historical bike-sharing and weather data. It uses **real-time weather forecasts** to make bike demand predictions, and **a cloud-hosted database** to display bike demand trends.

<p align="center">
  <img src="images/bikecast_homepage.png" width="80%" alt="App homepage">
  <br>
  <em>App homepage</em>
</p>


## 🚀 Try Our Web App

👉 **[Click here to explore BikeCast](https://bikecast-app.streamlit.app/)**

The application offers three main features:

**Data Visualization**: Explore how weather, time, location, and calendar factors influence bike-sharing demand.

**Automatic Prediction**: Predict hourly demand up to five days ahead using weather forecasts retrieved via the OpenWeather API and automatically generated calendar factors.

**Manual Prediction**: Predict hourly demand for future dates or hypothetical weather and calendar scenarios by manually entering all the factors yourself.


## 📊 Data

### Dataset

We trained our machine learning model on historical bike-sharing records from Berlin, Cologne, and Dresden covering August 2022 – July 2023, with 1.2 to 2.5 million trips per city.

We aggregated the records of individual bike-sharing trips to hourly bike demand, and added historical weather and calendar data to each hour. This resulted in a modeling dataset of ≈22,000 observations.

**Target of prediction:**
- **Shared bike trips**: Number of bike-sharing trips started per hour. It represents the demand for ready-to-use bikes that a company needs to prepare.

**Predictor factors:**
- **Location:** City.
- **Calendar factors:** Month, hour of the day, working day (vs. holiday/weekend), and school holidays (*Schulferien* vs. regular school periods).
- **Weather factors:** Weather conditions (clouds, clear, rain, snow, mist, drizzle or fog), temperature, humidity, wind speed, amount of rainfall and snowfall during the previous hour.

### Data Sources

- **Bike-Sharing Data:** Historical bike-sharing records obtained from the [European Bike Sharing Dataset](https://github.com/tumftm/european-bike-sharing-dataset)¹.
- **Weather Data:** Historical weather records collected using the [OpenWeather Marketplace](https://openweathermap.org/marketplace), including temperature, humidity, wind speed, rainfall, and snowfall.
- **Calendar Data:** Working day information generated using `holidays` library in Python; school break information taken from the [Schulferien website](https://www.schulferien.org/deutschland/ferien/).

## 🤖 Machine Learning & Model Performance

The final model uses **CatBoost**, a gradient boosting algorithm, to capture complex non-linear relationships between bike-sharing demand and the predictor factors.

The model was evaluated on unseen historical data.

| Metric                            | Score |
| --------------------------------- | ----- |
| R² (coefficient of determination) | 0.93  |

The model explains **93% of the variance in hourly bike-sharing demand** in the evaluation dataset. This means it captures most of the patterns behind why the number of bike rentals changes from one hour to another. The remaining 7% may be influenced by other factors that are not included in our model.

Before selecting our final model, we tested 6 other ones - you can see their results below. A more detailed overview of the model selection process (including hyperparameter tuning) can be found in *Data_Processing_and_Modelling* > *predictive_modelling.ipynb*.

<p align="center">
  <img src="images/model_comparison.png" width="55%" alt="App homepage">
  <br>
  <em>ML model comparison</em>
</p>

## 📂 Repository Structure

```text
├── .gitignore
├── README.md
├── app_cloud_db.py
├── bike.png
├── bikecast_qr.png
├── catboost_categories_spline.pkl
├── catboost_model_spline.pkl
├── functions_cloud_db.py
├── graphs.py
├── requirements.txt
└── school_holidays.py
```

## 📄 File Descriptions

| File | Description |
|---|---|
| `.gitignore` | Specifies files and directories that Git should ignore. |
| `README.md` | Contains project documentation and setup instructions. |
| `app_cloud_db.py` | Main Streamlit application for bike-sharing demand prediction with cloud database integration. |
| `bike.png` | Contains the bike image used in the application interface. |
| `bikecast_qr.png` | Contains a QR code that provides quick access to the BikeCast application via GitHub. |
| `catboost_categories_spline.pkl` | Saved CatBoost model for categorical features. |
| `catboost_model_spline.pkl` | Saved CatBoost model using spline-based features. |
| `functions_cloud_db.py` | Contains helper functions for data processing, weather data retrieval, database operations, and predictions. |
| `graphs.py` | Contains functions for generating and displaying data visualizations. |
| `requirements.txt` | Lists the Python dependencies required to run the project. |
| `school_holidays.py` | Contains functionality for handling school holiday information. |

## 🛠️ Technologies Used

- Python
- Streamlit
- CatBoost
- Pandas
- Scikit-learn
- MySQL
- Railway (cloud-hosted MySQL database)
- OpenWeather API


## 🔐 Configuration

The application may require:
- Database connection credentials.
- An OpenWeatherMap API key.

For security reasons, sensitive credentials and API keys should never be committed to the GitHub repository.
