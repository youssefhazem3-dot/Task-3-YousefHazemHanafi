# California Housing Price Prediction

## Project Overview

This project is part of the **DecodeLabs Data Science Internship**.  
The goal of this project is to analyze the California Housing dataset and build regression models that can predict the median house value of a housing district based on location, population, income, and housing-related features.

Unlike classification projects, this is a **regression problem** because the target variable, `median_house_value`, is a continuous numerical value.

---

## Dataset

The dataset used in this project is the California Housing dataset.

**Dataset Link:**  
https://raw.githubusercontent.com/ageron/handson-ml/master/datasets/housing/housing.csv

### Dataset Shape

- Rows: **20,640**
- Columns: **10 original columns**

### Target Column

| Column | Description |
|---|---|
| `median_house_value` | The median house value for a housing district |

### Main Features

| Feature | Description |
|---|---|
| `longitude` | Longitude coordinate of the housing district |
| `latitude` | Latitude coordinate of the housing district |
| `housing_median_age` | Median age of houses in the district |
| `total_rooms` | Total number of rooms in the district |
| `total_bedrooms` | Total number of bedrooms in the district |
| `population` | Total population of the district |
| `households` | Number of households in the district |
| `median_income` | Median income of residents |
| `ocean_proximity` | Category describing how close the district is to the ocean |

---

## Project Objectives

The main objectives of this project are to:

- Load and understand the dataset structure
- Identify columns, data types, missing values, and dataset size
- Clean and prepare the data for analysis
- Perform exploratory data analysis
- Visualize trends, relationships, and outliers
- Apply feature engineering
- Build regression models to predict house prices
- Compare model performance using regression metrics

---

## Project Workflow

### 1. Data Collection and Understanding

The dataset was loaded from an online CSV source using Pandas.  
Initial exploration included checking:

- Dataset shape
- Column names
- Data types
- Missing values
- Summary statistics
- First few rows of the dataset

### 2. Data Cleaning and Preprocessing

The dataset contained missing values in the `total_bedrooms` column.  
These missing values were handled by filling them with the median value of the column.

The categorical column `ocean_proximity` was converted into numerical dummy variables using one-hot encoding so it could be used in machine learning models.

### 3. Exploratory Data Analysis

Several EDA steps were performed to understand the dataset better, including:

- Checking numerical feature distributions
- Detecting outliers using boxplots
- Analyzing the relationship between location and house value
- Comparing house value across ocean proximity categories
- Studying feature correlations
- Visualizing actual patterns in the housing data

### 4. Feature Engineering

New features were created to improve model performance:

| New Feature | Formula |
|---|---|
| `rooms_per_household` | `total_rooms / households` |
| `bedrooms_ratio` | `total_bedrooms / total_rooms` |
| `population_per_household` | `population / households` |

These engineered features provide more meaningful information than the raw totals alone.

### 5. Model Building

Three regression models were trained and evaluated:

- Linear Regression
- Decision Tree Regressor
- Random Forest Regressor

### 6. Model Evaluation

The models were evaluated using:

- **MAE**: Mean Absolute Error
- **RMSE**: Root Mean Squared Error
- **R² Score**: Measures how much variance in the target variable is explained by the model

---

## Model Results

| Model | MAE | RMSE | R² Score |
|---|---:|---:|---:|
| Linear Regression | 50,888.66 | 72,668.54 | 0.5970 |
| Decision Tree Regressor | 42,539.86 | 63,767.77 | 0.6897 |
| Random Forest Regressor | 34,211.10 | 52,210.92 | 0.7920 |

---

## Best Model

The **Random Forest Regressor** achieved the best performance:

- Lowest MAE
- Lowest RMSE
- Highest R² Score

This means Random Forest was the most effective model among the tested algorithms for predicting median house values.

---

## Key Insights

- House values vary significantly based on geographical location.
- Inland areas generally have lower median house values compared to areas near the ocean or bay.
- The `median_income` feature is one of the strongest indicators of house value.
- Outliers exist in features such as `population`, `total_rooms`, `households`, and `median_house_value`, but they were kept because they may represent real housing districts.
- Engineered features such as `rooms_per_household` and `population_per_household` help provide better information for prediction.
- Random Forest performed better than Linear Regression and Decision Tree because it can capture more complex non-linear patterns.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

---

## How to Run the Project

1. Clone this repository:

```bash
git clone https://github.com/your-username/california-housing-price-prediction.git
```

2. Open the project folder:

```bash
cd california-housing-price-prediction
```

3. Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

4. Open the notebook:

```bash
jupyter notebook DecodeLabs_Project3.ipynb
```

5. Run all cells in order.

---

## Project Files

```text
DecodeLabs_Project3.ipynb   # Main notebook
README.md                   # Project documentation
```

---

## Future Improvements

Possible improvements for this project include:

- Applying cross-validation
- Tuning Random Forest hyperparameters
- Testing additional models such as Gradient Boosting or XGBoost
- Handling the capped values in `median_house_value`
- Adding more geospatial analysis
- Applying feature scaling for linear models
- Deploying the model as a simple web app

---

## Conclusion

This project successfully applies the main steps of a data science workflow: data understanding, cleaning, exploratory analysis, visualization, feature engineering, model building, and evaluation.

The Random Forest Regressor achieved the best results and provided a strong baseline model for predicting California housing prices.
