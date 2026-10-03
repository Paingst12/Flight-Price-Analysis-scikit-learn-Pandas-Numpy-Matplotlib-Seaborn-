# ✈️ Flight Price Exploratory Data Analysis & Predictive Modeling

## 📌 Project Background & Motivation

Airline ticket pricing is dynamic and influenced by a variety of factors including travel duration, transit layovers, route popularity, and carrier business models. Understanding these underlying mechanics is crucial for both travel platforms optimizing dynamic pricing engines and consumers seeking cost-effective itineraries.

This project was developed to perform a rigorous statistical and exploratory data analysis (EDA) on flight pricing data. By applying hypothesis testing, bivariate correlation analysis, and regression modeling, we aim to uncover the core quantitative drivers that dictate flight fare variations.

---

## ❓ Business Questions & Core Objectives

To provide actionable insights, this analysis addresses the following key questions:

1. **What is the primary driver of flight ticket prices?**
   - Does flight duration (`Duration_mins`) or the number of layover stops (`Total_Stops`) have a stronger impact on the final fare?
2. **How do specific routes and carriers influence pricing?**
   - Which departure sources and destination pairs command the highest premium fares?
   - How do budget carriers differ from premium airlines in terms of layovers and pricing strategy?
3. **Can we statistically model and quantify ticket prices?**
   - What is the baseline minimum fare for a route?
   - How accurately can a linear regression model explain price variance using duration and stops?

---

## 🔍 Analytical Approach & Exploratory Workflow

The analysis follows a structured data science pipeline implemented in `Flight Price Analysis.ipynb`:

### 1. Data Cleaning & Statistical Validation
- **Missing Value Handling:** Cleaned incomplete records across routes and durations.
- **Normality Testing:** Evaluated the `Weight`/continuous distributions using the **Shapiro-Wilk Test** ($p = 0.4341$), alongside Skewness ($0.12$) and Kurtosis ($-1.15$) metrics to verify distribution properties.
- **Outlier Detection:** Used the **Interquartile Range (IQR)** method to identify and bound extreme price outliers without distorting underlying distribution trends.

### 2. Multi-Panel Visual Exploration
- **Source & Destination Trends:** Analyzed route-specific average fares across major travel hubs.
- **Duration vs. Layover Analysis:** Grouped flight durations into time buckets to examine how layover frequency scales with total travel time.
- **Airline Carrier Segmentation:** Categorized pricing patterns across budget (IndiGo, SpiceJet, AirAsia) and premium/business carriers.

### 3. Statistical Testing & Predictive Modeling
- **Bivariate Correlation:** Measured linear relationships between numerical features and ticket price.
- **Hypothesis Testing:** Evaluated group differences across flight classes and stops.
- **Multiple Linear Regression:** Modeled price as a function of `Duration_mins` and `Stops_num`.

---

## 💡 Key Findings & Business Solutions

- **Primary Price Driver:** `Total_Stops` exhibits the strongest correlation with price ($r = 0.6039$), outperforming `Duration_mins` ($r = 0.5037$). Layovers add substantial operational and logistical costs reflected in the fare.
- **Regression Equation & Coefficients:**
  
  $$\text{Price} = 5426.36 + (1.21 \times \text{Duration\_mins}) + (3493.09 \times \text{Stops\_num})$$
  
  - **Baseline Fare (Intercept):** ~5,426.36
  - **Per-Stop Premium:** Every additional transit stop adds approximately **+3,493.09** to the fare.
  - **Per-Minute Fare:** Every additional minute of flight time adds **+1.21** to the fare.
- **Variance Explained ($R^2$):** The linear combination of duration and stops explains **35.06%** ($R^2 = 0.3506$) of ticket price variance. Single feature duration accounts for **24.84%** ($R^2 = 0.2484$).
- **Carrier Insights:** Premium business classes (e.g., Jet Airways Business) act as significant upper-bound outliers exceeding 100,000 average fares, whereas budget airlines maintain flat fare structures below 20,000 regardless of minor duration increases.

---

## 🛠️ Tech Stack & Key Libraries

- **Data Wrangling:** `pandas`, `numpy`
- **Statistical Testing:** `scipy.stats`, `statsmodels`
- **Data Visualization:** `matplotlib`, `seaborn`
- **Machine Learning:** `scikit-learn`
