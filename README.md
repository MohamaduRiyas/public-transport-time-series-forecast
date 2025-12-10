# 🚍 Daily Public Transport Passenger Forecasting Using Time Series (ARIMA Model)

## 📌 Project Overview
This project performs **Exploratory Data Analysis (EDA)** and **7-day forecasting** of public transport passenger journeys using historical daily data. The aim is to understand transport usage patterns, derive meaningful insights, and build a predictive model that helps in **capacity planning**, **resource allocation**, and **transport optimization**.

The dataset includes passenger counts for:
- **Local Route**
- **Light Rail**
- **Peak Service**
- **Rapid Route**
- **School Service**
- **Other Services**

This project is structured in two stages:
1. **EDA** → Understanding and cleaning the data  
2. **Forecasting** → Predicting the next 7 days using ARIMA  

---

## 🧠 Key Objectives

- Understand transport passenger behavior over time  
- Identify trends, patterns, and correlations  
- Forecast demand for the next 7 days  
- Provide actionable insights  
- Build and explain a forecasting model clearly  

---

## 📁 Dataset Information

**File:**  
`Daily_Public_Transport_Passenger_Journeys_by_Service_Type_20250603.xls`

**Columns:**
- Date  
- Local Route  
- Light Rail  
- Peak Service  
- Rapid Route  
- School  
- Other  

Each row represents **daily passenger count** for each service.

---

# 🛠️ Technologies Used

| Tool | Purpose |
|------|---------|
| **Python** | Core programming language |
| **Pandas** | Data loading & cleaning |
| **NumPy** | Numerical operations |
| **Matplotlib** | Visualizations |
| **Seaborn** | Statistical plotting |
| **Statsmodels** | ARIMA forecasting |
| **Jupyter Notebook** | Step-by-step analysis |

---

# 📊 Step-by-Step Workflow

This project follows a standard **CRISP-DM (Data Mining) workflow**.

---

## 🔹 **Step 1: Import Libraries**
Imported libraries required for data handling, visualization, and forecasting.

---

## 🔹 **Step 2: Data Ingestion**
Loaded the dataset using:

```python
df = pd.read_excel("Daily_Public_Transport_Passenger_Journeys_by_Service_Type_20250603.xls")
Sample rows were displayed using df.head() for initial inspection.

🔹 Step 3: Basic Data Understanding
Performed:

df.shape → Rows & columns

df.columns → Column names

df.dtypes → Data types

df.describe() → Numeric stats

df.isna().sum() → Missing value check

df.duplicated().sum() → Duplicate check

These steps help confirm dataset quality.

🔹 Step 4: Data Cleaning
Performed the following operations:

Converted Date column into datetime format

Set Date as index:

python
Copy code
df['Date'] = pd.to_datetime(df['Date'])
df = df.set_index('Date')
Removed duplicates

Handled missing values if any

This ensures the dataset is ready for time series modeling.

🔹 Step 5: Exploratory Data Analysis (EDA)
✔ Visualization 1: Daily Trend Line Plot
Shows how passenger counts change over time.

✔ Visualization 2: Distribution Plots
Shows how each service behaves statistically.

✔ Visualization 3: Correlation Heatmap
Identifies relationships between services.

✔ Visualization 4: Multivariate Analysis
Scatterplots and moving averages to study trends.

Sample EDA Visuals:
scss
Copy code
(Line plot showing overall transport trend)
(Histograms of passenger distributions)
(Correlation heatmap)
🤖 Step 6: Model Selection – Why ARIMA?
📌 Model Chosen: ARIMA (AutoRegressive Integrated Moving Average)
ARIMA is ideal for:

Date-based numerical data

Short-term forecasting

Datasets with trends but no strong seasonality

ARIMA Explanation:
AR (AutoRegressive): Uses past values

I (Integrated): Removes trend using differencing

MA (Moving Average): Uses past forecast errors

Parameters Used:
scss
Copy code
ARIMA(1, 1, 1)
Parameter	Meaning
p = 1	Looks 1 day back
d = 1	Stabilizes time series
q = 1	Uses previous error

Why ARIMA Was Selected:
Works perfectly for univariate time series

High accuracy for short-term forecasts

Easy to interpret

Industry standard for time series

Our dataset is daily numerical data → ideal for ARIMA

🔮 Step 7: Forecasting the Next 7 Days
Forecasts were generated for:

Local Route

Light Rail

Peak Service

Rapid Route

School Service

Each service was modeled separately using:

python
Copy code
model = ARIMA(series, order=(1,1,1))
model_fit = model.fit()
forecast = model_fit.forecast(steps=7)
✔ Output:
7 predicted passenger counts

Future trend visualization

Helps understand expected demand

Sample Forecast Visual:
arduino
Copy code
(Original data + red forecast line for next 7 days)
📝 Key Insights
Here are business-level insights extracted from the analysis:

🔹 Insight 1
Local Route has the highest average passenger count, indicating it is the most heavily used service.

🔹 Insight 2
School Service shows clear weekday patterns, suggesting high dependency on academic schedules.

🔹 Insight 3
Peak Service experiences sharp fluctuations, indicating strong dependence on office travel timings.

🔹 Insight 4
Rapid Route remains stable and predictable, showing consistent usage.

🔹 Insight 5
Multiple services show positive correlation, meaning passenger trends across services often move together.

📁 Repository Structure
Copy code
📦 Transport-Passenger-Forecasting
 ┣ 📄 README.md
 ┣ 📊 step1_eda.ipynb
 ┣ 📈 step2_forecasting.ipynb
 ┣ 📁 images/
 ┃ ┣ trend_plot.png
 ┃ ┣ heatmap.png
 ┃ ┗ forecast_local.png
 ┣ 📄 requirements.txt
 ┗ 📄 dataset.xls
🚀 Real-World Applications
Public transport planning

Demand forecasting

Smart-city analytics

Optimizing bus/train schedules

Resource allocation

🎯 Conclusion
This project demonstrates a complete end-to-end pipeline:

✔ Data Understanding
✔ Data Cleaning
✔ Visualization & EDA
✔ Time-Series Forecasting
✔ Insights & Conclusion

The ARIMA model helps predict short-term passenger demand with high reliability.

👨‍💻 Author
Name: MOHAMADU RIYAS S
Role: Data Science 
GitHub: Add your GitHub link here
Tools: Python | EDA | Time Series | ARIMA
