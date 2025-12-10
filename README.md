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
<img width="332" height="116" alt="image" src="https://github.com/user-attachments/assets/ba0ae500-a3ad-448e-90b9-212e85818c6c" />


---

## 🔹 **Step 2: Data Ingestion**
Loaded the dataset using:

```python
df = pd.read_excel("Daily_Public_Transport_Passenger_Journeys_by_Service_Type_20250603.xls")
Sample rows were displayed using df.head() for initial inspection.

<img width="748" height="306" alt="image" src="https://github.com/user-attachments/assets/4a884abb-d515-4191-9475-be28f2bc4ba8" />


🔹 Step 3: Basic Data Understanding
Performed:

df.shape → Rows & columns

<img width="339" height="167" alt="image" src="https://github.com/user-attachments/assets/c7aa3b2d-bd30-4064-883d-c983c0f6d45e" />


df.columns → Column names

<img width="790" height="210" alt="image" src="https://github.com/user-attachments/assets/98e65ed8-1a29-49d4-b6ca-9122bb0a341d" />


df.dtypes → Data types

<img width="539" height="308" alt="image" src="https://github.com/user-attachments/assets/f9fc0355-2b7c-447d-bc30-98b73d742d82" />


df.describe() → Numeric stats

<img width="1082" height="411" alt="image" src="https://github.com/user-attachments/assets/1cf3e7c9-aed3-4c46-a5aa-be042bbec6cc" />


df.isna().sum() → Missing value check

<img width="324" height="301" alt="image" src="https://github.com/user-attachments/assets/90e7535b-bdb3-42fa-a160-0d2729819fc2" />


df.duplicated().sum() → Duplicate check

<img width="356" height="151" alt="image" src="https://github.com/user-attachments/assets/d5f4e056-47dd-4096-b9ed-733c4ddf973f" />


These steps help confirm dataset quality.

🔹 Step 4: Data Cleaning
Performed the following operations:

Converted Date column into datetime format

Set Date as index:

<img width="520" height="338" alt="image" src="https://github.com/user-attachments/assets/8edb5459-bcb2-4739-927a-5acebc8e6e08" />

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

<img width="847" height="713" alt="image" src="https://github.com/user-attachments/assets/8e2ec1b9-32dd-47e1-a11f-20653de08733" />


Light Rail

<img width="758" height="703" alt="image" src="https://github.com/user-attachments/assets/d0f21091-9a29-4e65-bdd3-21918a91f615" />


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
