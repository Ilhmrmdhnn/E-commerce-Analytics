# 20240827_Perqara_Assessment_Data Scientist

# E-commerce Analytics Project

## Description

This project involves a comprehensive analysis of an e-commerce dataset, encompassing various aspects such as customer behavior, product performance, and order patterns. The analysis includes data preparation, basic and advanced analytics, and predictive modeling for order value and order status.

### Key Features
- Data integration from provided sources
- Time series forecasting of order volume
- Geospatial analysis of customer distribution
- RFM (Recency, Frequency, Monetary) customer segmentation
- Outlier detection in payment values
- Predictive modeling for order value and order status

### Objectives
- Gain actionable insights from the e-commerce dataset
- Develop predictive models to estimate order value and order status
- Perform customer segmentation based on their purchase behavior (RFM)
- Identify trends and patterns in order data

## Data Preparation

### ERD

![Assasment Data Science](https://github.com/user-attachments/assets/9e18e52a-07aa-44db-9aad-62046b1a4698)

The data preparation process involves merging several datasets:
- Customers Dataset
- Geolocation Dataset
- Order Items Dataset
- Order Payments Dataset
- Order Reviews Dataset
- Orders Dataset
- Product Category Name Translation
- Product Dataset
- Sellers Dataset

### Key Steps in Data Preparation:
- Cleaning each dataset
	- Size
	- Duplicate
	- Missing Value
- Merging relevant datasets into a single entity
- Handling missing values using mean imputation
- Converting date columns to datetime format
- Feature engineering (e.g., calculating delivery days)
- Normalizing numerical features
- Features Engineering

# Basic Analysis
The basic analysis phase reveals several insights:

## Describe Stats:

![Describe](https://github.com/user-attachments/assets/2a328c11-6698-4d3e-9be8-0d11a2860416)

This data shows descriptive statistics for various features related to online orders. Here are descriptions and interpretations for each feature:
### Feature and Interpretation
- **order_purchase_timestamp**: Date and time when the order was placed.  
  Date range: October 2016 - August 2018  
  Average purchase date: December 2017
- **order_delivered_customer_date**: Date and time when the order was delivered to the customer.  
  Date range: October 2016 - October 2018  
  Average delivery date: January 2018
- **order_estimated_delivery_date**: Estimated date and time for order delivery.  
  Date range: October 2016 - October 2018  
  Average estimated delivery date: January 2018
- **customer_zip_code_prefix**: Customer's zip code prefix.  
  Zip code range: 1003 - 99980  
  Average zip code: 34320
- **order_item_id**: Unique ID for each item in the order.  
  Item ID range: 1 - 21  
  Average item ID: 1
- **price**: Price of the item in the order.  
  Price range: 0.85 - 6735  
  Average price: 122
- **freight_value**: Shipping cost for the order.  
  Shipping cost range: 0 - 375.28  
  Average shipping cost: 20
- **payment_sequential**: Sequential number of the payment for the order.  
  Payment sequential number range: 1 - 13  
  Average payment sequential number: 1
- **payment_installments**: Number of installments for the payment of the order.  
  Number of installments range: 1 - 24  
  Average number of installments: 3
- **payment_value**: Total value of the payment for the order.  
  Payment value range: 0 - 13664.08  
  Average payment value: 185
- **review_score**: Customer review score for the order.  
  Review score range: 1 - 5  
  Average review score: 3.6
- **product_name_length**: Length of the product name in characters.  
  Product name length range: 5 - 720  
  Average product name length: 48
- **product_description_length**: Length of the product description in characters.  
  Product description length range: 4 - 3992  
  Average product description length: 769
- **product_photos_qty**: Number of product photos in the order.  
  Number of photos range: 1 - 19  
  Average number of photos: 2
- **product_weight_g**: Weight of the product in grams.  
  Product weight range: 0 - 30000  
  Average product weight: 2274
- **product_length_cm**: Length of the product in centimeters.  
  Product length range: 7 - 105  
  Average product length: 30
- **product_height_cm**: Height of the product in centimeters.  
  Product height range: 2 - 105  
  Average product height: 17
- **product_width_cm**: Width of the product in centimeters.  
  Product width range: 6 - 118  
  Average product width: 23
- **seller_zip_code_prefix**: Seller's zip code prefix.  
  Zip code range: 1001 - 99730  
  Average zip code: 24343
- **geolocation_zip_code_prefix**: Zip code prefix of the geolocation.  
  Zip code range: 1003 - 99980  
  Average zip code: 34320
- **geolocation_lat**: Latitude of the geolocation.  
  Latitude range: -36.605374 - 42.428884  
  Average latitude: -21.669125
- **geolocation_lng**: Longitude of the geolocation.  
  Longitude range: -101.466766 - -4.947823  
  Average longitude: -46.00489
- **order_delivery_days**: Number of days taken to deliver the order.  
  Number of days range: 0 - 195  
  Average number of days: 12
- **estimated_delivery_days**: Number of days estimated to deliver the order.  
  Number of days range: 2 - 155  
  Average number of days: 24

### Interpretation

This data can be used to understand purchase patterns, delivery behavior, and customer preferences:
- **Delivery Time**: The average delivery time is around 12 days, while the estimated delivery time is around 24 days, indicating that deliveries are often faster than estimated.
- **Shipping Costs**: The average shipping cost is around 20, indicating that shipping is a significant part of the order cost.
- **Improvement Areas**: This data can be used to identify areas for improvement, such as inaccurate delivery times or high shipping costs.

### Order Status Distribution:

![Order Status](https://github.com/user-attachments/assets/dc7ee13e-10f9-4851-8d93-9003460dbb53)

- **Delivered**: 4759405
- **Canceled**: 612

**Insight**: The majority of orders were successfully delivered, with a relatively low cancellation rate.

### Top 10 Product Categories by Average Order Value:

![Top 10](https://github.com/user-attachments/assets/583fe5c6-4209-4481-abfe-2bf357802b4c)

- **Computers**
- **Fixed Telephony** 
- **Signaling and Security**
- **Furniture Living Room**
- **Home Appliances 2**
- **Small Appliances Home Oven and Coffee**
- ** Agro Industry and Commerce**
- **Office Furniture**
- **Musical Instrument**
- **Air Conditioning**

**Insight**: The Computers and Fixed Telephony categories have the highest average order values, followed by Signaling and Security and Furniture Living Room.

### Correlation Analysis:

![Correlation Heatmap](https://github.com/user-attachments/assets/6c3c470d-b0d4-4af0-b1a3-19ef32f08a3e)

- High positive correlation between 'customer_zip_code_prefix' and 'geolocation_zip_code_prefix' (1.00)
- Other positive correlations between 'price' and 'payment_value' (0.72)

**Insight**: The price of the product strongly influences the payment value, and customer prefix strongly influences geolocation prefix

### Boxplot

![Boxplot Price](https://github.com/user-attachments/assets/7387d582-bc7d-4beb-9fa4-9e50ed98514f)

- The 'price' column has outliers, but no data dropping was performed because a lot of important information would be lost.

### Daily Order Volume Trend:

![Daily Order Volume](https://github.com/user-attachments/assets/2493f990-18a2-42f8-8573-a8f001bfc014)

- The trend shows fluctuating movement of order volume over time.
- Weekly fluctuations are clearly visible, with a drop on weekends

### Monthly Order Volume Trend:

![Monthly Order Volume](https://github.com/user-attachments/assets/fa25a99d-3d7f-4c94-897d-69e074a609dc)

- The trend shows an increase in order volume from month to month

**Insight**: This e-commerce business shows growth, with a consistent demand pattern.

## Advanced Analysis

### Time Series Forecasting
- **Methodology**: ARIMA model
- **Forecasting Horizon**: 365 days and 12 months
- **Daily** and **Monhtly**

![Order Volume Forecast 1 Year (Daily)](https://github.com/user-attachments/assets/ab145fb2-1bca-4426-af0e-62398b156cdc)

![Order Volume Forecast 1 Year (Monthly)](https://github.com/user-attachments/assets/7fdb2056-c1e2-4e5b-b868-f8c8d0c75a6a)

#### Key Findings:
- **Daily** The model predicts an increasing trend in order volume for the next 365 days, but it will become flat over a long period of time due to the lack of fluctuation in the historical data.
- **Monthly** The model predicts an increasing trend in order volume for the next 12 months, with an increase every month.

### Geo Analysis
- **Customer Geographic Distribution**:
![Cust Geo Distribution](https://github.com/user-attachments/assets/c4142a4d-54aa-48e3-8b02-c88f3220ee6e)

#### Insights:
- High customer concentration in the sao paulo, guarulhos and sao bernardo do campo areas

### Outlier Detection
- **Method**: Elliptic Envelope

![Payment Value Outliers](https://github.com/user-attachments/assets/cffbe4ed-3f03-41a5-80cd-07fd62ec53ed)

#### Findings:
- Approximately 10% of payment values are identified as outliers
- Outliers are generally transactions with very high values

### RFM Analysis
- **Segmentation**: 4 customer clusters identified

![Elbow Method](https://github.com/user-attachments/assets/5a4647d2-a03b-44e8-8d25-a2bb4a18cf0e)

![Visual RFM](https://github.com/user-attachments/assets/9abc1847-cabf-4bc6-a6bb-06610fe036a6)

![Visual RFM 3D](https://github.com/user-attachments/assets/c456aaab-8463-416b-8d1a-31356a4c28a3)

![Cluster Stat RFM](https://github.com/user-attachments/assets/f395149a-52f0-4bc4-a72f-b5be7be8ac77)

![RFM Summary](https://github.com/user-attachments/assets/29e6d86b-5fb1-41dc-969f-f8680dc9f2cb)

### Customer Segmentation
### 1. Prime Customers
- **Purchase Frequency**: Very high
- **Monetary Value**: Very high
- **Characteristics**: Most valuable and loyal customers

### 2. Potential Customers
- **Frequency and Monetary Value**: Medium
- **Recency**: Pretty good
- **Characteristics**: Potential to be upgraded to prime customers

### 3. New Customers
- **Recency**: Low (recent transactions)
- **Frequency and Monetary Value**: Still low
- **Characteristics**: Need strategies to increase loyalty

### 4. Passive Customers
- **Recency**: High (long time since last transaction)
- **Frequency and Monetary Value**: Low
- **Characteristics**: Need reactivation strategies


## Predictive Modeling

### Order Status Prediction Model
- **Model**: Random Forest Classifier
- **Target Variable**: Order Status

#### Model Performance:
![Classification Report (Order Status)](https://github.com/user-attachments/assets/0c5898f6-db36-4f57-ab1d-c9b07b8bfb39)

- **Accuracy**: 1
- **F1-score (weighted average)**: 1

#### Confusion Matrix
![CM (Order Status)](https://github.com/user-attachments/assets/e28b2329-6212-46b8-82e4-0553e39e22a2)

#### Top Feature Importance:
![Features Importan (Order Status)](https://github.com/user-attachments/assets/3cd05ed7-ae41-488e-b8d8-18bdcdf62ba4)

- **estimated_delivery_days**
- **freight_value**
- **order_delivery_days**
- **product_weight_g**
- **product_name_length**

**Insight**: The model has high accuracy in predicting order status, with the above variables being the main predictors

### Order Value Prediction Model
- **Model**: Random Forest Regressor
- **Target Variable**: Payment Value

#### Model Performance:

![evaluasi (Payment Value)](https://github.com/user-attachments/assets/3511b2ad-0d4a-48c6-92cc-b6ccbc64dd89)

- **Mean Squared Error**: 575.9692311025973
- **R-squared Score**: 0.992264227932851

#### Top Feature Importance:

![Features Importan (Payment Value)](https://github.com/user-attachments/assets/dedb39e9-c11f-47ea-8161-44eb68799e17)

- **price**
- **freight_value**
- **product_description_length**
- **product_name_length**
- **review_score**

**Insight**: The model shows good performance in predicting order value, with product price being the most significant predictor.



## Key Insights
- The majority of orders (99.99%) were successfully delivered, indicating high operational efficiency.
- Product categories like Computers, computer accessories, and Fixed Telephony generate the highest order values, making them potential targets for promotions.
- There is a clear trend pattern in order volume, with a drop on weekends, which can be leveraged for marketing strategies.
- High customer concentration in the sao paulo area, indicating potential for market expansion in other regions.
- Customer segmentation reveals four main groups, enabling more personalized marketing strategies.

## Recommendations
- Focus marketing efforts on high-value product categories such as Computers and Fixed Telephony.
- Implement retention strategies for customers in Cluster 0 (Passive Customers) to increase their purchase frequency.
- Optimize inventory and delivery resources based on the identified demand patterns.
- Consider special marketing campaigns to boost sales on weekdays.
- Explore expansion opportunities to areas with lower customer concentration.

## What can be developed for the next step:
- Implement deeper time series models for more accurate forecasting
- Develop a more detailed customer churn prediction model
- Perform sentiment analysis on review comments to understand customer satisfaction and other aspects
- Create a recommendation system based on purchase history

## How to Use This Repository
1. Clone the repository
2. Install the required dependencies: `pip install -r requirements.txt`
3. Run the scripts in the following order:
   - `assesment.py`
4. View the generated visualizations in the `visualizations` folder
5. Check the `models` folder for the saved predictive models

## Contributor
Ilham Ramadhan Nur Ahmad
