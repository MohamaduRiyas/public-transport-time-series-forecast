
---

#  Daily Public Transport Passenger Forecasting Using Time Series (ARIMA Model)

##  Project Overview

This project performs **Exploratory Data Analysis (EDA)** and **7-day forecasting** of public transport passenger journeys using historical daily data. The aim is to understand transport usage patterns, derive meaningful insights, and build a predictive model that helps in **capacity planning**, **resource allocation**, and **transport optimization**.

The dataset includes passenger counts for:

* **Local Route**
* **Light Rail**
* **Peak Service**
* **Rapid Route**
* **School Service**
* **Other Services**

This project is structured in two stages:

1. **EDA** → Understanding and cleaning the data
2. **Forecasting** → Predicting the next 7 days using ARIMA

---

#  Key Objectives

* Understand transport passenger behavior over time
* Identify trends, patterns, and correlations
* Forecast demand for the next 7 days
* Provide actionable insights
* Build and explain a forecasting model clearly

---

#  Dataset Information

**File:**
`Daily_Public_Transport_Passenger_Journeys_by_Service_Type_20250603.xls`

**Columns:**

* Date
* Local Route
* Light Rail
* Peak Service
* Rapid Route
* School
* Other

Each row represents **daily passenger count** for each service.

---

#  Technologies Used

| Tool                 | Purpose                   |
| -------------------- | ------------------------- |
| **Python**           | Core programming language |
| **Pandas**           | Data loading & cleaning   |
| **NumPy**            | Numerical operations      |
| **Matplotlib**       | Visualizations            |
| **Seaborn**          | Statistical plotting      |
| **Statsmodels**      | ARIMA forecasting         |
| **Jupyter Notebook** | Step-by-step analysis     |

---

#  Step-by-Step Workflow

This project follows the **CRISP-DM workflow**.

---

##  Step 1: Import Libraries

Imported libraries for data handling, visualization, and forecasting.

<img width="332" height="116" alt="image" src="https://github.com/user-attachments/assets/ba0ae500-a3ad-448e-90b9-212e85818c6c" />

---

##  Step 2: Data Ingestion

Loaded the dataset:

df = pd.read_excel("Daily_Public_Transport_Passenger_Journeys_by_Service_Type_20250603.xls")

Displayed sample rows using `df.head()`:

<img width="748" height="306" alt="image" src="https://github.com/user-attachments/assets/4a884abb-d515-4191-9475-be28f2bc4ba8" />

---

##  Step 3: Basic Data Understanding

###  Shape

<img width="339" height="167" alt="image" src="https://github.com/user-attachments/assets/c7aa3b2d-bd30-4064-883d-c983c0f6d45e" />

###  Column names

<img width="790" height="210" alt="image" src="https://github.com/user-attachments/assets/98e65ed8-1a29-49d4-b6ca-9122bb0a341d" />

###  Data types

<img width="539" height="308" alt="image" src="https://github.com/user-attachments/assets/f9fc0355-2b7c-447d-bc30-98b73d742d82" />

###  Numeric summary

<img width="1082" height="411" alt="image" src="https://github.com/user-attachments/assets/1cf3e7c9-aed3-4c46-a5aa-be042bbec6cc" />

###  Missing values

<img width="324" height="301" alt="image" src="https://github.com/user-attachments/assets/90e7535b-bdb3-42fa-a160-0d2729819fc2" />

###  Duplicate check

<img width="356" height="151" alt="image" src="https://github.com/user-attachments/assets/d5f4e056-47dd-4096-b9ed-733c4ddf973f" />

---

##  Step 4: Data Cleaning

Converted Date column to datetime and set as index.

<img width="520" height="338" alt="image" src="https://github.com/user-attachments/assets/8edb5459-bcb2-4739-927a-5acebc8e6e08" />

Performed:

* Duplicate removal
* Missing value handling

---

##  Step 5: Exploratory Data Analysis (EDA)

Performed:

 Daily trend line plots
 Distribution plots
 Correlation heatmap
 Multivariate analysis
 Moving average trend analysis

(Visuals include line plots, histograms, heatmaps, etc.)

---

##  Step 6: Model Selection – Why ARIMA?

###  Chosen Model: **ARIMA (1,1,1)**

**ARIMA** is ideal for:

* Daily numerical data
* Short-term forecasting
* Data with trends

### ARIMA Components:

* **AR(1)** → Past value dependency
* **I(1)** → Differencing for trend removal
* **MA(1)** → Past error correction

### Why ARIMA?

* High accuracy for short forecasts
* Easy to interpret
* Suitable for multiple service-level time series

---

##  Step 7: Forecasting the Next 7 Days

Models were built for each service:

###  Local Route Forecast

<img width="847" height="713" alt="image" src="https://github.com/user-attachments/assets/8e2ec1b9-32dd-47e1-a11f-20653de08733" />

###  Light Rail Forecast

<img width="758" height="703" alt="image" src="https://github.com/user-attachments/assets/d0f21091-9a29-4e65-bdd3-21918a91f615" />

Models built using:

model = ARIMA(series, order=(1,1,1))
model_fit = model.fit()
forecast = model_fit.forecast(steps=7)

Generated:

* 7 forecasted values
* Trend charts
* Comparison with historical data

---

#  Key Insights 

 **1. Local Route has the highest passengers**, so it is used the most.
 **2. School Service is very busy on weekdays** because of students.
 **3. Peak Service goes up and down**, linked to office travel.
 **4. Rapid Route is steady**, meaning consistent daily use.
 **5. Many services rise and fall together**, showing similar patterns.

---

#  Repository Structure

 Transport-Passenger-Forecasting
┣  README.md
┣  EDA.ipynb
┗  .gitignore

---

#  Real-World Applications

* Public transport planning
* Demand prediction
* Smart-city analytics
* Scheduling optimization
* Resource allocation

---

#  Conclusion

This project demonstrates an end-to-end time series pipeline:

 Data understanding
 Cleaning
 Visual EDA
 ARIMA forecasting
 Insights for decision-making

ARIMA provides reliable **short-term passenger demand** forecasting.

---

#  Author

**Name:** MOHAMADU RIYAS S
**Role:** Data Science
**GitHub:** *https://github.com/MohamaduRiyas/public-transport-time-series-forecast*
**Tools:** Python | EDA | Time Series | ARIMA

---

