# 🎓 Student Grade Prediction using Linear Regression

## 📌 Project Overview

This project predicts students' final mathematics grades using a **Linear Regression** model implemented with **scikit-learn**. The goal is to build a complete machine learning pipeline, including data preprocessing, feature engineering, model training, and evaluation.

This project was created as part of my Machine Learning learning journey.

---

## 📂 Dataset

The project uses the **Student Performance Dataset** (`student-mat.csv`), which contains demographic, social, and academic information about students.

**Target Variable:**

* `G3` — Final mathematics grade

---

## 🛠 Technologies Used

* Python
* Pandas
* Scikit-learn
* Jupyter Notebook

---

## ⚙️ Project Workflow

1. Load the dataset
2. Select features and target variable
3. Encode categorical variables
4. Split the dataset into training and testing sets
5. Train a Linear Regression model
6. Generate predictions
7. Evaluate the model using regression metrics
8. Analyze feature coefficients

---

## 📊 Model Performance

| Metric   |  Score |
| -------- | -----: |
| MAE      |  1.647 |
| MSE      | 5.656 |
| RMSE     |  2.378 |
| R² Score |  0.724 |

The model explains approximately **72%** of the variance in students' final grades.

---

## 📁 Repository Structure

```text
student-grade-prediction/
│
├── data/
│   └── student-mat.csv
│
├── student_grade_prediction.ipynb
│
└── README.md
```

---

## 🚀 Future Improvements

* Experiment with Decision Tree Regressor
* Compare multiple regression algorithms
* Perform feature selection and hyperparameter tuning
* Add data visualization and residual analysis

---

## 👨‍💻 Author

**Mobin Rahmati**

This repository documents one of my early machine learning projects as I continue building my data science and machine learning portfolio.
