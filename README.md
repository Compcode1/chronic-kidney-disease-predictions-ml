The goal of this project was to develop a machine learning model using **XGBoost** to predict **Chronic Kidney Disease (CKD)** based on various health-related features. XGBoost, or **Extreme Gradient Boosting**, is a powerful and efficient machine learning algorithm that leverages **gradient boosting** to improve model accuracy by sequentially building decision trees. Each tree attempts to correct the errors made by the previous one, and the final model is an ensemble of these trees. XGBoost is particularly known for its speed and performance in handling large datasets and achieving high predictive accuracy.

The project execution followed the initial steps of model development outlined in the **General Project Outline** but adapted dynamically based on the excellent results achieved without hyperparameter tuning, leading to a threshold adjustment to balance false negatives and false positives effectively.

### Execution Flow:
- **Initial Model**:
  The initial model was built with the default classification threshold of **0.5**. This produced outstanding results on the validation set, with:
  - **AUC-ROC**: 1.0000
  - **Accuracy**: 0.9985
  - **Precision**: 0.9976
  - **Recall**: 0.9861
  - **F1 Score**: 0.9919

- **Test Set Validation**:
  The model was validated on the test set to check for overfitting or memorization, and similar excellent results were achieved:
  - **AUC-ROC**: 0.9999
  - **Accuracy**: 0.9985
  - **Precision**: 0.9981
  - **Recall**: 0.9861
  - **F1 Score**: 0.9921

  These results confirmed that the model was generalizing well, with minimal risk of overfitting.

### Final Model – Adjusted Threshold:
Given the project’s focus on minimizing **False Negatives** (i.e., ensuring we catch as many CKD cases as possible), the decision was made to adjust the classification threshold from the default **0.5** to **0.3**. This adjustment sought to reduce False Negatives at the expense of some increase in False Positives.

- **New Metrics (Threshold 0.3)**:
  - **Recall**: Increased from **0.9861 to 0.9951** (+0.91%)
  - **Precision**: Decreased slightly from **0.9981 to 0.9687** (-2.95%)
  - **Accuracy**: Slightly reduced from **0.9985 to 0.9965** (-0.20%)
  - **F1 Score**: Decreased from **0.9921 to 0.9817** (-1.05%)

- **Confusion Matrix (Threshold 0.3)**:
  - True Positives (CKD cases correctly predicted): **4,669**
  - False Positives (non-CKD cases misclassified as CKD): **151**
  - False Negatives (CKD cases missed): **23** 
  - True Negatives (non-CKD cases correctly predicted): **45,157**

### Success and Trade-offs:
The **Recall** improved by **0.91%**, meaning the model correctly identified **99.51%** of CKD cases, significantly reducing the **False Negatives** from **65** to **23**. The trade-off was a **2.95%** reduction in **Precision**, indicating an increase in False Positives (from 9 to 151). Overall, the model maintained a high **F1 Score** of **0.9817**, balancing Precision and Recall effectively.

This adjustment aligns with the goal of prioritizing CKD detection, as it minimized the risk of missing actual CKD cases (False Negatives), which is critical in healthcare scenarios.

### Feature Importance:
An analysis of **feature importance** revealed the most influential features in predicting CKD:

1. **Obesity**: The most important feature, contributing significantly to CKD predictions.
2. **High Blood Pressure**: Another key predictor, strongly correlated with CKD.
3. **Diabetes**: A major factor in determining CKD risk.
4. **Exam Score**: The predictive value of this synthetic feature played a crucial role.
5. **Smoking**, **Liver Dx**, and **Age**: These features also had notable importance, though to a lesser extent.

The model's feature importance analysis highlights the dominance of metabolic and lifestyle-related factors (e.g., Obesity, Diabetes, High Blood Pressure) in predicting CKD.

### Conclusion:
The final model, with an adjusted threshold of **0.3**, achieved **Recall** of **99.51%** and **Precision** of **96.87%**, with an overall **Accuracy** of **99.65%**. This makes it an effective tool for predicting CKD while minimizing the risk of False Negatives, a critical requirement in medical diagnosis. The model balances a slight increase in False Positives while maintaining high performance, making it highly suitable for real-world application in healthcare scenarios.
