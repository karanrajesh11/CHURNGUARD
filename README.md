# ChurnGuard: End-to-End Customer Churn Prediction in R

An end-to-end data mining and machine learning project for customer churn prediction, developed entirely in R and executed in a containerised R environment inside Google Colab.

ChurnGuard uses the IBM Telco Customer Churn dataset to analyse customer behaviour, build predictive classification models, evaluate their performance, and integrate the trained models into an interactive R Shiny application.

## Project Overview

Customer churn occurs when customers discontinue a service. Identifying customers who are likely to leave can help organisations investigate retention opportunities and make data-driven decisions.

ChurnGuard implements a complete workflow covering data preprocessing, exploratory data analysis (EDA), classification modelling, model evaluation, model comparison, and interactive prediction.

The project is organised into three phases:

- **Phase 1: Data Preprocessing and EDA**: Dataset auditing, missing-value analysis, data cleaning, statistical summaries, and exploratory visualisations.
- **Phase 2: Data Mining and Model Evaluation**: Implementation and comparison of Logistic Regression, Decision Tree (CART), and Random Forest classifiers.
- **Phase 3: Interactive Application**: Integration of trained models into an R Shiny interface for customer churn prediction and model-performance inspection.

## Key Features

- Complete data analysis and predictive modelling workflow in R.
- Containerised R execution inside Google Colab.
- Dataset quality assessment and missing-value handling.
- Exploratory analysis of customer characteristics and churn patterns.
- Three classification algorithms and a majority-class baseline.
- Stratified train-test splitting and training-based preprocessing.
- Model evaluation using multiple classification metrics.
- Confusion matrices, ROC curves, and threshold sensitivity analysis.
- Random Forest feature-importance analysis.
- Saved models, predictions, evaluation results, and visualisation artefacts.
- R Shiny interface for interactive predictions, subject to the included application implementation.

## Dataset

**IBM Telco Customer Churn**

Source: [Kaggle: Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)

The dataset contains customer demographics, account information, service subscriptions, contract details, and billing attributes.

| Characteristic | Value |
|---|---:|
| Customer records | 7,043 |
| Original columns | 21 |
| Non-churn customers | 5,174 |
| Churn customers | 1,869 |
| Observed churn rate | 26.54% |
| Prediction task | Binary classification |

The initial data audit identified 11 missing `TotalCharges` values and no exact duplicate rows.

## Machine Learning Algorithms

**1. Logistic Regression**

Estimates customer churn probabilities using customer and account characteristics. It provides a statistical classification model and supports probability-based evaluation.

**2. Decision Tree (CART)**

Learns decision rules that divide customers into groups with different predicted churn probabilities. The tree structure supports interpretation of customer segments and classification decisions.

**3. Random Forest**

Combines multiple decision trees to capture more complex relationships between customer attributes and churn. Feature-importance measures help interpret the fitted model.

**Baseline: Majority-Class Classifier**

Predicts the majority class for every customer. This provides a reference point and demonstrates why accuracy alone is insufficient when the target classes are imbalanced.

## Model Evaluation

Models are evaluated on a held-out test set, with `Churn = Yes` treated as the positive class.

| Metric | Purpose |
|---|---|
| Accuracy | Overall proportion of correct predictions |
| Precision | Proportion of predicted churners who actually churned |
| Recall | Proportion of actual churners correctly identified |
| Specificity | Proportion of non-churners correctly identified |
| F1-score | Balance between precision and recall |
| Balanced accuracy | Average of sensitivity and specificity |
| ROC-AUC | Ability to distinguish between churn classes |
| Brier score | Accuracy of predicted probabilities |

Additional analyses include confusion matrices, ROC curves, classification-threshold sensitivity, decision-tree visualisation, and Random Forest feature importance.

### Recorded Test Results

The following results are from the recorded Phase 2 execution at a classification threshold of 0.50.

| Model | Accuracy | Precision | Recall | F1-score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Majority baseline | 73.46% | 0.0000 | 0.0000 | 0.0000 | 0.5000 |
| Logistic Regression | 80.34% | 0.6474 | 0.5695 | 0.6060 | 0.8429 |
| Decision Tree | 78.71% | 0.6000 | 0.5936 | 0.5968 | 0.8032 |
| Random Forest | 78.71% | 0.6217 | 0.5053 | 0.5575 | 0.8288 |

Logistic Regression achieved the highest recorded accuracy, F1-score, and ROC-AUC. The Decision Tree achieved the highest recall among the three trained classifiers.

These results describe a single train-test split and are not a guarantee of performance on future customers.

## Technology Stack

- **Programming language:** R
- **Execution environment:** Google Colab
- **Runtime architecture:** Containerised R environment within the notebook
- **Data visualisation:** ggplot2
- **Decision Tree:** rpart and rpart.plot
- **Random Forest:** randomForest
- **ROC analysis:** pROC
- **Interactive interface:** R Shiny

## How to Run ChurnGuard

**You do not need to install R locally.** The intended workflow is to download the notebook from this repository and execute it in Google Colab.

### Step 1: Download the notebook

1. Open this GitHub repository.
2. Navigate to the ChurnGuard `.ipynb` notebook.
3. Open the notebook file and select **Download raw file**, or use GitHub's download option.
4. Save the `.ipynb` file to your computer.

If the repository is distributed as a ZIP archive, download and extract the archive, then locate the notebook.

### Step 2: Open Google Colab

1. Visit [Google Colab](https://colab.research.google.com/).
2. Select **File → Upload notebook**.
3. Upload the downloaded ChurnGuard `.ipynb` file.
4. Wait for the notebook to load.

### Step 3: Initialise the containerised R environment

Run the notebook's initial setup cells in their original order.

These cells are responsible for initialising the containerised R environment, preparing dependencies, and configuring the notebook for R execution.

**Do not replace the container setup with a generic R installation.** The notebook's own environment initialisation instructions are the intended entry point.

### Step 4: Provide the dataset

Ensure that the IBM Telco Customer Churn CSV is available at the location expected by the notebook.

Depending on the notebook configuration, the dataset may be loaded from an existing file, a previously generated Phase 1 output, or a configured public data source.

If the notebook cannot locate the dataset automatically, obtain it from the [Kaggle dataset page](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) and follow the notebook's expected file path and naming convention.

### Step 5: Execute the notebook

Execute the cells sequentially, following the notebook's existing phase structure:

1. Environment initialisation and dependency setup.
2. Dataset loading and data-quality checks.
3. Data preprocessing and exploratory data analysis.
4. Classification model training.
5. Model evaluation and comparison.
6. Saving model artefacts and analytical outputs.
7. Application setup and launch, where included.

Use **Runtime → Run all** only after confirming that the notebook is configured for a fresh execution and that its setup and data-loading cells are ready.

Some phases depend on files created in earlier phases, so executing isolated cells without their prerequisites may produce errors.

### Step 6: Review the results

Inspect the notebook outputs, including:

- Data summaries and preprocessing results.
- Exploratory data analysis visualisations.
- Classification performance metrics.
- Confusion matrices and ROC curves.
- Threshold sensitivity results.
- Feature-importance analysis.
- Saved model artefacts and prediction files.

The Phase 2 workflow writes its outputs to `churn_guard_report2_outputs/`. Phase 1 may use `telco_eda_outputs/`.

### Step 7: Launch the R Shiny application

If the application is included in the repository workflow, execute its setup and launch cells after the required model artefacts have been generated or loaded.

Follow the notebook's application-specific instructions to access the interface. If the application requires an external URL or forwarding mechanism, that configuration must also be completed.

### Runtime considerations

Google Colab sessions are temporary. If the runtime disconnects or restarts, files stored only in the temporary runtime and installed dependencies may need to be restored. Rerun the setup cells and regenerate or reload the required artefacts before continuing.

Execution time depends on dependency installation, dataset retrieval, model training, and the resources available to the Colab session.

## Repository Contents

The repository should contain the actual notebook and any supporting files needed to reproduce the project. Depending on what is committed, these may include:

- The ChurnGuard Jupyter notebook (`.ipynb`).
- R Shiny application source code.
- Dataset acquisition instructions.
- Saved model artefacts.
- Evaluation tables and visualisations.
- Phase 1, Phase 2, and Phase 3 reports.

The exact file structure depends on the files included in the repository. Generated outputs may be created when the notebook is executed rather than being included in the initial download.

## Reproducibility

- A fixed random seed is used in the recorded Phase 2 workflow.
- The dataset is split into stratified training and test sets.
- Preprocessing values are learned from the training set to reduce information leakage.
- Models are compared using held-out test-set results.
- Saved model artefacts support integration with the application phase.

Results may vary if the dataset, preprocessing, model configuration, software versions, or random seed changes.

## Limitations and Future Work

The recorded evaluation is based on a single train-test split. Further work could include cross-validation, hyperparameter tuning, probability calibration, business-cost-based threshold selection, model monitoring, and evaluation on newer customer data.

Model associations and feature importance do not establish causation, and predictions should not be interpreted as guarantees of future customer behaviour.

## References

1. Kaggle. [Telco Customer Churn Dataset](https://www.kaggle.com/datasets/blastchar/telco-customer-churn).
2. R Core Team. [R: A Language and Environment for Statistical Computing](https://www.r-project.org/).
3. Therneau, T., Atkinson, B., and Ripley, B. Documentation for the `rpart` package.
4. Liaw, A., and Wiener, M. (2002). Classification and Regression by randomForest. *R News*, 2(3), 18–22.
5. [Google Colab](https://colab.research.google.com/).
6. [R Shiny Documentation](https://shiny.posit.co/).

---

**ChurnGuard** demonstrates the integration of data preprocessing, exploratory analysis, classification algorithms, model evaluation, and interactive prediction in a containerised R workflow executed through Google Colab.
