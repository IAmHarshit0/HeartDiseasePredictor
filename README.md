# ❤️ Heart Disease Prediction using Machine Learning

This project presents a recall-optimized machine learning model for predicting the likelihood of heart disease based on clinical and lifestyle parameters. The primary aim is to reduce false negatives — ensuring patients with heart disease are not mistakenly classified as healthy.

---

## 📘 Objective

The goal of this project is to build a predictive model that is sensitive to high-risk heart disease cases. This is accomplished by:

- Selecting the most impactful features
- Using ensemble-based classifiers
- Performing **threshold tuning** to emphasize **recall over overall accuracy**
- Deploying the model using a **Streamlit web interface**

---

## 📊 Dataset Overview

After feature selection, the following input features were used:

| Feature                 | Description                                          |
|------------------------|------------------------------------------------------|
| Age                    | Age of the patient (years)                           |
| Blood Pressure         | Resting blood pressure (mm Hg)                       |
| Cholesterol Level      | Total cholesterol (mg/dL)                            |
| BMI                    | Body Mass Index                                      |
| Sleep Hours            | Average sleep duration (hours/day)                   |
| Triglyceride Level     | Triglycerides (mg/dL)                                |
| Fasting Blood Sugar    | Blood sugar > 120 mg/dL (1 = true; 0 = false)        |
| CRP Level              | C-Reactive Protein level (mg/L)                      |
| Homocysteine Level     | Homocysteine (µmol/L)                                |
| Gender_Male            | Binary indicator for male gender                     |
| Excercise_Low          | Binary indicator for low physical activity           |

All numeric features were standardized using **StandardScaler**.

---

## 🔧 Model Development

Multiple classification models were trained and evaluated using stratified train-test splits and classification metrics.

### Models Evaluated:

- Logistic Regression
- Random Forest
- AdaBoost
- Gradient Boosting
- HistGradientBoosting
- ✅ **CatBoostClassifier** (final selected model)

---

## 🎯 Threshold Tuning

Instead of using the default classification threshold (0.5), **threshold tuning** was conducted to prioritize recall. Precision vs. Recall vs. Threshold curves were plotted and analyzed.

> **Final Threshold Chosen:** `0.44`  
> This value strikes the best balance while maximizing recall — which is crucial in medical diagnostics.

---

## 📈 Final Model Performance (CatBoost @ threshold = 0.44)

| Metric     | Score |
|------------|--------|
| Accuracy   | 0.79   |
| Precision  | 0.79   |
| Recall     | **0.80** ✅ |
| F1-Score   | 0.79   |

The model correctly detects most patients with heart disease, ensuring low false-negative rates.

---

## 🖥️ Streamlit Web Application

A frontend interface was built using **Streamlit**, allowing users to input clinical data and receive real-time predictions.

### Features:

- Interactive sidebar to input all 11 features
- Uses saved preprocessing and model artifacts
- Applies the threshold tuned at `0.44` to prioritize recall
- Displays:
  - Final diagnosis (Heart Disease: Yes/No)
  - Confidence score
  - Raw predicted probability

### Running the App Locally

```bash
pip install -r requirements.txt
streamlit run app.py
```

---

## 📁 Files in This Repository

| File                 | Purpose                                                   |
|----------------------|-----------------------------------------------------------|
| `heart.ipynb`        | Full modeling pipeline including preprocessing, training, and evaluation |
| `heart_disease.csv`  | Dataset used for training the model                       |
| `Heart_Disease.pkl` | Saved CatBoost model after training and tuning            |
| `Scaler.pkl`         | Fitted StandardScaler object used for real-time scaling   |
| `main.py`             | Streamlit frontend for user interaction and predictions   |
| `README.md`          | Project documentation                                     |

---

## 📚 Future Improvements

- Add model explainability using **SHAP** values or **LIME**
- Deploy the app to **Streamlit Cloud** or **Render**
- Log and monitor real-time user inputs for analysis (with consent)
- Extend the model to handle multiclass cardiovascular risk levels
- Add an API layer using **FastAPI** or **Flask**

---

## 🙋 Author

**Harshit Mishra**  
B.Tech CSE Student  
Project built with academic precision and focus on healthcare responsibility.

---

## 🧠 Acknowledgements

- [Kaggle](https://www.kaggle.com/datasets/oktayrdeki/heart-disease)
- [CatBoost](https://catboost.ai/)
- Streamlit, scikit-learn, NumPy, Pandas

---
