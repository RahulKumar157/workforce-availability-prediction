# workforce-availability-prediction

# 🏭 AI-Driven Workforce Availability & Compliance System

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Machine Learning](https://img.shields.io/badge/ML-Random%20Forest-green)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📌 Project Overview
This project focuses on optimizing workforce planning for a fulfillment center by moving from reactive staffing to a **data-driven proactive approach**. 

Using **41 days of contractor attendance data**, I built a solution to:
1.  **Predict Daily Availability:** Forecast which employees are likely to be present/absent.
2.  **Ensure Compliance:** Automate checks for labor health standards (Fatigue Management).
3.  **Analyze Trends:** Visualize attendance patterns to identify operational risks.

## 🎯 Business Problem & Solution
**The Challenge:** High absenteeism and manual roster checks were leading to staffing shortages and potential violations of labor laws (continuous working days).

**The Solution:**
* **ETL Pipeline:** Transformed raw "Wide-Format" rosters into "Long-Format" Time-Series data.
* **Machine Learning:** Trained a Random Forest Classifier to predict attendance with high accuracy.
* **Risk Auditing:** Implemented logic to flag employees working **>7 continuous day shifts** or **>14 continuous night shifts**.

## 📊 Key Insights & "The Holi Anomaly"
During the Exploratory Data Analysis (EDA), I identified a critical anomaly:
* **Observation:** Mondays showed the lowest average attendance (~51%), even lower than Sundays.
* **Investigation:** Deep-dive analysis revealed that **March 25, 2024 (Holi Festival)** fell on a Monday, dragging the average down by ~30%.
* **Action:** Engineered a custom feature `Is_Holiday` to isolate this event, preventing the model from falsely penalizing all future Mondays.

## 🛠️ Tech Stack
* **Data Processing:** Python (Pandas, NumPy), SQL (for initial data extraction).
* **Machine Learning:** Scikit-Learn (Random Forest, Gradient Boosting, Label Encoding).
* **Visualization:** Matplotlib, Seaborn, Power BI (for dashboarding).
* **IDE:** Jupyter Notebook / VS Code.

## ⚙️ Methodology
1.  **Data Cleaning:** Handled missing values and standardized categorical inconsistencies (e.g., merging 'MALE' and 'Male').
2.  **Feature Engineering:**
    * Created `DayOfWeek`, `Is_Weekend`, and `Is_Holiday` features.
    * Applied **Label Encoding** for categorical variables (Vendor, Shift, Designation).
3.  **Modeling:** Compared Logistic Regression, Decision Trees, and Random Forest.
    * *Winner:* **Random Forest** (Best balance of accuracy and generalization).
4.  **Compliance Logic:**
    * Day Shift Alert: Streak > 7 days (Broken by 'WOD'/'COD').
    * Night Shift Alert: Streak > 14 days (Broken by 'WON').

## 📈 Results
* **Baseline Availability:** Established a benchmark availability rate of **58%**.
* **Risk Mitigation:** Successfully identified high-risk rosters violating fatigue guidelines.
* **Forecasting:** Generated a list of employees with high probability scores for the next day's shift.

## 🚀 How to Run
1. Clone the repository:
   ```bash
   git clone [https://github.com/your-username/workforce-availability-prediction.git](https://github.com/your-username/workforce-availability-prediction.git)
