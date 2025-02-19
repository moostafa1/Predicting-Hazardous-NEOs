# 🚀 Predicting Hazardous NEOs  
A machine learning project aimed at accurately predicting whether a Near-Earth Object (NEO) is hazardous or not. This is a **critical** task for planetary defense, as identifying dangerous objects early can help prevent potential threats to Earth.  

## 📌 Project Workflow  
### 🔹 Data Processing  
- Cleaned the dataset by **dropping null values**.  
- Removed the `orbiting_body` column, as it had only **one unique value** (not useful for predictions).  

### 🔹 Exploratory Data Analysis (EDA)  
- Visualized **feature distributions** and examined correlations with the target variable `is_hazardous`.  
- Combined `estimated_diameter_min` and `estimated_diameter_max` into a new column **`estimated_diameter`**, representing their **average**.  

### 🔹 Data Preprocessing  
- **Split the data** into training and testing sets.  
- Applied **StandardScaler** on the `relative_velocity` column.  
- Applied **MinMaxScaler** on the `miss_distance` column.  

### 🔹 Model Selection & Training  
- Used **GridSearchCV** to find the best-performing model among:  
  - `RandomForestClassifier` 🌟 (Best Model)  
  - `DecisionTreeClassifier`  
  - `LogisticRegression`  
  - `XGBClassifier`  

## 🏆 Best Model: Random Forest  
The **Random Forest Classifier** achieved **high accuracy and strong performance** across all metrics.  

### 📊 Model Performance  
| Metric | Score |
|---------|--------|
| **Accuracy** | 0.9784 |
| **ROC-AUC Score** | 0.9961 |

#### **Classification Report**  
| Class | Precision | Recall | F1-Score | Support |
|-------|----------|--------|----------|---------|
| **False (Not Hazardous)** | 0.98 | 0.99 | 0.99 | 59002 |
| **True (Hazardous)** | 0.95 | 0.88 | 0.91 | 8633 |
| **Macro Avg** | 0.97 | 0.94 | 0.95 | 67635 |
| **Weighted Avg** | 0.98 | 0.98 | 0.98 | 67635 |

---

## 📈 Understanding the Evaluation Metrics  
### ✅ **Accuracy**  
- Measures **overall correctness** of the model:  
  ```
  Accuracy = (Correct Predictions) / (Total Predictions)
  ```
- **Limitation:** In imbalanced datasets, accuracy may be misleading (e.g., a model predicting "Not Hazardous" 95% of the time will still have high accuracy but poor recall for hazardous cases).

### ✅ **Precision**  
- Measures how many **positive predictions (hazardous NEOs) were actually correct**.  
  ```
  Precision = TP / (TP + FP)
  ```
- **High precision** means **fewer false alarms**.

### ✅ **Recall (Sensitivity)**  
- Measures how many **actual hazardous NEOs were correctly identified**.  
  ```
  Recall = TP / (TP + FN)
  ```
- **High recall** ensures **fewer hazardous NEOs are missed**.

### ✅ **F1-Score**  
- **Harmonic mean** of Precision & Recall, balancing both:  
  ```
  F1 = 2 * (Precision * Recall) / (Precision + Recall)
  ```
- A **good metric** when dealing with imbalanced datasets.

### ✅ **ROC-AUC Score**  
- Measures how well the model distinguishes between **hazardous vs. non-hazardous NEOs**.  
  - **Closer to 1.0** → Better performance.  
  - **Near 0.5** → No better than random guessing.  
- **Doesn't depend on the classification threshold**, so it's great for imbalanced datasets.  

---

## 📌 Conclusion  
- **Random Forest was the best model**, with **high accuracy (97.8%) and an excellent ROC-AUC score (99.6%)**.  
- The **balanced approach** between Precision and Recall ensures we identify hazardous NEOs while minimizing false alarms.  
- The **ROC-AUC metric helped evaluate the model without needing SMOTE**, since it remains unaffected by class imbalance.  

---
