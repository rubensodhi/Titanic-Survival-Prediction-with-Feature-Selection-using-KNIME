
# Predicting Titanic Passenger Survival Using KNIME

This project utilizes the KNIME Analytics Platform to build machine learning models that predict Titanic passenger survival based on provided demographic and ticket information. The analysis explores preprocessing, feature engineering, class balancing, feature selection, and model evaluation techniques.

## Overview

![image](https://github.com/user-attachments/assets/402eb761-197d-4109-9170-ece089058f4a)

The Titanic dataset contains information on 1,268 passengers, including:
- **Continuous variables**: `Age`, `Fare`, `Salary`, and `FamilySize`
- **Categorical variables**: `Sex`, `Embarked`, `Ticket`, `Cabin`, and `Job`

The objective is to predict the binary outcome: **`Survived`** (1 for survived, 0 for not survived).



## Key Steps
The data was first joined then partitioned:

![image](https://github.com/user-attachments/assets/e8c7e488-9bf8-4e3c-b47a-c0e42ff78de2)


### 1. Data Cleaning and Preprocessing

![image](https://github.com/user-attachments/assets/347735f0-72f1-46a0-93e4-2503543cb8ba)


- **Missing Values**: Imputed using median for numerical and mode for categorical variables.

![image](https://github.com/user-attachments/assets/f4119426-d220-41d3-8125-25829af842ef)

- **Outlier Removal**: Identified and addressed using KNIME's Numeric Outlier Node.

- **Normalization**: Min-Max scaling applied to continuous variables.

- **Feature Engineering**:
  - `FamilySize`: Combined `SibSp` and `Parch`, with log transformation applied.
  
  ![image](https://github.com/user-attachments/assets/9be310c7-eac3-44e6-b5d4-d79aed159879)

  ![image](https://github.com/user-attachments/assets/7d211cb8-a32e-4297-8167-a03696629b58)

  - Categorical variables encoded using one-hot encoding.
  - `Age` grouped into categories (e.g., Child, Adult).
  
  ![image](https://github.com/user-attachments/assets/7147e380-59f1-401e-8992-a35b2627f1fd)


### 2. Feature Selection

![image](https://github.com/user-attachments/assets/3e2e7335-4357-4178-a1cb-7536969c0af2)


- **Genetic Algorithm**: Used to identify the most important features based on Cohen's Kappa.
- Selected features include `log(FamilySize)`, `log(Salary)`, `Sex`, and age group categories.

### 3. Model Training

![image](https://github.com/user-attachments/assets/11bdff76-23de-4699-8df9-6428e31f62d2)


- Two models were implemented:
  - **Logistic Regression**: For interpretability and efficiency.
  - **Random Forest**: For capturing non-linear relationships and feature importance.
- **Class Balancing**: Applied SMOTE to address imbalance in the `Survived` column.
- **Cross-Validation**: 10-fold cross-validation to ensure robust performance estimates.

### 4. Model Evaluation
- Models were evaluated on testing data using:
  - **Accuracy**
  - **Cohen's Kappa**
  - **ROC-AUC**
  - **Error Percentage**

## Results

![image](https://github.com/user-attachments/assets/effebf2b-4be5-4cd2-a1d6-e8edb45bfda7)


- **Key Insights**:
  - Logistic Regression performed better in terms of accuracy but was slightly less robust in handling non-linearities compared to Random Forest.
  - Feature engineering and class balancing significantly improved both models.

## How to Use

1. Clone this repository:
   ```bash
   git clone <repository-url>
   ```
2. Open the workflow file (`Titanic_LogisticRegression_and_RandomForest_four_workflows.knwf`) in KNIME.
3. Ensure datasets (`titanic_ticket_data.csv` and `titanic_personal_data.csv`) are in the same directory as the workflow.
4. Execute the workflow and analyze the results.

## Dependencies

- KNIME Analytics Platform
- Required KNIME Extensions:
  - Python Integration
  - Machine Learning
  - Data Mining

---

This README provides a high-level summary of the project. For detailed documentation, please refer to the complete report.
