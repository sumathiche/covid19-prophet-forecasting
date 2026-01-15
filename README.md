### Project Overview

This project applies time-series forecasting to COVID-19 confirmed case data for India, the USA, and Brazil using Facebook Prophet.

The goal is to generate short-term forecasts and evaluate their accuracy using statistical metrics, helping demonstrate how data science can support public-health planning and early warning systems.

The notebook performs: Data cleaning and preprocessing, Trend and seasonality analysis, Country-wise modeling, Forecast generation, Accuracy evaluation (RMSE, MAE, confidence intervals).

### Why Facebook Prophet?

Facebook Prophet is chosen because it handles non-linear trends, works well with missing data, automatically detects seasonality, and is robust to sudden changes (e.g., pandemic waves).

This makes it especially suitable for pandemic time-series data.

### Dataset

The dataset contains daily COVID-19 confirmed cases for: IN India, US United States, BR Brazil. 

Each record includes date and cumulative confirmed cases.

The data is cleaned, formatted, and converted into Prophet-compatible structure (ds for date and y for cases).

### Data Preprocessing

1. **Date Parsing**

    Converts date strings to datetime objects

2. **Filtering by Country**

    Creates separate datasets for India, USA, and Brazil

3. **Handling Missing Values**

    Removes or interpolates missing records

4. **Renaming Columns**

    Prophet requires:

        ds → Date

        y → Target variable (cases)

5. **Train–Test Split**

    Historical data is split into:

        Training set

        Validation set for accuracy evaluation

### Trend Analysis

Before forecasting, the notebook visualizes:

    * Daily confirmed cases

    * Growth patterns over time

    * Differences in outbreak intensity between countries

These plots reveal:

    * Multiple waves in the USA

    * Rapid growth followed by stabilization in India

    * Volatile patterns in Brazil

This exploratory analysis helps justify why forecasting is needed.

### Prophet Model

For each country, a separate Prophet model is trained:

model = Prophet()

model.fit(data)

The model learns:

    * Long-term trend

    * Weekly and yearly seasonality

    * Irregular fluctuations

### Forecasting

The model predicts future COVID-19 cases over a short-term horizon (e.g., next 30 days).

Prophet outputs:

    * yhat → predicted cases

    * yhat_lower → lower confidence bound

    * yhat_upper → upper confidence bound

These bounds show forecast uncertainty, which is critical for public-health decision-making.

### Visualization

The notebook generates:

    * Forecast plots

    * Trend + seasonality decomposition

    * Comparison of actual vs predicted values

This allows users to:

    * See how well the model fits historical data

    * Understand future trends visually

### Model Evaluation

To measure accuracy, the notebook calculates:

1. RMSE (Root Mean Square Error)

    Measures how far predictions deviate from actual values.

2. MAE (Mean Absolute Error)

    Measures average prediction error.

    Lower RMSE and MAE indicate better performance.

These metrics are computed separately for:

* India

* USA

* Brazil

This makes cross-country comparison possible.

### Country-wise Insights

| Country | Behavior |
|---------|----------|
| India   | More stable growth after major waves |
| USA     | High volatility with multiple strong peaks |
| Brazil  | Irregular growth with frequent fluctuations |

These differences influence how Prophet fits each dataset.

### Why This Matters

Accurate COVID-19 forecasting helps:

- Hospitals prepare resources  
- Governments plan restrictions  
- Health agencies anticipate outbreaks  

This project demonstrates how **machine learning + time-series analysis** can support real-world policy decisions.

### Technologies Used

- Python  
- Pandas  
- Matplotlib  
- Facebook Prophet  
- NumPy  
- Scikit-learn (for metrics)

### How to Run

**1. Clone the repository**

git clone https://github.com/sumathiche/covid19-prophet-forecasting

**2. Install dependencies**

pip install pandas matplotlib prophet scikit-learn

**3. Open the notebook**

jupyter notebook covid19_prophet_forecasting.ipynb

### Conclusion

This project shows that Facebook Prophet can effectively model COVID-19 time-series data and provide meaningful short-term forecasts for multiple countries.

By combining forecasting with statistical validation, the project creates a reliable framework for pandemic trend analysis.


