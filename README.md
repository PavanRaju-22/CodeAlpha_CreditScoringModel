# Credit Scoring Model

A machine learning project that explores binary classification for credit risk assessment using the German Credit dataset. The goal is to compare classification algorithms and evaluate how effectively they identify customers classified as having bad credit risk.

## Project Overview

This project follows a machine learning workflow covering exploratory data analysis (EDA), data preprocessing, model training, evaluation, and model comparison.

**Objective:** Predict credit risk and investigate the trade-off between correctly identifying risky customers and incorrectly flagging creditworthy customers.

## Dataset

- **Dataset:** German Credit dataset
- **Records:** 1,000
- **Original input features:** 20
- **Target variable:** `credit_risk`
  - `1` — Good credit risk
  - `2` — Bad credit risk

The dataset contains numerical and categorical features describing credit applicants.

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Jupyter Notebook

## Workflow

1. **Exploratory Data Analysis:** Examined the dataset, target distribution, feature types, missing values, and duplicate records.
2. **Preprocessing:** Standardized numerical features and one-hot encoded categorical features using a preprocessing pipeline.
3. **Data Splitting:** Used a stratified 80/20 train-test split to preserve the target class proportions.
4. **Model Training:** Trained a majority-class baseline and four machine learning classification models.
5. **Evaluation:** Compared accuracy, precision, recall, F1-score, confusion matrices, and ROC-AUC.
6. **Model Comparison:** Evaluated the trade-offs between overall performance and identifying customers in the Bad credit class.

## Models Evaluated

- Majority-class baseline
- Logistic Regression
- Decision Tree (maximum depth of 6)
- Random Forest
- Balanced Random Forest using class weights

## Results

The following results were obtained on the held-out test set. Precision, recall, and F1-score refer to the **Bad credit class** (`credit_risk = 2`).

| Model | Accuracy | Bad Precision | Bad Recall | Bad F1-Score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Majority-Class Baseline | 70.0% | 0.000 | 0.000 | 0.000 | N/A |
| Logistic Regression | 78.0% | 0.667 | 0.533 | 0.593 | 0.804 |
| Decision Tree (Depth 6) | 61.5% | 0.395 | 0.533 | 0.454 | 0.651 |
| Random Forest | 74.0% | 0.605 | 0.383 | 0.469 | 0.779 |
| Balanced Random Forest | 73.5% | 0.556 | 0.583 | 0.569 | 0.788 |

### Key Findings

- **Logistic Regression** achieved the highest accuracy (78.0%), Bad-class F1-score (0.593), and ROC-AUC (0.804) among the evaluated models.
- **Balanced Random Forest** achieved the highest Bad-class recall (58.3%), identifying 35 of the 60 Bad-class examples in the test set.
- **Standard Random Forest** identified 23 of the 60 Bad-class examples. It had higher Bad-class precision than the balanced version but lower recall.
- The Balanced Random Forest also incorrectly classified more Good-class customers as Bad, illustrating the trade-off between detecting risky customers and avoiding false alarms.

Based on the current test-set results, Logistic Regression is the preferred overall model. Balanced Random Forest is a useful alternative when identifying a larger proportion of risky customers is the priority.

## How to Run

### 1. Clone the Repository

```bash
git clone https://github.com/PavanRaju-22/CodeAlpha_CreditScoringModel.git
cd CodeAlpha_CreditScoringModel
```

### 2. Create a Virtual Environment

```bash
python -m venv .venv
```

Activate it on Windows:

```powershell
.venv\Scripts\Activate.ps1
```

If you use Command Prompt instead of PowerShell:

```cmd
.venv\Scripts\activate.bat
```

### 3. Install Dependencies

```bash
python -m pip install --upgrade pip
python -m pip install pandas numpy scikit-learn jupyter ipykernel
```

### 4. Verify the Dataset

Ensure the following files are present in the `data/` directory:

- `german.data`
- `german.doc`

### 5. Open and Run the Notebook

Open the repository in VS Code and open:

`notebooks/01_credit_scoring_eda.ipynb`

Select the virtual environment as the notebook kernel, then restart the kernel and run all cells from the beginning.

## Limitations

- The dataset contains only 1,000 records and may not represent current lending populations.
- The results are based on a single train-test split and may vary with different splits.
- The models have not been validated for real-world lending decisions.
- Fairness, probability calibration, decision thresholds, and the consequences of classification errors require further investigation.
- Performance metrics alone are insufficient to establish that a model is suitable for credit decisions.

This project is an educational machine learning experiment and is **not intended for direct use in real-world credit approval decisions**.

## Future Improvements

- Perform more systematic cross-validation and hyperparameter tuning.
- Evaluate decision thresholds using the relative costs of classification errors.
- Investigate probability calibration and model interpretability.
- Assess fairness and robustness across relevant customer groups.
- Validate the selected model on additional data before considering practical applications.

## Author

**Pavan Raju C**

GitHub: [PavanRaju-22](https://github.com/PavanRaju-22)
