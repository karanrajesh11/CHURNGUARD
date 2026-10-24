# ChurnGuard: Containerised R-Based Customer Churn Prediction

ChurnGuard is an end-to-end data mining and machine learning project developed entirely in **R**, with the R execution environment containerised and run within Google Colab. Using the IBM Telco Customer Churn dataset, the project aims to identify customers at risk of discontinuing their telecommunications services through predictive modelling and data-driven analysis.

The project encompasses data preprocessing, missing-value handling, exploratory data analysis (EDA), classification modelling, model evaluation, and interactive visualisation. Three classification algorithms are implemented and compared: **Logistic Regression, Decision Tree (CART), and Random Forest**, alongside a majority-class baseline.

Models are evaluated using accuracy, precision, recall, specificity, F1-score, balanced accuracy, ROC-AUC, and Brier score. Confusion matrices, ROC curves, classification threshold analysis, and feature importance visualisations support model comparison and interpretation.

The project also incorporates an **R Shiny application** to integrate trained models into an interactive prediction interface, supporting individual customer predictions, batch CSV scoring, and model performance visualisations according to the implemented functionality.

By combining containerised R execution in Google Colab with data mining algorithms, systematic model evaluation, and an interactive application, ChurnGuard demonstrates a reproducible workflow for customer churn prediction and predictive analytics in the telecommunications domain.

**Technology stack:** R, Google Colab, containerisation, R Shiny, ggplot2, rpart, randomForest.

**Core components:** Data preprocessing, exploratory data analysis, classification, model evaluation, model comparison, feature importance, and interactive churn prediction.
