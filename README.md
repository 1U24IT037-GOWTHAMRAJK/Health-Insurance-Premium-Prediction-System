# 🏥 Health Insurance Premium Prediction

A Machine Learning project that predicts individual health insurance charges based on factors such as **age, BMI, smoking status, number of children, gender, and region**.

---

## 📌 Project Overview

Health insurance charges can vary significantly from person to person depending on different personal and lifestyle factors.

This project uses **Exploratory Data Analysis (EDA)** and **Linear Regression** to understand the factors affecting insurance charges and build a model that can predict the expected premium for a new individual.

The project focuses on identifying the most influential factors and evaluating how well a machine learning model can estimate insurance charges.

---

## 🎯 Objectives

* Analyze the factors that influence health insurance charges
* Perform data cleaning and exploratory data analysis
* Identify relationships between customer attributes and insurance charges
* Encode categorical variables for machine learning
* Build and compare multiple Linear Regression models
* Evaluate model performance using **R² Score** and **Mean Squared Error**
* Predict insurance charges for new, unseen individuals

---

## 📊 Dataset

The dataset contains **1,338 records and 7 columns**.

| Feature    | Description                                  |
| ---------- | -------------------------------------------- |
| `age`      | Age of the insured individual                |
| `sex`      | Gender of the individual                     |
| `bmi`      | Body Mass Index                              |
| `children` | Number of dependent children                 |
| `smoker`   | Smoking status                               |
| `region`   | Residential region                           |
| `charges`  | Annual health insurance charges — **Target** |

---

## 🛠️ Technologies Used

* **Python 3**
* **Pandas** — Data manipulation
* **NumPy** — Numerical operations
* **Matplotlib** — Data visualization
* **Seaborn** — Statistical visualization
* **Scikit-learn** — Machine learning and evaluation
* **Google Colab** — Development environment

---

## 🔄 Project Workflow

### 1. Data Loading & Understanding

* Loaded the insurance dataset
* Checked dataset dimensions using `.shape`
* Examined data types using `.info()`
* Generated statistical summaries using `.describe()`
* Checked for missing values

**Result:** No missing values were found.

---

### 2. Data Cleaning

During data cleaning, **1 duplicate record** was identified and removed.

```text
Original records : 1338
After cleaning   : 1337
```

This ensured that duplicate observations did not affect the analysis and model training.

---

## 🔍 Exploratory Data Analysis

### 📈 Univariate Analysis

The dataset was analyzed feature by feature to understand its overall distribution.

Key observations:

* Age ranges from approximately **18 to 64 years**
* Gender distribution is almost balanced
* BMI is centered around approximately **30**
* Most individuals are **non-smokers**
* The **Southeast** region has the highest number of records
* Insurance charges are **right-skewed**, with some high-value observations

---

### 📊 Bivariate Analysis

Relationships between individual features and insurance charges were analyzed.

Key findings:

* Insurance charges generally increase with **age**
* **Smoking status** has the strongest relationship with insurance charges
* Smokers generally have significantly higher charges than non-smokers
* BMI has a positive relationship with charges
* Gender has a comparatively smaller effect
* Regional differences are relatively limited compared with smoking status

---

### 🔗 Correlation Analysis

| Feature Pair   | Correlation |
| -------------- | ----------: |
| Age vs Charges |        0.30 |
| BMI vs Charges |        0.20 |
| Age vs BMI     |        0.11 |

The analysis indicates that **age and BMI have positive relationships with insurance charges**, although their individual correlations are not strong.

---

## ⚙️ Data Preprocessing

Before training the models:

* Categorical features were converted into numerical values using **One-Hot Encoding**
* `drop_first=True` was used to avoid redundant dummy variables
* The dataset was divided into:

  * **70% Training Data**
  * **30% Testing Data**

Categorical features:

```text
sex
smoker
region
```

---

## 🤖 Model Building

Three Linear Regression models were developed to understand how adding features affects prediction performance.

| Model       | Features         |  Train R² |   Test R² |       Test MSE |
| ----------- | ---------------- | --------: | --------: | -------------: |
| Model 1     | Age              |     0.082 |     0.097 |     1.55 × 10⁸ |
| Model 2     | Age + BMI        |     0.099 |     0.140 |     1.47 × 10⁸ |
| **Model 3** | **All Features** | **0.736** | **0.772** | **3.89 × 10⁷** |

### 🏆 Best Model

**Model 3 — Linear Regression with all available features** was selected as the final model.

It achieved:

* **Training R²:** 0.736
* **Testing R²:** 0.772
* **Testing MSE:** 3.89 × 10⁷

The similar training and testing performance indicates that the model generalizes reasonably well to unseen data.

---

## 🧮 Final Regression Equation

```text
Charges = -11516.78
        + (251.25 × age)
        + (328.38 × bmi)
        + (522.16 × children)
        + (-111.91 × sex_male)
        + (22874.45 × smoker_yes)
        + (-465.75 × region_northwest)
        + (-936.10 × region_southeast)
        + (-765.58 × region_southwest)
```

The coefficients provide an indication of how each feature contributes to the predicted insurance charges while holding the other features constant.

---

## 🔮 Prediction on New Data

The final model was tested with three new individuals who were not part of the training or testing dataset.

| Age | Smoker |  BMI | Region    | Predicted Charge |
| --: | ------ | ---: | --------- | ---------------: |
|  30 | No     | 25.0 | Southwest |        ₹3,464.60 |
|  50 | Yes    | 35.0 | Southeast |       ₹35,409.69 |
|  22 | No     | 20.0 | Northwest |          ₹634.70 |

### 📌 Prediction Insight

The predictions follow the patterns identified during EDA.

The **50-year-old smoker with a BMI of 35** receives the highest predicted charge, while the **22-year-old non-smoker with a BMI of 20** receives the lowest predicted charge.

This further highlights the strong influence of **smoking status**, along with age and BMI.

---

## 📈 Key Insights

### 🥇 Smoking Status

Smoking is the most influential factor in the model. Smokers generally have substantially higher insurance charges.

### 👤 Age

Insurance charges tend to increase as age increases.

### ⚖️ BMI

BMI has a positive relationship with insurance charges, although its impact is smaller than smoking status.

### 👶 Number of Children

The number of children has a relatively smaller effect compared with age, BMI, and smoking status.

### 🌍 Region & Gender

Gender and region have comparatively smaller effects on the predicted charges in this dataset.

---

## ✅ Conclusion

This project demonstrates how Machine Learning can be used to estimate health insurance charges from personal and lifestyle attributes.

The final **Linear Regression model achieved a Test R² of approximately 0.77**, indicating that the selected features explain a substantial portion of the variation in insurance charges.

The analysis shows that **smoking status is the strongest factor**, followed by age and BMI, while gender, region, and number of children have comparatively smaller effects.

Overall, the project provides a practical example of using **Python, EDA, data preprocessing, and Machine Learning** to solve a real-world prediction problem.

---

## 🚀 How to Run

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd health-insurance-premium-prediction
```

### 2. Open the Notebook

Open:

```text
Health_Insurance_Premium_Prediction_System.ipynb
```

using **Google Colab** or Jupyter Notebook.

### 3. Load the Dataset

Place `insurance_prediction.csv` in the required location and update the dataset path in the notebook if necessary.

Example:

```python
data = pd.read_csv("insurance_prediction.csv")
```

### 4. Run the Notebook

Run all cells sequentially to perform:

```text
Data Loading
     ↓
Data Cleaning
     ↓
EDA
     ↓
Preprocessing
     ↓
Model Training
     ↓
Model Evaluation
     ↓
Prediction
```

---

## 📁 Project Structure

```text
Health-Insurance-Premium-Prediction/
│
├── Health_Insurance_Premium_Prediction_System.ipynb
├── insurance_prediction.csv
└── README.md
```

> Note: The dataset may be excluded from the repository depending on its source and usage permissions.

---

## 🔮 Future Improvements

The project can be improved further by:

* Testing **Random Forest Regression**
* Implementing **Gradient Boosting**
* Experimenting with **XGBoost**
* Performing **hyperparameter tuning**
* Using **cross-validation**
* Applying appropriate feature scaling
* Checking regression assumptions
* Investigating multicollinearity
* Applying log transformation to the target variable
* Comparing multiple regression algorithms to identify the best-performing model

---
