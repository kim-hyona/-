# 🧪 Breast Cancer Survival Prediction
"Predicting survival outcomes for breast cancer patients using machine learning."
This project aims to develop a predictive model for survival outcomes based on data from female breast cancer patients. Breast cancer is one of the most common cancers among women globally, and early diagnosis and timely treatment significantly influence survival rates. Since survival can vary based on personal characteristics such as cancer stage, age, and marital status, predictive modeling can help provide tailored treatment plans and better outcomes.

# 📊 Dataset Description
We used the Breast Cancer dataset from Kaggle, sourced from the SEER program by the NCI (updated November 2017). It includes female patients diagnosed with invasive ductal and lobular breast cancers between 2006–2010. Patients with missing tumor size data, unknown lymph node info, or survival months less than 1 were excluded, resulting in a final dataset of 4,024 patients.

# 🩹 Data Preprocessing & EDA
* Target variable Status was label-encoded (0 = deceased, 1 = survived).
* Dataset was split into training and testing sets (80:20).
* Categorical variables were one-hot encoded using pd.get_dummies.
* SMOTE was applied to training data to address class imbalance.


# 📈 Visual Explorations

## 1. Survival by Age Distribution
Younger patients (ages 50–60) had higher survival density, while deceased patients were mostly aged 60–70.

<img width="862" height="397" alt="Image" src="https://github.com/user-attachments/assets/41564b92-3ed4-4888-8040-e1baecde1d56" />


---------------------------
## 2. Survival by Marital Status
Married patients formed the majority. However, more deceased patients were married, possibly due to diagnosis bias or support availability.

<img width="935" height="462" alt="Image" src="https://github.com/user-attachments/assets/ce5d12b8-fb24-4a5f-a2f8-a77f35d5b101" />




---------------------------
## 3. Tumor Size by Survival Status
Both survived and deceased groups show similar tumor size distributions, indicating size may not be a decisive survival factor.

<img width="940" height="470" alt="Image" src="https://github.com/user-attachments/assets/0dee096c-625f-475e-8c3a-932a4eb50961" />


-----------------------
## 4. Survival Months by Status
Survivors lived significantly longer. Many deceased patients passed within the first 1–2 months, highlighting the importance of early detection.

<img width="931" height="433" alt="Image" src="https://github.com/user-attachments/assets/c23b63f1-d10c-402b-9425-d39b7f1213f0" />


-----------------------

# 🤖 Model Training (SVM)

Model: Support Vector Machine (SVM)

Why SVM? Effective in handling imbalanced data and finding the optimal decision boundary (maximum margin hyperplane).

SMOTE: Used to synthetically balance minority class samples.

Hyperparameter Tuning: Performed using RandomizedSearchCV to explore combinations of C, gamma, and kernel efficiently.

📋 Evaluation

Overall Accuracy: ~87%

Class 0 (Deceased): Precision = 0.93, Recall = 0.92

Class 1 (Survived): Precision = 0.57, Recall = 0.60, F1 = 0.59

The model performs well on the majority class but underperforms on the minority class. This reflects the typical challenge of imbalanced datasets. To address this, we used SHAP for interpretability.

<img width="937" height="477" alt="Image" src="https://github.com/user-attachments/assets/7becb68b-4c1b-43eb-afc8-540dfe3a3130" />
<img width="939" height="447" alt="Image" src="https://github.com/user-attachments/assets/84bbd8fa-f2bd-438b-8958-e05bf4cffd50" />


# 🔍 Model Interpretation using SHAP



SHAP (SHapley Additive exPlanations) was used to analyze the feature importance:

Survival Months: Most impactful. Longer survival months → higher survival probability.

Grade_2: Negatively impacts survival. Higher tumor grade correlates with lower survival.

Marital Status (Married): Associated with better survival odds.

Regional Node Positive: Higher lymph node involvement → worse survival.

AGE: Younger age increases survival odds.

Tumor Size: Larger size slightly decreases survival probability.

<img width="929" height="474" alt="Image" src="https://github.com/user-attachments/assets/b4e6ebe4-33d9-44b7-b0bf-5b98d1382f61" /> 


🧐 Summary:

SHAP analysis confirms that key survival indicators include:

Long survival duration

Low tumor grade

Being married

Low lymph node involvement

Younger age

Smaller tumor size

These insights could support doctors in identifying high-risk patients and prioritizing treatment plans.
