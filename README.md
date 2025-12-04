# Telecom Traffic Forecasting With Linear Regression

Forecasting telecom Arrivals and Departures traffic using linear regression and the Moore–Penrose pseudo inverse. Includes a full 100-period prediction pipeline.


![Python](https://img.shields.io/badge/Python-3.x-blue.svg)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)
![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)


This project builds a simple and interpretable forecasting model for telecom traffic using a real dataset.  
We focus on two important signals that describe network behavior:

- **Arrivals** (connected users)  
- **Departures** (disconnected users)

We use **Linear Regression**, solved with the **Moore–Penrose pseudo inverse**, to create a baseline for forecasting.  
The goal is to analyze the traffic and forecast the next **100 future periods**.

---

## Dataset Description

The dataset contains telecommunication traffic measurements collected over time.  
Each record includes:

- `Season` – seasonal index (1 to 4)  
- `DayOfWeek` – day index within the week (1 to 7)  
- `Period` – time slot in the day (1 to 24)  
- `PricePerGB` – price category for data usage (1 or 2)  
- `Arrivals` – connected traffic  
- `Departures` – disconnected traffic  

These features help describe how network load changes throughout the day and week.

---

## What This Project Does

The main notebook walks through:

1. Loading and inspecting the telecom dataset  
2. Cleaning and preparing the data  
3. Creating the feature matrix:
   - Period as numeric  
   - One hot encoding for Season, DayOfWeek, PricePerGB  
   - Bias term  
4. Splitting the data in time order (80% training, 20% testing)  
5. Training a linear regression model using the pseudo inverse  
6. Evaluating performance with MAE and RMSE  
7. Plotting predictions and residuals  
8. Building a future timeline for the next 100 periods  
9. Forecasting Arrivals and Departures for those periods  
10. Saving the forecasts into a CSV file

This gives a clean baseline model before trying more advanced forecasting methods.

---

## Method Overview

### Linear Regression Model

We model the predictions as:

$$
\hat{y} = X \beta
$$

The model finds β by minimizing the squared error:

$$
\min_{\beta} \lVert X\beta - y \rVert^2
$$

Using the Moore–Penrose pseudo inverse, the solution is:

$$
\beta = X^{+} y
$$

This gives a direct, closed-form solution without iterative training.

---

## One Hot Encoding

Categorical variables are encoded as binary columns so the model can treat each category separately.  
This avoids misleading numeric order relationships.

---

## Time-Based Train/Test Split

Since this is time-dependent data, we keep the original order and split like this:

- First 80% → training  
- Last 20% → testing  

This simulates a real forecasting scenario where the future cannot influence the past.

---

## Evaluation Metrics

We use two standard metrics.

**Mean Absolute Error (MAE)**

$$
\text{MAE} = \frac{1}{n} \sum_{i=1}^{n} | y_i - \hat{y}_i |
$$

**Root Mean Squared Error (RMSE)**

$$
\text{RMSE} = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}
$$

MAE measures the average error, while RMSE increases the penalty for large mistakes.

---

## Repository Structure

```text
.
├─ README.md
├─ LICENSE
├─ requirements.txt
├─ .gitignore
├─ data/
│  └─ telecom_traffic_data.csv
├─ notebooks/
│  └─ telecom_linear_regression_pinv.ipynb
└─ results/
   └─ telecom_forecasting_linear_regression_100periods.csv
```


## Installation

### 1. Clone the repository
```bash
git clone https://github.com/Zahid-Alabadllah/TELECOMMUNICATION-TRAFFIC-AND-FORECASTING.git
cd TELECOMMUNICATION-TRAFFIC-AND-FORECASTING 
```
### 2. Install dependencies
```bash
pip install -r requirements.txt 
```

## Quickstart

You can run the full forecasting workflow in a few steps.

### 1. Open the notebook

Start Jupyter Notebook:

```bash
jupyter notebook
```

Then open:
```bash
notebooks/telecom_linear_regression_pinv.ipynb
```

### 2. Run all cells

Run the notebook from top to bottom.
It will:

● Load the dataset

● Build the feature matrix

● Train the linear regression model

● Evaluate Arrivals and Departures

● Build the future timeline

● Generate the next 100-period forecasts

● Save the results to the results/ folder

## 3. View the generated forecasts

The final predictions are saved as:
```bash
results/telecom_forecasting_linear_regression_100periods.csv
```
## Contact
**Author:** Zahid Sami Alabadllah  

MSc High Performance and Cloud Computing, KFUPM

BSc Computer Science, KFUPM

Email: Zahid.Alabadllah@hotmail.com

LinkedIn: https://www.linkedin.com/in/zahid-alabadllah

GitHub: https://github.com/Zahid-Alabadllah


