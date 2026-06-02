# 🏀 Predicting Made vs. Missed NBA Shots Using Machine Learning

This project was developed as part of a master's-level **Python and Advanced Data Science** course.

The goal of the project is to predict whether an NBA shot attempt is made or missed using shot-level, player-level, team-level, spatial, temporal, and game-context features.

The project compares multiple supervised machine learning models, including **Logistic Regression**, **Linear SVC**, **Random Forest**, **AdaBoost**, and **Artificial Neural Networks**.

---

## 📌 Project Overview

Basketball shot success depends on many contextual factors such as shot location, distance, shot type, player form, team performance, game state, and time pressure.

This project uses NBA 2023–2024 regular-season shot-level data to build and evaluate models that predict the binary target variable:

```text
SHOT_MADE = True / False
```

The main research question is:

```text
Can contextual and engineered basketball features be used to predict whether an NBA shot will be made?
```

---

## 📊 Dataset

The project uses NBA shot-level data from the following public dataset:

- **Source:** https://github.com/DomSamangy/NBA_Shots_04_24
- **Season used:** NBA 2023–2024
- **Target variable:** `SHOT_MADE`

The dataset is downloaded directly inside the notebook.

---

## 📁 Repository Structure

```text
.
├── README.md
└── notebooks/
    └── nba_shot_prediction.ipynb
```

---

## 🧭 Main Steps

The project follows a full data science workflow:

1. Data loading and initial inspection
2. Data quality assessment
3. Exploratory data analysis
4. Feature engineering
5. Feature selection and multicollinearity checks
6. Model training and evaluation
7. Model comparison and interpretation

---

## ✅ Data Quality Assessment

The dataset was checked for:

- Missing values
- Duplicate records
- Invalid or inconsistent values
- Syntactic accuracy
- Semantic consistency
- Outlier behavior
- Feature validity

Several corrections and transformations were applied before modeling.

---

## 🔍 Exploratory Data Analysis

The exploratory analysis focused on understanding how different factors relate to shot success.

The analysis included:

- Overall shot success distribution
- Shot distance and shot efficiency
- Shot zone performance
- Spatial shot patterns
- Quarter-based performance
- Time-pressure situations
- Player-level performance
- Team-level performance
- Position-based differences

---

## 🛠️ Feature Engineering

Several new features were created to improve the predictive power of the models.

Examples of engineered features include:

- Home/away indicator
- Time left in game
- Current score situation
- Team recent performance
- Opponent defensive performance
- Player recent form
- Hot/cold streak features
- Shot angle
- Trade shock decay
- Playoff and standings context

---

## 🧪 Feature Selection

Before modeling, feature selection and multicollinearity checks were performed.

The process included:

- Correlation analysis
- Variance Inflation Factor analysis
- Removal of highly correlated variables
- Selection of features suitable for machine learning models

---

## 🤖 Models Evaluated

The following models were trained and compared:

| Model | Purpose |
|---|---|
| Logistic Regression | Interpretable linear baseline |
| Linear SVC | Linear margin-based classifier |
| Random Forest | Non-linear ensemble model |
| AdaBoost | Boosting-based ensemble model |
| Artificial Neural Network | Deep learning benchmark |

---

## 📏 Evaluation Metrics

The models were evaluated using:

- Accuracy
- F1-score
- ROC-AUC
- PR-AUC

Because the target variable is not perfectly balanced and threshold choice affects classification performance, **ROC-AUC** and **PR-AUC** were especially important for comparing model quality.

---

## 🏆 Key Results

On the common test set of the classical machine learning models, the best models achieved similar ranking performance.

| Model Variant | Accuracy | F1 | ROC-AUC | PR-AUC |
|---|---:|---:|---:|---:|
| Random Forest - Baseline | 0.6130 | 0.5289 | 0.6389 | 0.6510 |
| Random Forest - Best GridSearch | 0.6289 | 0.4923 | 0.6538 | 0.6655 |
| Random Forest - Calibrated + Threshold Tuned | 0.6170 | 0.5699 | 0.6539 | 0.6652 |
| AdaBoost - Tuned + Calibrated + Thresholded | 0.6286 | 0.5173 | 0.6546 | 0.6643 |
| Logistic Regression - Tuned | 0.6067 | 0.5693 | 0.6481 | 0.6548 |
| Linear SVC - Final Default Threshold | 0.6065 | 0.5697 | 0.6481 | 0.6550 |

The best tuned Artificial Neural Network used a separate test split and achieved:

| Model | Accuracy | ROC-AUC |
|---|---:|---:|
| ANN - VeryWideDeep, LeakyReLU, Adam | 0.6265 | 0.6473 |

---

## 💡 Main Findings

The project shows that NBA shot prediction is possible using contextual and engineered features, but the prediction task remains difficult.

The most important findings are:

- Tree-based ensemble models performed slightly better than linear baselines in terms of ROC-AUC and PR-AUC.
- Logistic Regression and Linear SVC were strong and stable baseline models.
- Threshold tuning improved F1-score in some cases but reduced accuracy.
- ROC-AUC and PR-AUC were more reliable for comparing model quality than a single threshold-based metric.
- Model performance plateaued around a ROC-AUC value of approximately 0.65.

---

## 🧠 Final Interpretation

The best models for shot-quality ranking were the ensemble models.

- **AdaBoost** achieved the highest ROC-AUC.
- **Random Forest** achieved the highest PR-AUC.

However, the improvement over simpler linear models was modest. This suggests that while non-linear models capture additional interactions, NBA shot success remains highly stochastic and difficult to predict with shot-context features alone.

---

## 🧰 Technologies Used

- Python
- pandas
- NumPy
- matplotlib
- seaborn
- scikit-learn
- TensorFlow / Keras
- Jupyter Notebook

---

## 🚀 How to Run

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME.git
cd YOUR_REPOSITORY_NAME
```

Install the required Python packages:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn tensorflow jupyter
```

Open the notebook:

```bash
jupyter notebook notebooks/nba_shot_prediction.ipynb
```

Run the notebook cells from top to bottom.

The dataset is downloaded automatically inside the notebook.

---

## 📝 Notes

This project was created for academic purposes.

The results should be interpreted as an applied machine learning study, not as a production-ready betting, scouting, or decision-making system.

---

## 🔮 Future Work

Potential improvements include:

- Repeated cross-validation for more robust confidence intervals
- Better probability calibration analysis
- More advanced feature engineering
- Additional model families such as XGBoost or LightGBM
- Player-specific and team-specific subgroup error analysis
- More detailed interpretability using SHAP or permutation importance
