# Bankruptcy Prediction Model

This project details the development of a machine learning model to predict company bankruptcy, addressing the challenges posed by imbalanced datasets.

## Workflow Summary

Our journey involved a systematic approach to building a robust bankruptcy prediction system:

1.  **Data Understanding and Preparation:**
    * We started with the **Poland Bankruptcy Dataset**, which consists of 64 financial ratios (`feat_1` to `feat_64`) as features and a binary target variable indicating bankruptcy status (`bankrupt`).
    * A critical initial observation was the severe class imbalance, with bankrupt companies (minority class) being significantly rarer than non-bankrupt ones.

2.  **Addressing Class Imbalance:**
    * We recognized that standard models often struggle with imbalanced data, leading to poor minority class detection.
    * Initial experiments with a default Decision Tree without resampling confirmed this, showing high overall accuracy but very low recall for bankruptcies.
    * We then explored common resampling techniques: **Random Undersampling** and **SMOTE Oversampling**.
    * **Random Undersampling** proved to be highly effective, significantly boosting the minority class recall and ROC AUC for the Decision Tree, despite a slight decrease in overall accuracy. This strategy was adopted for all subsequent model training.

3.  **Model Exploration and Hyperparameter Tuning:**
    * We evaluated several powerful machine learning models, including **Decision Tree**, **Random Forest**, and **Gradient Boosting**.
    * Each model was trained using the undersampled data, and their hyperparameters were optimized through **Grid Search** to achieve the best performance.
    * Performance was assessed on a separate, **original (non-resampled) validation set** to ensure realistic evaluation of generalization.
    * The **Tuned Gradient Boosting Classifier with Undersampling** emerged as the strongest candidate, demonstrating the optimal balance of high ROC AUC and robust minority class recall on the validation data.

4.  **Final Model Evaluation:**
    * The chosen **Tuned Gradient Boosting with Undersampling** model was rigorously tested on a completely **unseen test set** to provide an unbiased estimate of its real-world performance. This crucial step validates the model's ability to generalize to new, never-before-seen company data.

## Conclusion

Our project successfully developed a highly effective and interpretable **Gradient Boosting Classifier model with Random Undersampling** for predicting company bankruptcy.

The model's performance on the unseen test set demonstrates its strength:

* **Exceptional ROC AUC:** A score of **0.8930** highlights the model's excellent ability to distinguish between bankrupt and non-bankrupt companies.
* **High Minority Class Recall:** With a **Recall of 0.81** for bankrupt companies, the model effectively identifies a large proportion of actual bankruptcy cases. This is paramount for minimizing the costly consequences of missed predictions.
* **Precision-Recall Trade-off:** The model exhibits a Precision of **0.10** for the minority class. While this indicates a higher rate of false alarms, it is a common and often acceptable trade-off in imbalanced classification where the primary goal is to capture as many rare positive events as possible.

**Key Feature Importances:**
Analysis of the model's feature importances (Gini Importance) revealed that its predictions are primarily driven by critical financial ratios:

* `feat_27`: Operating activities / financial expenses
* `feat_24`: Profit on operating activities (in 3 years) / total assets
* `feat_34`: Operating expenses / total liabilities
* `feat_48`: EBITDA / total assets
* `feat_13`: Profit / total costs

These features highlight the crucial role of a company's profitability, operational efficiency, and ability to manage its financial obligations in determining its bankruptcy risk.

This project demonstrates the successful development of an interpretable and robust bankruptcy prediction model, capable of serving as a valuable **early warning system** for financial institutions and businesses to assess credit risk, guide investment decisions, and enable proactive interventions.

## Author
**Sawsan Yousef** 

*Data Scientist | Predictive Modeling | Computer Vision*
