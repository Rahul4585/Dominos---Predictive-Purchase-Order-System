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

- To Develop a predictive model to forecast pizza sales.
- To Create a purchase order system that calculates the required quantities of ingredients based on the sales forecast.
 
---

## 🔍 Dataset Overview

The project involves two datasets: **Pizza Sales** and **Pizza Ingredients**. The **Pizza Sales Dataset** comprises 48,620 entries, each detailing an individual sale. This includes information such as `pizza_id` (a unique identifier for the sale), `order_id` (linking to a specific order), `pizza_name_id` (identifying the type of pizza), `quantity` (number of pizzas sold), `order_date` and `order_time` (when the sale occurred), `unit_price` and `total_price` (pricing details), as well as `pizza_size` and `pizza_category` (size and type of pizza). This dataset offers a thorough view of sales, covering pricing, timing, and pizza characteristics. The **Pizza Ingredients Dataset** consists of 518 entries that describe the ingredients for various pizzas. It includes `pizza_name_id` (a unique identifier for each pizza), `pizza_name` (name of the pizza), `pizza_ingredients` (list of ingredients), and `Items_Qty_In_Grams` (the quantity of each ingredient used). This dataset provides detailed insights into the composition of each pizza and the amounts of ingredients required.

You can download the dataset from the following link:

[Download pizza_sales Dataset](https://docs.google.com/spreadsheets/d/1gB2O_G9G_ym41h-Wra3k4VDHHYVONh3jfkEBLzAOuUI/edit?usp=sharing)

[Download pizza_ingredients Dataset](https://docs.google.com/spreadsheets/d/13h0bdBCgcnf7kduth_5ci1pMytzXc02H57Ms30Xg5AA/edit?usp=drivesdk)

---

## 📊 Metrics

- [__Mean Absolute Percentage Error__](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.mean_absolute_percentage_error.html): Used to evaluate the accuracy of forecasting models. It measures the average absolute percentage error between the predicted values and the actual values.

---

## 💡 Business Use Cases

-  **Inventory Management**: Ensuring optimal stock levels to meet future demand without overstocking.
-  **Cost Reduction**: Minimizing waste and reducing costs associated with expired or excess inventory.
-  **Sales Forecasting**: Accurately predicting sales trends to inform business strategies and promotions.
-  **Supply Chain Optimization**: Streamlining the ordering process to align with predicted sales and avoid disruptions.

---

## 🛠️ Approach

### I.  Data Preprocessing

**Data Cleaning** ensures the dataset's accuracy and consistency through:

- **Handling Missing Data**:
  - Detected missing values.
  - Replaced missing values using mean, median, mode, or placeholders.
  - Removed columns or rows with excessive missing data if necessary.

- **Removing Inconsistent Data**:
  - Checked for format consistency and valid ranges.
  - Fixed inconsistencies, such as standardizing text and correcting typos.

- **Handling Outliers**:
  - Identified outliers using statistical methods or visualizations.
  - Removed, transform, or categorize outliers based on their impact.

### II.  Exploratory Data Analysis (EDA)

**Exploratory Data Analysis (EDA)** discovers patterns, relationships, and anomalies in the data.

### i) Distribution of Pizza Names:
- It shows the distribution of the top 15 pizza names in the dataset. This visualization helps identify the most or least ordered pizzas.
- Here y-axis represents different pizza names, and the bars represent the count of orders per pizza.

<div align="center">

![image](https://github.com/user-attachments/assets/40973c61-565b-423c-900d-d938e6e7bc34)

</div>

### ii) Distribution of Pizza Categories:
- It shows how pizza orders are distributed across different categories (e.g., vegetarian, meat-lovers, etc.). This gives insight into customer preferences by category.
- Here y-axis represents pizza categories, and the bars represent the number of orders for each category.
   
<div align="center">

![image](https://github.com/user-attachments/assets/572df784-a366-4952-b558-66a802452b10)

</div>

### iii) Sales Trends Over Time:
- The `order_date` column is converted into a datetime format and then groups the sales by date to generate a time series plot.
- Here the line plot displays daily pizza sales (quantity sold) over time, which helps in spotting trends, seasonality, or spikes in sales.

<div align="center">

![image](https://github.com/user-attachments/assets/b5d12af5-9d27-40be-8f90-c68eebcc8a52)

</div>

### iv) Top 15 Ingredients by Total Quantity Used:
- Here the bar plot shows the top 15 pizza ingredients used, based on the total quantity in grams. This helps to determine the most commonly used ingredients.
- The x-axis represents the total quantity used in grams, while the y-axis lists the ingredients.

<div align="center">

![image](https://github.com/user-attachments/assets/11ed12b9-2a05-4feb-811c-0bd57f83c2f8)

</div>

### v) Top 15 Pizzas by Total Quantity of Ingredients Used:
- Another bar plot displays the top 15 pizzas based on the total amount of ingredients (in grams) used. This gives insights into which pizzas require more ingredients, possibly hinting at their complexity or popularity.
- Here x-axis represents the total quantity of ingredients in grams, and the y-axis shows the pizza names.

<div align="center">

![image](https://github.com/user-attachments/assets/a7169ff4-d0c5-4543-bc6e-6f61bf5658eb)

</div>

### III. Sales Prediction

Sales Prediction involves **Time Series Forecasting** , a technique used to predict future values based on historical data collected over time. The process includes the following steps:

#### i) Feature Engineering

Created new variables from the raw sales data to improve the model’s performance like:

- **Day of the Week**: Extracted the day of the week from the sales date to capture weekly variations.
- **Month**: Extracted the month from the sales date to account for monthly trends and seasonal patterns.
- **Holiday Effects**: Identified and included features for holidays or special events that can impact sales patterns.

#### ii) Model Selection

Model Selection involves choosing the most suitable forecasting model for our sales data:

- [__ARIMA (AutoRegressive Integrated Moving Average)__](https://www.statsmodels.org/stable/generated/statsmodels.tsa.arima.model.ARIMA.html): Captures trends and autocorrelations in non-seasonal data.
- [__SARIMA (Seasonal ARIMA)__](https://www.statsmodels.org/dev/generated/statsmodels.tsa.statespace.sarimax.SARIMAX.html): Extends ARIMA to handle seasonality.

#### iii) Model Training

Model Training involves fitting the chosen model to historical sales data:

- Splited the data into training and test sets to evaluate model performance.
- Trained the model on the training set by adjusting parameters to minimize prediction errors.
- Optimized model performance by tuning hyperparameters using techniques like cross-validation or grid search.

#### iv) Model Evaluation

Model Evaluation assesses the accuracy and performance of the trained model using:

- **Mean Absolute Percentage Error (MAPE)**:
  - Measures the accuracy of forecasts by calculating the average percentage error between the predicted and actual values. It provides a percentage-based metric to assess forecast performance.
  - **Formula**:
    ```text
    MAPE = (1/n) * Σ |(A_i - F_i) / A_i| * 100
    ```
    - `A_i` = Actual value
    - `F_i` = Forecasted value
    - `n` = Number of observations
  - A lower MAPE value indicates better forecast accuracy, giving a clear percentage representation of the error relative to the actual values.

### IV. Purchase Order Generation

In this stage, the process begins with sales forecasting, where the trained model is used to predict pizza sales for the upcoming week. Following this, the ingredient calculation phase involves determining the required quantities of each ingredient based on the predicted sales and the existing ingredient dataset. Finally, a purchase order creation step is undertaken to generate a comprehensive purchase order that details the quantities of each ingredient needed for the forecasted sales period. This ensures that inventory levels are appropriately adjusted to meet the anticipated demand.

<div align="center">

<img width="950" alt="image" src="https://github.com/user-attachments/assets/46354248-bc8b-4a0d-8a40-45b03b5f0dbb">


</div>

---

## 🧩 Model Comparison

This graph compares the actual pizza sales with the predictions from both the ARIMA and Best SARIMA models over a specific time period.The visualization helps assess the performance of the ARIMA and SARIMA models by showing how closely their predictions align with actual sales data. X-axis (Weeks) represents time, with each point corresponding to a specific week in the test dataset and Y-axis (Sales Quantity) represents the number of pizzas sold.

<div align="center">

![image](https://github.com/user-attachments/assets/61ff8b20-fd83-4fca-bd37-4b0338edde05)

</div>

This comparison allows us to evaluate how closely each model's predictions match the actual sales data. Additionally, the visual representation helps in identifying potential issues such as overfitting or underfitting, offering valuable insights into the models' performance. Based on how well the predictions from each model align with the actual data, we can determine whether the SARIMA or ARIMA model is more suitable for forecasting future sales.

<div align="center">

| __Forecasting Methods__ | __Mean Absolute Percentage Error (MAPE)__ |
| :-: | :-: |
| [__1. ARIMA__](https://statsmodels.org/stable/generated/statsmodels.tsa.arima.model.ARIMA.html) | 0.19 |
| [__2. SARIMA__](https://www.statsmodels.org/stable/generated/statsmodels.tsa.statespace.sarimax.SARIMAX.html) | 0.20 |

</div>

The comparison of forecasting methods based on the Mean Absolute Percentage Error (MAPE) shows that the ARIMA model slightly outperforms SARIMA, with a lower MAPE value of 0.19 compared to 0.20 for SARIMA. This indicates that **ARIMA** provides marginally more accurate predictions in this context.

---

## 🏆 Results

The results include accurate sales predictions, where the forecasting model delivers precise estimates of pizza sales for the upcoming period. This enables more effective planning and inventory management. Additionally, a comprehensive purchase order is generated, which outlines the exact quantities of each ingredient required based on the forecasted sales. This ensures that all necessary ingredients are available to meet the predicted demand, supporting smooth operations and efficient stock management.

---
