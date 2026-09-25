# 🚖 NYC Yellow Taxi EDA & Hypothesis Testing: Payment Method vs. Fare Amount

## 📌 Project Overview
This project explores **NYC Yellow Taxi trip data (January 2020)** with over **5.26 million cleaned records**.  
The goal is to determine whether the **Payment Method** (Credit Card vs. Cash) significantly affects the **Total Fare Amount**, and to derive actionable strategies that optimize driver earnings while maintaining customer satisfaction.

---

## 📊 Dataset Summary
- **Source:** NYC Taxi & Limousine Commission (TLC) — Yellow Taxi Trip Records  
- **Original Size:** 6,405,008 rows, 18 columns  
- **Cleaned Size:** 5,262,323 rows, 22 columns  

### Key Features
- **Trip Timestamps:** `tpep_pickup_datetime`, `tpep_dropoff_datetime`  
- **Trip Metrics:** `trip_distance`, `trip_duration_min`, `avg_speed_mph`  
- **Fare Details:** `fare_amount`, `tip_amount`, `total_amount`  
- **Payment Types:**  
  - `1 = Credit Card`  
  - `2 = Cash`  
  - `3 = No Charge`  
  - `4 = Dispute`  
- **Engineered Features:** `pickup_hour`, `pickup_day`, `is_weekend`, `time_of_day`

---

## ⚙️ Methodology
1. **Missing Values:** Imputed `passenger_count` & `payment_type` using mode; dropped irrelevant metadata.  
2. **Outlier Removal:** Applied IQR filtering on `fare_amount`, `tip_amount`, `total_amount`, `trip_distance`.  
3. **Feature Engineering:** Derived temporal and performance metrics.  
4. **Hypothesis Testing (ANOVA / F-Test):**  
   - **Null Hypothesis ($H_0$):** Mean fare (Credit Card) = Mean fare (Cash)  
   - **Alternative ($H_1$):** Mean fares differ significantly  

---

## 📈 Key Findings

### 🔹 Hypothesis Test Results
- **Method:** One-Way ANOVA / F-test (`scipy.stats.f_oneway`)  
- **F-Statistic:** **98,742.15**  
- **p-Value:** **< 0.0001**  
- **Decision:** ✅ **Reject $H_0$** → Payment method **does affect fare amount**

### 🔹 Behavioral Insights
- **Average Fare:**  
  - Credit Card ≈ **$19.80**  
  - Cash ≈ **$14.30**  
- **Trip Preference:** Longer, high-cost trips (e.g., airport routes) lean toward **credit card payments**.  
- **Tip Logging Gap:** Credit card tips are auto-recorded, while cash tips are often missing, underreporting cash totals.

---

## 💡 Business Recommendations
1. **Smart Tip Displays:** Pre-set tip options (18%, 20%, 22%) on checkout screens.  
2. **Contactless Payments:** Promote Apple Pay / Google Pay to reduce checkout friction.  
3. **Driver Incentives:** Offer instant daily payouts for card transactions to encourage digital payments.

---

## 🛠️ Tech Stack
- **Language:** Python 3.13  
- **Libraries:**  
  - Data: `pandas`, `numpy`  
  - Visualization: `matplotlib`, `seaborn`  
  - Stats: `scipy.stats`  

---

## 📂 Project Structure
