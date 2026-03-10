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
* Handle missing values: we checked for missing and null values in the datset and found some in the bmi column
* Encode categorical variables: We use the Label encoding technique to convert categorical (text) data into numerical values so algorithms can process them.
* Detected outliers: A boxplot and a function was created to detect outliers in the numericl variables in the dataset and we found outliers in avg_glucose_level, bmi columns, then the outliers were replaced with the up and low whiskers respectively.
* feature scaling
* Checked for class imbalance in the Dataset: Stroke cases are typically much fewer than non-stroke cases, this leads to class imbalance, which affected model performance.

### 3.2 Data Visualization
#### Stroke Distribution
  ![image alt](https://github.com/ifyyoyo/Healthcare-Data-Science-Project-Stroke-Risk-Prediction/blob/a575f92ac3fe844b1737975ce818d0bded178b43/Screenshot%202026-03-10%20110520.png)

Observation:
* Stroke cases are typically much fewer than non-stroke cases.
* This leads to class imbalance, which affects model performance.

#### Age,Bmi and Average Glucose Level Vs Stroke
  <img width="2020" height="601" alt="image" src="https://github.com/user-attachments/assets/76bfe728-8465-4e7f-9783-c9679d0734c4" />

* This pattern suggests a strong positive relationship between age and stroke risk, indicating that stroke probability increases significantly with age 
* This suggests that elevated glucose levels may be associated with increased stroke risk, potentially reflecting underlying metabolic conditions such as diabetes.  
* High BMI (obesity) contributes to risk but may be weaker than age

#### Hypertension, Heart Disease and Gender Vs Stroke 
  <img width="1705" height="447" alt="image" src="https://github.com/user-attachments/assets/d6822c1a-bda7-4f00-9bd5-9545a671a000" />

* Individuals with hypertension show a relatively higher proportion of stroke cases compared to those without hypertension
* The proportion of stroke cases is noticeably higher among individuals with heart disease compared to those without it.
* Based on the observed distribution, gender does not appear to exhibit a strong direct association with stroke occurrence in this dataset.

#### Smoking statues, Work type and Residence type Vs Stroke occurance
  <img width="1705" height="447" alt="image" src="https://github.com/user-attachments/assets/8ac2171e-b3f2-41ce-b6f0-64e33d45c731" />

* Smoking history increases stroke risk.
* Individuals in private and self-employed categories likely represent the adult working population, which explains the higher number of stroke occurrences in these groups.
* People in urban areas are more likely to have stroke as compared to the rural areas.

### 4. FEATURE CORRELATION
A correlation heatmap was used to visualize the relationships between different features in the dataset.From the analysis, age shows a relatively strong positive correlation with ever_married (0.68) and moderate correlations with hypertension, heart disease, and BMI, indicating that these health factors tend to increase with age.

### 5. Predictive Modeling
#### 5.1 FEATURE SCALING
Standardized the numerical values of features with standardscaler so that they are on a similar scale.

#### 5.2 TRAIN-TEST-SPLIT
Dataset was divide into training data (to build the model) and testing data (to evaluate the model).

#### 5.3 TRAINING & TESTING OF MODELS
LogisticRegression()
KNeighborsClassifier()
DecisionTreeClassifier()
RandomForestClassifier()
SVC()
GradientBoostingClassifier()
XGBClassifier()
The above models were trained and tested but a cross validation was first of all built to rule out overfitting and underfitting the of models.
Due to the imbalanced state of the dataset, we trained the models with, firstly with the preprocessed imbalanced set and with a balanced dataset were we used SMOTE to balance only the training Datasets 










