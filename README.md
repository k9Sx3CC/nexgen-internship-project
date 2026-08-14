# nexgen-internship-project

# Week 4 Capstone — Predicting Internship Selection Outcomes

A machine learning project that uses applicant information to predict whether an internship applicant is likely to be **Selected** or **Not Selected**.

## 1. Objective

The objective of this project is to build a simple machine learning model that predicts internship selection outcomes from applicant-related features.

This project combines data preparation, feature engineering, machine learning, and model evaluation to demonstrate a complete predictive modeling workflow.

The model is intended as a **decision-support tool** for this exercise and is not designed to replace human judgment in actual internship selection.

## 2. Dataset

The dataset contains internship applicant information and their selection outcomes.

Applicants with an **Under Review** status were excluded from model training because they did not have a confirmed selection outcome. The remaining applicants were classified as:

* **Selected** — target value `1`
* **Rejected / Not Selected** — target value `0`

Four additional features were added for this exercise:

* `num_skills_listed`
* `has_portfolio`
* `prior_hackathon_participation`
* `statement_quality_score`

### Important Note About Simulated Features

The four newly added features are **simulated**, not real historical applicant data. They were generated for this learning exercise because the original dataset did not contain these behavioral/application features.

Therefore, the model results should be treated as an illustration of the machine-learning workflow rather than evidence about the actual factors that determine internship selection.

For a real deployment, these features would need to be collected consistently from actual applications and the model would need to be validated using a much larger real-world dataset.

## 3. Method

The project follows these main steps:

### Data Cleaning

* Loaded the applicant dataset using Pandas.
* Examined the existing applicant status values.
* Removed applicants whose status was **Under Review**, since their outcomes were not confirmed.

### Feature Preparation

* Added four simulated applicant features.
* Converted Yes/No features into numerical `0/1` values.
* Converted the selection outcome into a binary target:

  * `1` = Selected
  * `0` = Not Selected
* Converted the application domain into numerical features using one-hot encoding.
* Excluded identifying information such as applicant names and email addresses from the model features.

### Model Training

A **Decision Tree Classifier** was trained using:

* Maximum tree depth: `4`
* Random state: `42`
* Train/test split: `80% / 20%`

The maximum depth was limited to reduce the risk of overfitting and to make the model easier to interpret.

### Model Evaluation

The model was evaluated on the unseen test set using:

* Accuracy
* Precision
* Recall
* Confusion Matrix

Feature importance was also examined to understand which inputs contributed most to the model's decisions.

## 4. Key Results

The Decision Tree achieved the following results on the test set:

| Metric    |     Result |
| --------- | ---------: |
| Accuracy  | **75.00%** |
| Precision | **80.00%** |
| Recall    | **66.67%** |

In plain terms, the model correctly predicted the selection outcome for approximately **3 out of every 4 applicants in the test set**.

The model achieved **80.00% precision**, meaning that most applicants predicted as Selected were actually Selected.

The model achieved **66.67% recall**, meaning that it identified about two-thirds of the applicants who were actually Selected.

### Important Interpretation

The test set contains only **12 applicants**, so these metrics should be interpreted cautiously. A small test set means that a small number of different predictions can cause the reported metrics to change noticeably.

The results are therefore useful for demonstrating the machine-learning process, but they should not be treated as a guarantee of performance on future applicants.

## 5. Limitations

This project has several important limitations:

* The dataset is relatively small.
* The test set contains only 12 applicants.
* Four model features were simulated rather than collected from real historical applications.
* Model performance may change with a different train/test split.
* The model could potentially reflect biases present in historical selection decisions.
* Feature importance indicates patterns learned by the model but does not prove that a feature causes selection.
* The model should be treated as a **decision-support tool**, not a replacement for human review.

## 6. How to Run

### Google Colab

1. Open the notebook in Google Colab.
2. Upload the required dataset, such as `applicants_cleaned.csv`.
3. Make sure the dataset is located in the expected working directory.
4. Run the notebook cells from top to bottom.
5. Review the model evaluation metrics, confusion matrix, and feature importance results.

### Required Libraries

The project uses:

* Python
* Pandas
* NumPy
* Matplotlib
* Scikit-learn

## 7. Recorded Walkthrough

A 2–3 minute walkthrough video explaining the project, methodology, results, limitations, and recommendation is required.

**Walkthrough Video:** `[Insert your recorded video link here]`

## Conclusion

This project demonstrates an end-to-end machine-learning workflow for predicting internship selection outcomes, from data preparation and feature engineering through model training and evaluation.

The results demonstrate how a predictive model can be evaluated using multiple metrics rather than accuracy alone. However, because the dataset is small and several features are simulated, the findings should be considered illustrative rather than production-ready.
