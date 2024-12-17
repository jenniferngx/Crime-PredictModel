# 🔎 **Crime Rate Prediction Using Lasso Regression**  

Building a Predictive Model to Analyze Violent Crime Rates Across US Communities

Read my [full paper](https://drive.google.com/file/d/1YfqSZZswrhX0DkUvjg3ANmLg77Y7sicB/view)

## 🚀 **Project Overview**  

This project develops a **predictive regression model** to estimate violent crime rates using socio-economic and criminal justice data from **1,994 US communities**. The data combines the 1990 US Census, Law Enforcement Management Statistics, and FBI Uniform Crime Reporting.  

The goal is twofold:  
1. Build the most accurate model for predicting crime rates.  
2. Identify the most significant predictors influencing violent crime.  

To handle the challenges of **missing data**, **multicollinearity**, and a high number of predictors (125 variables), we employed:  
- **Ridge Regression**  
- **Lasso Regression**  
- **Principal Component Regression (PCR)**  

Through cross-validation, **Lasso Regression** emerged as the best-performing model with the lowest prediction error.

## 🔍 **Key Objectives**  
1. Preprocess the dataset by addressing missing values and multicollinearity.  
2. Apply Ridge Regression, Lasso Regression, and PCR to predict violent crime rates.  
3. Use **5-fold cross-validation** for model comparison and **10-fold cross-validation** to tune hyperparameters.  
4. Identify the **most influential predictors** for violent crime rates.  
5. Generate predictions for a test dataset.  

## 🛠️ **Tools & Technologies**  
- **Programming Language**: R  
- **Libraries**: `glmnet`, `dplyr`, `pls`, `ggplot2`  
- **Techniques**: Ridge Regression, Lasso Regression, Principal Component Regression (PCR), Cross-Validation  

## 🧩 **Methodology**  

### **1. Data Preprocessing**  
- Removed columns with **85% missing values** (columns 100–125).  
- Handled multicollinearity by removing derived columns (columns 84 and 88).  
- Log-transformed the target variable **violentCrimesPerPop** to address skewness.  
- Removed remaining missing values and categorical variables (e.g., `STATE`).  

### **2. Model Implementation**  
- **Ridge Regression**: Reduces overfitting by shrinking coefficients.  
- **Lasso Regression**: Performs variable selection by shrinking some coefficients to zero.  
- **Principal Component Regression (PCR)**: Reduces dimensionality by using principal components.  

### **3. Model Comparison**  
- Used **5-fold cross-validation** to compute the Mean Squared Error (MSE) for each model:  
   - **Ridge Regression MSE**: 214,075.8  
   - **Lasso Regression MSE**: 204,842.7 (Best Performing Model)  
   - **PCR MSE**: 229,196.4  

### **4. Final Model: Lasso Regression**  
- Used **10-fold cross-validation** to determine the optimal penalty parameter (**λ**).  
- Identified significant predictors based on non-zero coefficients.

## 📊 **Results & Insights**  

### **Key Predictors of Violent Crime**  

| Predictor                | Coefficient | Impact                              |
|--------------------------|-------------|------------------------------------|
| `pctKidsBornNevrMar`     | +48.81      | % of kids born to never-married mothers ↑ |  
| `MalePctDivorce`         | +23.33      | % of divorced males ↑              |  
| `pctVacantBoarded`       | +4.52       | % of vacant boarded-up housing ↑   |  
| `pctKids2Par`            | -11.05      | % of kids in two-parent families ↓ |  
| `racePctWhite`           | -7.39       | % of white population ↓            |  
| `pctWorkMom`             | -2.69       | % of working mothers ↓             |  

- **Positive Coefficients**: Socio-economic challenges (e.g., single-parent families, urbanization, vacant housing) are associated with **higher crime rates**.  
- **Negative Coefficients**: Indicators of **stability** (e.g., two-parent families, housing occupancy) are associated with **lower crime rates**.  



