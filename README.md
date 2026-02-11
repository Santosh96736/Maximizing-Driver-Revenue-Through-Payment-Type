# Maximizing-Driver-Revenue-Through-Payment-Type

# Project Overview
This project analyzes NYC Yellow Taxi trip data to determine whether payment type (Card vs Cash) significantly impacts driver revenue per trip.

Using statistical analysis and hypothesis testing, we evaluate whether encouraging digital payments can increase driver earnings.

# Business Problem
Taxi drivers receive payments via multiple methods.
However, it is unclear whether:

- Card payments generate higher revenue than cash

- The difference is statistically significant

- Payment behavior impacts earnings

This project aims to answer:

Does payment type significantly affect driver revenue?

# Dataset
Source: NYC Yellow Taxi Trip Data (2023)

Time Period Used: January–February 2023

Size: Multi-million trip records

Processing Method: Chunk-based loading for memory efficiency

## Selected Columns
| Columns          | Over View            |
| ---------------- | -------------------- |
| pickup_datetime  | Trip start time      |
| dropoff_datetime | Trip end time        |
| passenger_count  | Trip passenger count |
| trip_distance    |        |
| payment_type     | Independent variable |
| fare_amount      | Dependent variable   |

# Technical Approach :
## Large-Scale Data Handling
- Used chunksize=1_000_000

- Filtered specific months

- Wrote processed subset to a new CSV

- Ensured reproducibility (file deletion before append)

## Data Cleaning

- Removed missing values

- Removed duplicates

- Filtered unrealistic records:

   - Duration > 0

   - Distance > 0

   - Fare > 0

- Restricted to:

   - Passenger count 1–5

   - Payment types: Card & Cash only

   - Outlier removal using IQR method

## Feature Engineering

Created:  

- Trip duration (minutes)

This helped validate realistic trip behavior.

## Exploratory Data Analysis

Analyzed:

- Fare distribution by payment type

- Trip distance distribution

- Payment preference distribution

- Passenger count segmentation

Key observation:

- Card payments dominate usage

- Card trips show higher average fares

## Statistical Testing
Hypothesis

- H₀: Payment type has no effect on average fare
- H₁: Payment type significantly affects average fare

Test Used  

- Welch’s t-test (unequal variance assumption)  
```st.ttest_ind(card_sample, cash_sample, equal_var=False)```

Result

- p-value < 0.05

- Null hypothesis rejected

Conclusion:

- Payment type significantly impacts driver revenue per trip.

## Key Findings

- Card payments have higher average fare and lower standard deviation than cash.

- Revenue difference is statistically significant.

## Business Recommendation

- Drivers should encourage card payments.

- Platforms may incentivize digital transactions.

- Digital payment ecosystems likely improve revenue predictability.

## Skills Demonstrated

- Large-scale data processing

- Data cleaning & validation

- Feature engineering

- EDA & visualization

- Hypothesis testing

- Business interpretation
