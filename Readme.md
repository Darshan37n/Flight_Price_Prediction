# ✈️ Flight Fare Prediction

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-orange?logo=scikitlearn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-Best%20Model-green)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

A machine learning project that predicts flight ticket prices based on airline, route, travel time, duration, and number of stops using a complete end-to-end ML pipeline.

---

## 📁 Project Structure

```
flight-fare-prediction/
│
├── README.md
├── .gitignore
├── requirements.txt
│
├── data/
│   ├── Flight_Fare.xlsx
│   └── README.md
│
├── notebooks/
│   └── FlightPricePrediction.ipynb
│
└── models/
    └── model.pkl
```

---

## 📊 Dataset

| Detail | Info |
|---|---|
| **Source** | DataMites Institute |
| **Size** | 10,683 rows × 11 columns |
| **Target Variable** | `Price` — Flight ticket fare (INR) |

**Key Features:**

| Feature | Type | Description |
|---|---|---|
| `Airline` | Categorical | Name of the airline |
| `Date_of_Journey` | Categorical | Date of travel |
| `Source` | Categorical | Departure city |
| `Destination` | Categorical | Arrival city |
| `Route` | Categorical | Path taken by flight |
| `Dep_Time` | Categorical | Departure time |
| `Arrival_Time` | Categorical | Arrival time |
| `Duration` | Categorical | Total flight duration |
| `Total_Stops` | Categorical | Number of stops |
| `Additional_Info` | Categorical | Extra info (meals, baggage) |
| **`Price`** | **Numerical** | **🎯 Target variable** |

---

## 🚀 Project Workflow

### 1. 🧹 Data Cleaning
- Dropped 1 row with missing values in Route and Total_Stops
- Removed duplicate records

### 2. ⚙️ Feature Engineering
| Original Column | Extracted Features |
|---|---|
| `Date_of_Journey` | `Journey_Day`, `Journey_Month` |
| `Dep_Time` | `Dep_Hour`, `Dep_Mins` |
| `Arrival_Time` | `Arrival_Hour`, `Arrival_Min` |
| `Duration` | `Duration_Mins` (converted to integer) |

### 3. 📈 EDA Findings
- Jet Airways Business has the highest average price — nearly ₹60,000
- Delhi is the most expensive departure city — highest demand hub
- Non-stop flights are cheaper — they cover short domestic routes
- 4 stop flights are the most expensive — longer journeys covering more distance
- March to June is peak season — prices spike during summer travel
- Dep_Mins and Arrival_Min carry no predictive value — dropped

### 4. 🔧 Encoding Strategy

| Encoding | Feature | Reason |
|---|---|---|
| Ordinal | `Total_Stops` | Natural order exists |
| Target | `Airline` | High cardinality, strong price signal |
| One-Hot | `Source`, `Destination` | Nominal categories |
| Dropped | `Route`, `Additional_Info` | Too many unique values / low signal |

### 5. 🤖 Models Trained

| Model | Notes |
|---|---|
| Linear Regression | Baseline |
| Ridge Regression (L2) | Reduces overfitting |
| Lasso Regression (L1) | Feature sparsity |
| Gradient Boosting | Captures non-linear patterns |
| Random Forest | Strong ensemble model |
| **XGBoost** | ✅ **Best performance after tuning** |

---

## 🔧 Tools Used

- Python — Pandas, NumPy, Matplotlib, Seaborn
- Scikit-Learn — Preprocessing, Models, RandomizedSearchCV
- XGBoost
- Pickle — Model saving


## 📌 Key Takeaways

- Airline type is the strongest predictor of flight price
- Duration and number of stops are the most important numerical features
- Tree-based models (XGBoost, Random Forest) significantly outperform linear models
- Seasonal travel patterns (March–June) have a visible impact on pricing
