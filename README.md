# Big-Data-Analytics
# Airfare Prediction and Optimization with PySpark

## Project Overview

This project tackles the dynamic and complex challenge of predicting and optimizing airfare prices in the airline industry. Leveraging a massive dataset of historical flight itineraries and the power of Apache Spark (PySpark), we developed a robust data-driven solution to forecast airfares and explore potential optimization strategies for airlines. The project showcases a comprehensive data science workflow, encompassing data cleaning, feature engineering, exploratory data analysis, model building, hyperparameter tuning, and model evaluation.

## Project Goals

*   **Accurate Airfare Prediction:** Build a high-accuracy predictive model for airfares, empowering travelers to make informed booking decisions by anticipating price fluctuations.
*   **Feature Importance Analysis:** Identify the key factors that drive airfare variations, providing actionable insights into market dynamics.
*   **Relationship Exploration:** Analyze the nature of the relationships between various features and airfare, uncovering non-linear patterns and interaction effects.
*   **Optimization Strategy Exploration:** Investigate how airlines could leverage the predictive model to dynamically adjust pricing and maximize revenue based on predicted demand.

## Dataset

The project utilizes a rich dataset containing millions of flight itineraries, encompassing a wide range of information, including:

*   **Temporal Data:** `searchDate`, `flightDate`, `elapsedDays`, `travelDuration`
*   **Flight Details:** `originAirportCode`, `destinationAirportCode`, `segmentsAirlineCode`, `segmentsEquipmentDescription`, `totalTravelDistance`, `isNonStop`
*   **Pricing Information:** `baseFare`, `totalFare`
*   **Other Attributes:** `seatsRemaining`, `isBasicEconomy`, `isRefundable`, `cabinCode`

## Tools and Technologies

*   **Apache Spark (PySpark):** Distributed data processing and machine learning.
*   **Python:** Primary programming language.
*   **Pandas:** Data manipulation and analysis.
*   **Matplotlib/Seaborn:** Data visualization.
*   **PySpark MLlib:** Machine learning algorithms within Spark.
*   **Jupyter Notebook:** Interactive development and documentation.

## Key Findings and Observations

### Exploratory Data Analysis (EDA) Insights:

*   **Non-Linear Price-Time Relationship:** Contrary to a simple linear expectation, the relationship between `days_until_departure` and `totalFare` is non-linear. Fares generally decrease as the departure date approaches but can increase sharply in the last few days.
*   **Layovers Impact:** While itineraries with layovers are often cheaper, we observed instances where flights with one layover were more expensive than direct flights, suggesting the influence of route popularity or airline pricing strategies.
*   **Airport-Specific Pricing:** Significant variations in pricing strategies exist across different airports, even for similar routes, highlighting the importance of including location-based features in the model.
*   **Weekday Travel Patterns:** Flight activity peaks during weekdays, with a noticeable drop during weekends, reflecting typical business and leisure travel trends.
*   **Day of Week vs. Fare:** The analysis indicated minimal variation in average flight prices across different days of the week.
*   **Seasonality:** Airfares exhibit clear seasonal patterns, with higher prices observed during peak travel periods like summer and holidays (Fig. 5 in the report).
*   **Skewed Distributions:** The distributions of `totalDuration` and `totalFare` are right-skewed, indicating the need for data transformations (e.g., square root) to improve model performance.
*   **Correlation Highlights:**
    *   Strong positive correlations exist between `totalFare` and `travelDuration` (0.95), as well as `totalFare` and `totalTravelDistance` (0.76).
    *   A moderate negative correlation (-0.48) was found between `days_until_departure` and `fare_difference`.

### Model Performance and Feature Importance:

*   **Best Model:** The Gradient-Boosted Trees (GBT) Regressor consistently outperformed other models, achieving the lowest RMSE (12.60) and the highest R-squared (0.98).
*   **Feature Importance (from GBT):**
    *   `totalTravelDistance`
    *   `days_until_departure`
    *   `originAirport`
    *   `destinationAirport`
    *   `airline`
    *   `cabinClass`

### Model Results Summary:

| Model                 | RMSE   | R-squared |
| :-------------------- | :----- | :-------- |
| GBTRegressor          | 12.60  | 0.98      |
| RandomForestRegressor | 16.86  | 0.98      |
| Linear Regression     | 18.47  | 0.96      |
| Decision Tree Regressor | 15.25  | 0.97     |
