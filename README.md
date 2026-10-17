# 🎓 Student Grade Prediction: How Much Do Previous Grades Matter?

## 📌 Project Overview

This project predicts students' final mathematics grades (`G3`) using scikit-learn. It started as a simple Linear Regression model, and I then extended it to answer a more interesting question:

> **How much of a student's final grade can be predicted, and how much of that comes only from their previous period grades (`G1`, `G2`)?**

To answer it, every model is trained twice: once **with** `G1`/`G2` as features and once **without** them. Models are also compared against a naive **baseline** (always predicting the mean grade) to check that they actually learn something.

This project is part of my machine learning learning journey.

## 🔍 Key Finding

My first version reached **R² = 0.72**, but that number was misleading: `G1` and `G2` (grades from the earlier periods of the same course) were included as features, and they are very strongly related to the final grade.

After removing them, the same Linear Regression model dropped to **R² = 0.14**.

| Linear Regression (single 80/20 split) | MAE | RMSE | R² |
|---|---|---|---|
| With G1/G2 | 1.65 | 2.38 | 0.72 |
| Without G1/G2 | 3.40 | 4.20 | 0.14 |

**Takeaway:** most of the predictive power comes from earlier grades. Demographic and behavioral features (study time, absences, family background, etc.) explain only a small part of the final grade on their own.

## 📂 Dataset

[UCI Student Performance Dataset](https://archive.ics.uci.edu/dataset/320/student+performance), math course (`student-mat.csv`, 395 students). It contains demographic, social, and academic information.

**Target variable:** `G3`, the final mathematics grade (0 to 20).

## 🛠 Technologies Used

- Python
- Pandas
- Scikit-learn
- Matplotlib
- Jupyter Notebook

## ⚙️ Project Workflow

1. Load the dataset
2. Explore the target distribution (including students with `G3 = 0`)
3. Encode categorical variables (yes/no mapping and one-hot encoding)
4. Build two feature sets: with and without `G1`/`G2`
5. Compare a baseline, Linear Regression, and Random Forest using 5-fold cross-validation
6. Evaluate with MAE, RMSE, and R²
7. Analyze feature importance (Random Forest) and standardized coefficients (Linear Regression)

## 📊 Model Comparison (5-fold cross-validation)

| Features | Model | R² | RMSE | MAE |
|---|---|---|---|---|
| With G1/G2 | Baseline (mean) | -0.06 | 4.58 | 3.46 | 
| With G1/G2 | Linear Regression | 0.78 | 2.04 | 1.36 |
| With G1/G2 | Random Forest | 0.83 | 1.80 | 1.11 |
| Without G1/G2 | Baseline (mean) | -0.06 | 4.58 | 3.46 |
| Without G1/G2 | Linear Regression | 0.00 | 4.44 | 3.47 |
| Without G1/G2 | Random Forest | 0.13 | 4.12 | 3.16 |

![R² comparison](r2_comparison.png)

![Top features](feature_importance.png)

## ⚠️ Limitations

- Small dataset (395 rows), so results can vary between splits (cross-validation is used to reduce this).
- A group of students has `G3 = 0` (most likely students who did not take the final exam), which is hard for linear models to handle.
- Only one subject (math) and two schools.
- Models use default hyperparameters; no tuning was done.

## 📁 Repository Structure

```
student-grade-prediction/
│
├── data/
│   └── student-mat.csv
│
├── main.ipynb
├── r2_comparison.png
├── feature_importance.png
└── README.md
```

## 🚀 How to Run

```bash
pip install pandas scikit-learn matplotlib jupyter
jupyter notebook main.ipynb
```

## 🔮 Future Improvements

- Tune hyperparameters (e.g. with GridSearchCV)
- Handle the `G3 = 0` group separately (for example, a classifier for "did not take the exam" plus a regressor for the rest)
- Add residual analysis
- Try gradient boosting models

## 👨‍💻 Author

Mobin Rahmati

This repository documents one of my early machine learning projects as I continue building my data science and machine learning portfolio.
