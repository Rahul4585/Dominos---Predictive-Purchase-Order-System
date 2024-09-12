<div align="center">

# 🍕 Dominos - Predictive Purchase Order System

</div>

<div align="center">

[![](https://img.shields.io/badge/Python-FFD43B?style=for-the-badge&logo=python&logoColor=darkgreen)](https://www.python.org)
[![](https://img.shields.io/badge/scikit_learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/stable/)
[![](https://img.shields.io/badge/Numpy-777BB4?style=for-the-badge&logo=numpy&logoColor=white)](https://numpy.org)
[![](https://img.shields.io/badge/Pandas-2C2D72?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org)
[![](https://img.shields.io/badge/Plotly-239120?style=for-the-badge&logo=plotly&logoColor=white)](https://plotly.com)
[![](https://img.shields.io/badge/Machine%20Learning-FF6F00?style=for-the-badge&logo=google-cloud&logoColor=white)](https://www.google.com/)

</div>

<div align="center">
<img src="https://github.com/user-attachments/assets/9bbc3acc-86f2-4e9e-9dbd-d5399264440e" width="800"/>
</div>

## 📈 Problem Statement

This project focuses on optimizing Domino's inventory management by building a predictive system that forecasts pizza sales and generates purchase orders for ingredients. By leveraging historical sales data, the goal is to develop a model that accurately predicts future sales, allowing Domino's to order the right amount of ingredients, minimizing waste, and preventing stockouts.

---

## 🎯 Objective:
- Develop a predictive model to forecast pizza sales.
- Create a purchase order system that calculates the required quantities of ingredients based on the sales forecast.
 
---

## 💡 Business Use Cases

-  **Inventory Management**: Ensuring optimal stock levels to meet future demand without overstocking.
-  **Cost Reduction**: Minimizing waste and reducing costs associated with expired or excess inventory.
-  **Sales Forecasting**: Accurately predicting sales trends to inform business strategies and promotions.
-  **Supply Chain Optimization**: Streamlining the ordering process to align with predicted sales and avoid disruptions.

---

## 🛠️ Approach

### I. 🔍 Data Preprocessing and Exploration

- **Data Cleaning**: Remove any missing or inconsistent data entries, handle outliers, and format the data appropriately.
- **Exploratory Data Analysis (EDA)**: Analyze sales trends, seasonality, and patterns in the historical sales data. Visualize the data to identify significant features.

### II. 🔮 Sales Prediction

- **Feature Engineering**: Create relevant features from the sales data, such as day of the week, month, promotional periods, and holiday effects.
- **Model Selection**: Choose an appropriate time series forecasting model (e.g., ARIMA, SARIMA, Prophet, LSTM, Regression Model).
- **Model Training**: Train the predictive model on the historical sales data.
- **Model Evaluation**: Use metric Mean Absolute Percentage Error (MAPE) to evaluate model performance.

### III. 📦 Purchase Order Generation

- **Sales Forecasting**: Predict pizza sales for the next week using the trained model.
- **Ingredient Calculation**: Calculate the required quantities of each ingredient based on the predicted sales and the ingredient dataset.
- **Purchase Order Creation**: Generate a detailed purchase order listing the quantities of each ingredient needed for the predicted sales period.

---
