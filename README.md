# 🚲 BikeCast – Bike-Sharing Demand Forecasting

An end-to-end machine learning project that predicts hourly bike-sharing demand in Berlin, Cologne, and Dresden based on weather, temporal, and calendar factors.

## 📌 Project Overview

Accurate demand forecasting can help bike-sharing providers optimize fleet availability, improve resource allocation, and increase customer satisfaction, thus supporting sustainable urban mobility.

We developed and deployed an interactive web application that combines historical bike-sharing data, machine learning, real-time weather forecast integration, and a cloud-hosted database to support data-driven operational planning.


## 🚀 Try the Live App

👉 **[Click here to explore BikeCast](https://bikecast-app.streamlit.app/)**

The application offers three main features:

Data Visualization: Explore how weather, time, location, and calendar factors influence bike-sharing demand.

Automatic Prediction: Forecast hourly demand up to five days ahead using weather forecasts retrieved via the OpenWeather API and automatically generated calendar features.

Manual Prediction: Estimate demand for future dates or hypothetical weather and calendar scenarios.


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
- OpenWeatherMap API


## 🔐 Configuration

The application may require:
- Database connection credentials.
- An OpenWeatherMap API key.

For security reasons, sensitive credentials and API keys should never be committed to the GitHub repository.
