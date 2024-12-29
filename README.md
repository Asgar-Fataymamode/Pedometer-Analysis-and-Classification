# **Daily Pedometer Data Analysis Report**

---

## **1. Introduction**

### **Objective:**
The goal of this project is to **analyze daily pedometer data** and predict whether the user **walked their dogs** (1 = Yes, 0 = No) based on features such as **step count**, **calories burned**, **distance covered**, **weather conditions**, and **day of the week**.

### **Key Questions:**
1. Can we predict whether the user walked their dogs based on pedometer data?  
2. Which features have the most influence on predictions?  
3. How do different machine learning models—**Logistic Regression** and **Random Forest**—perform in terms of accuracy and reliability?  

---

## **2. Dataset Overview**

### **Data Source:**
The dataset contains **223 observations** with 8 variables related to daily activity tracking and weather conditions.

### **Columns:**
- **StepCount**: Number of steps taken in a day.
- **Kcal**: Calories burned.  
- **Miles**: Distance walked in miles.  
- **Weather**: Weather condition (cold, rain, shine).  
- **Day**: Day of the week (e.g., Monday, Tuesday).  
- **Walk**: Whether dogs were walked (1 = Yes, 0 = No).  
- **Steps**: Steps divided by 1000 for scaling.  
- **Details**: Additional notes about the day.  

### **Preprocessing Steps:**
- Encoded **categorical variables** (e.g., Weather and Day) using **One-Hot Encoding**.  
- Filled any **missing values** with suitable defaults or removed incomplete rows.  
- Scaled numerical features like **StepCount**, **Kcal**, and **Miles** for better model performance.  

---

## **3. Exploratory Data Analysis (EDA)**

### **Key Insights:**
1. **Walking Patterns:**
   - Higher **step counts**, **calories burned**, and **miles covered** correlate with dog-walking days.  
   - Most dog-walking days occurred under **shine** weather conditions.  

2. **Weather Trends:**
   - Weather impacted walking behavior, with **cold and rainy** days associated with fewer walks.  

3. **Day of the Week:**
   - Walks were more frequent during weekends (Saturday and Sunday).  

4. **Distributions:**
   - **StepCount** ranged widely, with averages higher on dog-walking days.  
   - **Calories burned** followed a similar trend, reflecting activity levels.  

### **EDA Visualizations:**
- Distributions of **StepCount** and **Kcal** by walking status.  
- Boxplots showing weather and day-of-week effects.  
- Scatterplots revealing correlations between **miles walked** and **step count**.  
- Pie chart illustrating walking frequency based on weather conditions.  

---

## **4. Modeling Approach**

### **Feature Engineering:**
- Encoded categorical variables (**Weather** and **Day**) using **One-Hot Encoding**.  
- Scaled numerical features like **Steps**, **Kcal**, and **Miles** using **StandardScaler**.  

### **Models Trained:**
1. **Logistic Regression**:  
   - Linear model optimized for binary classification.  
2. **Random Forest Classifier**:  
   - Ensemble method designed to capture non-linear relationships.  

### **Training and Testing Split:**
- Training size: **178 samples** (80%).  
- Validation size: **45 samples** (20%).  

---

## **5. Model Evaluation**

### **Logistic Regression Results:**
- **Accuracy:** **73.3%**  
- **Precision, Recall, and F1-scores:**
- **Class 0 (No Walk):** F1 = **0.84**  
- **Class 1 (Walk):** F1 = **0.25**  
- **ROC-AUC Score:** **0.744**  

**Observations:**
- Logistic Regression performed reasonably well for predicting **no walks** (Class 0) but struggled with predicting **walks** (Class 1).  
- The imbalance between classes caused the model to favor the majority class (**No Walk**) at the expense of the minority class (**Walk**).  

---

### **Random Forest Results:**
- **Accuracy:** **78.0%**  
- **Precision, Recall, and F1-scores:**
- **Class 0 (No Walk):** F1 = **0.84**  
- **Class 1 (Walk):** F1 = **0.62**  
- **ROC-AUC Score:** **0.794**  

**Observations:**
- Random Forest performed better than Logistic Regression, achieving higher accuracy and better recall for the minority class (**Walk**).  
- It effectively captured non-linear relationships between features, particularly the influence of **weather** and **step count**.  

---

### **Model Comparison:**

| Metric                  | Logistic Regression | Random Forest |
|-------------------------|---------------------|---------------|
| **Accuracy**            | 73.3%               | **78.0%**     |
| **F1-Score (Avg)**      | 65%                 | **77%**       |
| **ROC-AUC (Avg)**       | 0.744               | **0.794**     |
| **Misclassification**   | Over-predicts No Walk | Balanced predictions |

**Key Finding:**  
The **Random Forest Classifier** outperformed **Logistic Regression**, particularly in identifying **walking days**. It achieved a **higher recall (57%)** for the minority class, making it more reliable for practical applications.

---

## **6. Observations**

### **Key Observations:**
1. **Random Forest** delivered **78% accuracy** and better balance across both classes, making it more reliable for prediction.  
2. **Logistic Regression** struggled with class imbalance, favoring the majority class (**No Walk**) and showing low recall for minority predictions.  
3. **Step Count**, **Calories Burned**, and **Weather** were the most influential predictors, highlighting the relationship between activity levels and dog walking.  

---

## **7. Conclusion**

This project successfully developed models to predict whether the user walked their dogs based on pedometer data, achieving **78% accuracy** with the **Random Forest Classifier**.

### **Key Takeaways:**
- **EDA** highlighted patterns in activity levels and weather impacts on walking behavior.  
- **Random Forest** outperformed **Logistic Regression**, especially in handling class imbalance.  
- **ROC-AUC Scores** indicated strong separability, supporting model reliability.  
