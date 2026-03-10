# Healthcare-Data-Science-Project-Stroke-Risk-Prediction

## 1. Introduction

Stroke is a major global health problem and a leading cause of mortality and disability. Early detection of individuals at high risk enables healthcare providers to intervene through preventive strategies such as lifestyle changes, medication, and routine monitoring.

### The objective of this project is to:
* Perform Exploratory Data Analysis (EDA) to understand factors associated with stroke.
* Develop a classification model to predict stroke risk.
* Provide clinical recommendations for early intervention.
* Discuss ethical considerations in healthcare prediction systems.

### 2. Dataset Description
   | Feature           | Description                                 |
   | ----------------- | ------------------------------------------- |
   | age               | Patient age                                 |
   | gender            | Male/Female                                 |
   | hypertension      | Whether the patient has hypertension        |
   | heart_disease     | Presence of heart disease                   |
   | ever_married      | Marital status                              |
   | work_type         | Employment type                             |
   | Residence_type    | Urban or Rural                              |
   | avg_glucose_level | Average blood glucose level                 |
   | bmi               | Body Mass Index                             |
   | smoking_status    | Smoking behavior                            |
   | stroke            | Target variable (1 = stroke, 0 = no stroke) |


### 3. Exploratory Data Analysis (EDA)
#### 3.1 Data Cleaning
##### Key preprocessing steps taken:
* Handle missing values (BMI).
* Encode categorical variables.
* Detected outliers(avg_glucose_level, bmi).
* Checked for class imbalance in the Dataset.

### 3.2 Stroke Distribution
  ![image alt](https://github.com/ifyyoyo/Healthcare-Data-Science-Project-Stroke-Risk-Prediction/blob/a575f92ac3fe844b1737975ce818d0bded178b43/Screenshot%202026-03-10%20110520.png)

Observation:
* Stroke cases are typically much fewer than non-stroke cases.
* This leads to class imbalance, which affects model performance.

### 3.3 Age,Bmi and Average Glucose Level Vs Stroke
  <img width="2020" height="601" alt="image" src="https://github.com/user-attachments/assets/76bfe728-8465-4e7f-9783-c9679d0734c4" />

* This pattern suggests a strong positive relationship between age and stroke risk, indicating that stroke probability increases significantly with age 
* This suggests that elevated glucose levels may be associated with increased stroke risk, potentially reflecting underlying metabolic conditions such as diabetes.  
* High BMI (obesity) contributes to risk but may be weaker than age

### 3.4 Hypertension, Heart Disease and Gender Vs Stroke 
  <img width="1705" height="447" alt="image" src="https://github.com/user-attachments/assets/d6822c1a-bda7-4f00-9bd5-9545a671a000" />

* Individuals with hypertension show a relatively higher proportion of stroke cases compared to those without hypertension
* The proportion of stroke cases is noticeably higher among individuals with heart disease compared to those without it.
* Based on the observed distribution, gender does not appear to exhibit a strong direct association with stroke occurrence in this dataset.

### 3.5 Smoking statues, Work type and Residence type Vs Stroke occurance
  <img width="1705" height="447" alt="image" src="https://github.com/user-attachments/assets/8ac2171e-b3f2-41ce-b6f0-64e33d45c731" />

* As expected, people who smoke or formerly smoked have more cases of stroke.
* Individuals in private and self-employed categories likely represent the adult working population, which explains the higher number of stroke occurrences in these groups.
* People in urban areas are more likely to have stroke as compared to the rural areas.








