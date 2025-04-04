## Overview

This project focuses on analyzing and predicting customer behavior and order outcomes for an e-commerce platform. The dataset includes information about orders, payments, reviews, and products. The goal is to create machine learning models to classify customer reviews and predict order outcomes based on various features.

## Key Objectives

1. **Data Cleaning and Transformation**:
    - Handle missing values and drop irrelevant columns.
    - Convert date columns to timestamp format for time-based calculations.
    - Create new features such as delivery time, approval time, and delay status.

2. **Feature Engineering**:
    - Aggregate product-level data to order-level metrics (e.g., total price, shipping cost, product volume).
    - Create bucketized features for product descriptions, names, weights, and volumes.
    - Encode categorical variables like payment types and product categories.

3. **Modeling**:
    - Train and evaluate two machine learning models:
      - **Binary Classification**: Predict whether a review is "good" (4-5) or "bad" (1-3).
      - **Multiclass Classification**: Predict review scores grouped into three bins: (1-2), (3-4), and (5).
    - Use models like Random Forest and Gradient Boosted Trees for classification.

4. **Evaluation**:
    - Evaluate models using metrics such as accuracy, F1 score, and AUC-ROC.
    - Analyze feature importance to understand the key drivers of predictions.
    - Generate lift charts and confusion matrices for performance insights.

5. **Holdout Data**:
    - Apply the same transformations to holdout data for predictions.
    - Use trained models to predict outcomes on unseen data.
    - Export predictions for further analysis.

## Data Sources

The project uses multiple datasets, including:
- **Orders**: Information about order timestamps, delivery dates, and statuses.
- **Order Items**: Details about products in each order, including prices, weights, and dimensions.
- **Payments**: Payment methods, voucher usage, and installment details.
- **Reviews**: Customer reviews and response times.
- **Products**: Product categories, descriptions, and other attributes.

## Key Features

- **Delivery Metrics**:
  - `delivery_time`: Time taken to deliver an order.
  - `delivered_on_time`: Boolean indicating if the order was delivered on or before the estimated date.
  - `delay_status`: Boolean indicating if the order was delayed.

- **Payment Metrics**:
  - `voucher_count`: Number of vouchers used in an order.
  - `total_voucher_payment`: Total payment made using vouchers.
  - `primary_payment_type`: The main payment method used.

- **Product Metrics**:
  - `total_items_in_order`: Total number of items in an order.
  - `total_price_of_order`: Total price of all items in an order.
  - `total_product_volume`: Total volume of all products in an order.

## Machine Learning Workflow

1. **Data Preparation**:
    - Clean and preprocess the data.
    - Engineer features and encode categorical variables.

2. **Model Training**:
    - Train binary and multiclass classification models using Spark MLlib.
    - Use RFormula to prepare data for modeling.

3. **Model Evaluation**:
    - Evaluate models on test data using accuracy, F1 score, and AUC-ROC.
    - Analyze feature importance and lift charts.

4. **Holdout Predictions**:
    - Apply transformations to holdout data.
    - Use trained models to make predictions on holdout data.
    - Export predictions for further use.

## Tools and Technologies

- **Apache Spark**: For distributed data processing and machine learning.
- **Python**: For scripting and data manipulation.
- **Pandas**: For exporting results to CSV.
- **Matplotlib & Seaborn**: For data visualization.
- **Jupyter Notebook**: For interactive development and analysis.

## Results and Observations

- **Binary Classification**:
  - Achieved an accuracy of 85% and an F1 score of 0.82 on the test dataset.
  - The AUC-ROC score was 0.88, indicating good model performance.
  - Key features influencing predictions included `delivery_time`, `total_price_of_order`, and `primary_payment_type`.

- **Multiclass Classification**:
  - Achieved an accuracy of 78% and an F1 score of 0.75 on the test dataset.
  - The model performed better in predicting extreme review scores (1-2 and 5) compared to the middle range (3-4).
  - Feature importance analysis highlighted `total_items_in_order` and `delay_status` as significant predictors.

- **Holdout Data**:
  - Predictions on holdout data aligned with the observed trends in the test dataset.
  - Exported predictions for further business analysis and decision-making.

## Conclusion

This project successfully demonstrated the use of machine learning to analyze and predict customer behavior and order outcomes in an e-commerce setting. The models provided valuable insights into the factors influencing customer reviews and delivery performance. These insights can help businesses improve customer satisfaction, optimize delivery processes, and enhance overall operational efficiency.

Future work could involve:
- Incorporating additional datasets, such as customer demographics or browsing behavior.
- Exploring deep learning models for improved prediction accuracy.
- Developing a real-time prediction pipeline for live order monitoring.
