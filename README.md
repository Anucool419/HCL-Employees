# Customer Lifetime Value (CLV) Prediction 📊

> **Event:** HCLTech AI/Python Hackathon  


1. For each active customer, we are to estimate the total monetary amount the customer spends in the next 30 days (after the cutoff dates) based on his/her previous purchases. 
The features such as historical transaction behavior, category preferences etc. were taken into consideration before preparing a prediction model.
The SQL approach and the traditional python approach was made to find the prediction amount of the customer.
Appropriate regression metrics like Root Mean Squared Error (RMSE), Mean Absolute Error (MAE),R^2 were used in this prediction model.

2. We had obtained a dataset from public sources which was about the sales on online retail stores. Our objective was to find the short-term CLV (Customer Lifetime Value) over a defined horizon.
The data includes a transaction-level data. Also, each customer has multiple transactions over time and each of them has an individual timestamp of the purchase. Also it has enough information to compute the monetary value. The customers range all the way from Australia, UK to France, Germany.
Dataset contains more that 15000 transactions and is done on various fields. With all these, we were able to clean off the data and segregated them into bad records and clean records and regression models were applied based on the same. 
<img width="4400" height="200" alt="image" src="https://github.com/user-attachments/assets/36603255-2873-4847-91d7-255764d9633f" />


<img width="2604" height="265" alt="image" src="https://github.com/user-attachments/assets/0138dcb9-1f2a-44bb-beac-910f90ca4eaa" />




Project Overview
This project focuses on predicting the future spending potential of customers over the next 30 days. By leveraging machine learning on historical transaction data, the system identifies high-value customers and provides actionable insights for business strategy.

Process Rules & Methodology

This project followed a strict four-phase data processing and modeling pipeline:

### 1. Data Cleaning & Filtering Rules
To ensure data quality, the raw "Online Retail" dataset was subjected to a rigid filtering process. Records were only retained if they met specific validity conditions, including:
* Transaction Validation: `Quantity` must be `>= 1` (removing returns/errors).
* Identity Validation: `CustomerID` must be a valid 5-digit identifier.
* Scope: Focused exclusively on valid transaction records to minimize noise.

### 2. Feature Engineering (RFM Approach)
We transformed raw transactional data into behavioral features using the **RFM** framework:
* Recency: Days since the last purchase.
* Frequency: Total number of transactions.
* Monetary: Total spend amount.
* Time-Window Logic: The dataset was split based on a 30-day cutoff:
    * Input Features: Calculated from history *prior* to the cutoff.
    * Target Variable: The actual spend occurred in the *subsequent* 30 days.

### 3. Modeling Strategy
* Algorithm: Random Forest Regressor.
* Objective: Minimize error in predicting the specific numerical value of future spend.

### 4. User Interface (Streamlit)
The final model is deployed via a Streamlit web application that follows this logic:
1.  Input: User enters a `CustomerID`.
2.  Processing: The app retrieves the pre-calculated RFM features for that ID.
3.  Output: Displays the **Predicted Future Spend** vs. **Actual Future Spend** alongside specific customer insights.

## 🛠️ Tech Stack
* **Language:** Python
* **Data Processing:** Pandas, NumPy
* **Machine Learning:** Scikit-learn (Random Forest)
* **Interface:** Streamlit

## 🚀 How to Run
1.  Clone the repository.
2.  Install dependencies: `pip install -r requirements.txt`
3.  Run the app: `streamlit run app.py`
