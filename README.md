# Student-Performance-Predictor

# 🎓 Student Grade Prediction (G3) with Machine Learning and Gradio

This project predicts students' final grades using machine learning techniques, explores model performance comparisons, and deploys the final model through an interactive Gradio web app.

---

## 📌 Project Summary

**Goal:** Predict a student's final grade (`G3`) out of 20 using historical and behavioral data.  
**Dataset:** [UCI Student Performance Dataset](https://archive.ics.uci.edu/ml/datasets/Student+Performance)

---

## 🔍 Workflow Overview

### ✅ 1. Data Preprocessing & EDA

- Loaded and cleaned the data from `student-mat.csv`
- Handled categorical features with `pd.get_dummies()`
- Explored data through correlation heatmaps and summary statistics
- Identified `G2` (second period grade) as the strongest predictor of `G3`

### ✅ 2. Model Comparison

We trained and evaluated three regression models:

| Model                | R² Score | RMSE   |
|---------------------|----------|--------|
| Linear Regression    | ~0.72    | ~2.38  |
| Decision Tree        | ~0.66    | ~2.75  |
| Random Forest        | **~0.82**| **~1.7** ✅ |

**Conclusion:**  
> **Random Forest Regressor** outperformed the others in both R² and RMSE. It captured non-linear relationships and generalized well without overfitting.

---

## 🌲 3. Decision Tree Tuning

To better understand tree-based models, we tested different depths for the Decision Tree Regressor:

| Max Depth | R² Score | RMSE   |
|-----------|----------|--------|
| 2         | ~0.66    | ~2.75  |
| 3         | ~0.66    | ~2.75  |
| >4        | ↓ R²     | ↑ RMSE |

> **Insight:** A depth of **2 or 3** was optimal. Larger trees overfit and degraded performance.

---

## 🧠 4. Feature Importance Analysis

We used the Random Forest model to extract the most important features affecting prediction:

![Feature Importance Plot](assets/feature_importance.png)

### 🎯 Top Predictors of Final Grade (G3):
1. **G2** – Second period grade
2. **Fjob_other** – Father's job type (encoded)
3. **G1** – First period grade
4. **Fedu** – Father's education level

---

## ✂️ 5. Simplified Model for Web Deployment

To make the Gradio interface cleaner and more user-friendly, we retrained the model using only the **top 5 numeric features**:

- `G1`, `G2`, `studytime`, `failures`, `absences`

This reduced complexity without sacrificing much predictive power.

---

## 💻 6. Gradio Web App

We built an interactive front-end using **Gradio**, allowing users to input student data and get instant predictions for final grades (`G3` out of 20).

### 🎮 Features:
- Real-time predictions
- Clear sliders and labels for usability
- Public Gradio share link for easy access

![Gradio Demo](assets/gradio_demo.png)

---

## 🛠 Technologies Used

- Python
- Pandas, NumPy
- Scikit-learn
- Gradio
- Matplotlib & Seaborn (for visualizations)
- Google Colab

---

## 📦 Project Structure



![image](https://github.com/user-attachments/assets/f92be522-158d-45d6-a160-070193b4357c)
