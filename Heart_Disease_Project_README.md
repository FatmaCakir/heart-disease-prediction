# Heart Disease Prediction Using Machine Learning

## Project Overview
This supervised machine learning project predicts the `HeartDisease` label (0 = no heart disease; 1 = heart disease) using clinical and demographic variables. It is a classroom exercise, not a diagnostic tool.

## Dataset
Source: [Heart Failure Prediction dataset on Kaggle](https://www.kaggle.com/datasets/fedesoriano/heart-failure-prediction).

The dataset contains 918 records and 12 columns (11 features and one target). The file used in this project is `heart.xls`, containing CSV-formatted text despite its extension.

## Features and Target
- Target: `HeartDisease`
- Features: `Age`, `Sex`, `ChestPainType`, `RestingBP`, `Cholesterol`, `FastingBS`, `RestingECG`, `MaxHR`, `ExerciseAngina`, `Oldpeak`, `ST_Slope`.

## Data Preparation
- Inspected missing values and duplicate rows.
- Identified 172 zero cholesterol measurements and one zero resting blood pressure measurement; treated these as missing for preprocessing.
- Applied imputation and categorical encoding within the model pipelines.
- Split the records into 734 training and 184 test observations.

## Modeling and Evaluation
Compared a majority-class baseline, Logistic Regression, and Random Forest, using five-fold stratified cross-validation. Tuned Random Forest with `GridSearchCV`.

### Final tuned Random Forest — held-out test set
| Metric | Result |
|---|---:|
| Accuracy | 89.1% |
| Precision | 87.3% |
| Recall | 94.1% |
| F1-score | 90.6% |
| ROC-AUC | 0.938 |

These figures reflect this dataset and split, not expected clinical performance.

## How to Run
1. Keep `heart_disease_analysis.ipynb` and `heart.xls` together in the same folder.
2. Install dependencies: `pip install pandas numpy matplotlib seaborn scikit-learn jupyter`.
3. Open `heart_disease_analysis.ipynb` in Jupyter Notebook.
4. Confirm the data-loading cell uses:
   ```python
   from pathlib import Path
   import pandas as pd
   data_path = Path("heart.xls")
   df = pd.read_csv(data_path)
   ```
5. Run all cells in order.

## Key Findings
The tuned Random Forest attained 94.1% recall and 0.938 ROC-AUC on the held-out test data. Recall is especially relevant when discussing missed positive cases.

## Limitations and Future Work
This dataset is limited in size and representativeness. Further work should include independent external validation, calibration, subgroup performance analysis, and assessment of clinical appropriateness. This model must not be used to make medical decisions.

## Repository Contents
The final submission should include this `README.md`, the executed notebook, dataset or access instructions, reusable Python scripts, dependencies, and presentation slides.
