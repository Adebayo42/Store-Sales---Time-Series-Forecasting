# 🛒 Store Sales - Time Series Forecasting

A machine learning project that forecasts unit sales for thousands of items sold at Corporación Favorita, a large Ecuadorian-based grocery retailer. This project ranked in the **top 5.97% globally** (52nd out of 871 participants) and in the **top 1.5% of 3,455 submissions**—a personal milestone toward my aspiration to become a global leader in the data science space.



## 🌍 Context

Retailers face a daily balancing act: overstock perishables and incur waste, or understock and lose revenue—and trust. Traditionally, sales forecasts in grocery retail have relied on manual, experience-based heuristics with limited data. However, the ever-evolving landscape—ranging from local events to promotions, weather, and seasonality—calls for more robust, scalable, and data-driven methods.

This project explores how machine learning, specifically time series modeling with the Darts library, can enhance forecasting accuracy at scale.



## 🔥 Highlights

- 🧠 **Machine Learning Model**: Trained Random Forest models using time series features, past covariates, future covariates, and static features.
- 🗂️ **Hierarchical Modeling**: Forecasts were built both at the **family-level (global model)** and **store-family level (granular model)**.
- 📈 **Features Used**:
  - Promotions
  - Date attributes (cyclical and non-cyclical)
  - Oil prices with moving averages
  - Holidays in Ecuador
  - Transaction counts (past covariate)
  - Earthquake impact flags
  - Pay-day effect
- 📊 **Performance**:
  - Global model MAE: `22.77`
  - Store-family model MAE: `18.47`

---

## 📦 Tech Stack

- Python 🐍
- [Darts](https://github.com/unit8co/darts) – Time Series modeling
- Pandas, NumPy – Data manipulation
- Scikit-learn – Random Forest regressor
- Matplotlib – Visualization

---

## ⚙️ Setup Instructions

To reproduce this project:

```bash
# Clone the repository
git clone https://github.com/Adebayo42/Store-Sales---Time-Series-Forecasting.git
cd Store-Sales---Time-Series-Forecasting

# Install dependencies
pip install darts pandas numpy matplotlib scikit-learn
```


---

## 📊 Modeling Strategy

### 1. Preprocessing & Feature Engineering

- Filled missing dates and zero values in `sales` and `onpromotion`.
- Built full date range per store-family combination.
- Computed oil price moving averages: 7, 14, 21, and 28-day windows.
- Generated datetime features: day, week, month, etc. (including cyclic encodings).
- Added binary flags for:
  - Ecuadorian holidays
  - Payday effects (15th and end of month)
  - Earthquake impact (April 2016)

### 2. Covariates Preparation

- **Past covariates**:  
  - `transactions`
- **Future covariates**:  
  - Oil price features  
  - Date attributes  
  - Holidays
- **Static covariates**:  
  - Store-level info (e.g., city, cluster, store type)

### 3. Model Training

- Trained two tiers of models:
  - **Global Family Models**: One model per product family across all stores.
  - **Granular Store-Family Models**: One model per store-family combination.
- Utilized `RandomForest` models from the **Darts** library with:
  - Lag features
  - Multi-output forecasting
  - Covariates as inputs

### 4. Evaluation

- Backtested on historical data.
- Used **Mean Absolute Error (MAE)** to measure performance.

---

## 🧪 Results

| Model Level            | Average MAE |
|------------------------|-------------|
| Global (by Family)     | 22.77       |
| Store-Family           | **18.47**   |

---

## 🏆 Achievement

- 🥇 Placed **52nd globally** (Top **5.97%**) among **871** participants.
- 🥈 Solution ranked in the **Top 1.5%** of **3,455** total submissions.

---

## 🙌 Acknowledgements

Special thanks to [Kaggle](https://www.kaggle.com/competitions/store-sales-time-series-forecasting) for providing the dataset and hosting the competition.
