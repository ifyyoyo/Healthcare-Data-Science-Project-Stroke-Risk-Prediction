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

data:image/png;base64,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AEgiCgCAQhQAAElEAQBQiAIAIIkoAAAKUQAAJBEFAEAhCgCAJKIAAChEAQCQRBQAAIUoAACSiAIAoBAFAECSpO1ADq7VDtY0AIC+dqB/b9eqqqoOzlQAgIHE0wcAQBJRAAAUogAASCIKAIBCFAAASUQBAFCIAgAgiSgAAApRAAAkEQUH7Pnnn88ll1ySKVOm5NRTT80111yTTZs2JUnWrl2b8847L5MmTcr06dOzbNmyJs92cOru7s7s2bNz7bXX9txmbZpv8+bNueaaa3LyySfnpJNOypw5c/KPf/wjifVptj/+8Y+58MILM3ny5EybNi033XRT3n333STWppk2bdqUGTNm5Mknn+y5bV/rsWLFisyYMSMnnHBCZs6cmTVr1hzYSSv22zvvvFOdeuqp1a233lpt37692rRpU3X55ZdXV155ZbV58+ZqypQp1T333FPt2LGjevzxx6tJkyZVa9eubfa0B51bbrmlOuqoo6r58+dXVVVZmxbxzW9+s5o7d261ZcuW6s0336y+/e1vV1dccYX1abLu7u7q1FNPrX7+859X3d3d1auvvlp95StfqX76059amybq6uqqTj/99OrII4+sVq9eXVXVvvey1atXV5MmTaq6urqqd999t7rrrruqk08+uXr77bf3+7weKTgAr7zySo466qjMnTs3w4YNy5gxY3L++efnqaeeyiOPPJJDDjkkF154Ydra2jJ16tScffbZ+eUvf9nsaQ8qTzzxRB555JF8+ctf7rnN2jTfc889l7Vr12bhwoUZPXp0Ro4cmRtvvDFXX3219WmyLVu25LXXXkuj0UhV/iucer2ejo4Oa9MkK1asyNVXX52rrrpqj9v3tR7Lli3LmWeemRNPPDFDhw7NxRdfnDFjxuShhx7a73OLggPw+c9/PnfeeWeGDBnSc9vDDz+cY445Ji+99FKOPPLIPY6fMGFCnn/++f6e5qC1cePGLFiwID/5yU/S0dHRc7u1ab5nnnkmEyZMyNKlSzNjxoxMmzYtixYtyrhx46xPk40ZMyYXX3xxFi1alGOPPTannXZaPve5z+Xiiy+2Nk0ybdq0PProoznjjDP2uH1f6/Hyyy9/5PUSBR9SVVW5+eab89vf/jYLFizIW2+9tcdfREnS3t6et99+u0kzHFwajUa++93v5pJLLslRRx21x8esTfNt2bIlL7zwQv7yl79kxYoVWblyZTZs2JD58+dbnyZrNBppb2/PDTfckKeffjoPPvhg/vSnP+W2226zNk0ybty4tLW1ve/2fa1HX6yXKPgQtm7dmnnz5mXVqlW55557MnHixHR0dGTbtm17HLdt27Z84hOfaNIsB5ef/exnGTZsWGbPnv2+j1mb5hs2bFiSZMGCBRk5cmTGjh2b73znO3nsscdSVZX1aaJHH300Dz/8cC644IIMGzYsRxxxRObOnZt7773XtdNi9rUefbFeouAA/fWvf82sWbOydevWLF++PBMnTkySHHnkkXnppZf2OPbll1/OEUcc0YxpDjr3339/fve732Xy5MmZPHlyHnzwwTz44IOZPHmytWkBEyZMSKPRyI4dO3puazQaSZKjjz7a+jTRq6++2vMvDXZpa2vL0KFDXTstZl/rccQRR3zk9RIFB2DLli256KKL8oUvfCGLFy9OZ2dnz8dmzJiR119/PUuWLMmOHTuyevXqrFq1KrNmzWrijAeP3/zmN/nDH/6Qrq6udHV15ayzzspZZ52Vrq4ua9MCTjnllHz2s5/Nddddl7feeiubNm3KzTffnNNPPz1nnXWW9WmiadOm5bXXXssdd9yR7u7u/O1vf8vtt9+es88+27XTYva1Hueee25WrVqV1atXZ8eOHVmyZEk2btyYGTNm7Pc5atWuXzdln+66664sXLgwHR0dqdVqe3xszZo1efbZZ/P9738/L774Yjo7OzNnzpzMnDmzSbMd3Ha9RsHChQuTxNq0gA0bNmThwoV56qmnsn379kyfPj0LFizI6NGjrU+TPf7447nlllvy5z//OaNGjcrXvva1nn9lZW2aa+LEifnFL36Rk08+Ocm+97L7778/t99+ezZs2JAJEybk+uuvz/HHH7/f5xMFAEASTx8AAIUoAACSiAIAoBAFAEASUQAAFKIAAEgiCgCAQhQAAElEAXysrVu3LhMnTsy6des+8lhnnnlmHnjggT6YFdCq3v9/MwLsxa9//etmTwE4yDxSAIPAypUrc/rpp+eUU07J9ddfn61bt+a+++7LBRdckEWLFmXKlCn54he/mLvvvjtLly7Nl770pZx44on53ve+1zPG9OnTc9999zXxqwAONlEAg0BXV1eWLl2aBx54IC+++GJ+8IMfJEl+//vf57DDDsvq1aszb968/PCHP8yTTz6Zhx56KEuWLMny5cvz1FNPNXn2QH8RBTAIXHvttens7MzYsWMzb968rFq1Ko1GIyNGjMhFF12Uer2eadOmpbu7O5deemk6Ojpy7LHH5pOf/GTWr1/f7OkD/UQUwCBw+OGH97w9fvz4vPvuu9m8eXMOOeSQnv8GvF7/j+1g9OjRPcfW6/U0Go3+nSzQNKIABoENGzb0vL1u3bqMGDEinZ2dPUEAkIgCGBR+/OMfZ8uWLfn73/+eW2+9Neeff36zpwS0IFEAg8CkSZPy1a9+NbNmzcpJJ52Uq666qtlTAlpQraqqqtmTAACazyMFAEASUQAAFKIAAEgiCgCAQhQAAElEAQBQiAIAIIkoAAAKUQAAJBEFAEAhCgCAJMn/A8ApX46XDex8AAAAAElFTkSuQmCC

### 4. FEATURE CORRELATION
A correlation heatmap was used to visualize the relationships between different features in the dataset.From the analysis, age shows a relatively strong positive correlation with ever_married (0.68) and moderate correlations with hypertension, heart disease, and BMI, indicating that these health factors tend to increase with age.

### 5. Predictive Modeling
#### 5.1 FEATURE SCALING
Standardized the numerical values of features with standardscaler so that they are on a similar scale.

#### 5.2 TRAIN-TEST-SPLIT
Dataset was divide into training data (to build the model) and testing data (to evaluate the model).

#### 5.3 TRAINING & TESTING OF MODELS
* LogisticRegression()
* KNeighborsClassifier()
* DecisionTreeClassifier()
* RandomForestClassifier()
* SVC()
* GradientBoostingClassifier()
* XGBClassifier()
  
The above models were trained and tested but a cross validation was first of all built to rule out overfitting and underfitting the of models.
Due to the imbalanced state of the dataset, we trained the models with, firstly with the preprocessed imbalanced set and with a balanced dataset were we used SMOTE to balance only the training Datasets.










