# Problematic Internet Use Prediction

## About this repository
This repository contains the code for our machine learning project for the final. It includes 3 main versions of our model, the data, and the related documents.

### Where are the sub-versions?
As you can see, we have the main versions 1.0, 2.0, and 3.0, but what about versions 1.1, 2.1, and so on? The sub-versions are integrated directly into the main versions. Each code file contains the latest sub-version of the corresponding main version.

## 1. Indirect Prediction of SII (via PCIAT)
To estimate the Self-Identified Internet Addiction Score (SII), we first predict the component columns of the PCIAT (Problematic Internet Use scale) using machine learning models. The SII is then derived indirectly by aggregating the predicted PCIAT scores.

### Steps:
 **Data Preprocessing:**
   - Handle missing values.
   - KNN imputer
     
     ![image](https://github.com/user-attachments/assets/4c6d0937-1cde-45b7-a31f-60d23ad2d7d2)

 **Model Training:**
   - Train regression models using Random Forest to predict individual PCIAT components.
     
     ![image](https://github.com/user-attachments/assets/18c1cf37-6e46-4906-84cd-17d0b634fa43)

 **Aggregation:**
   - Combine the predicted PCIAT components to calculate the final SII.

 **Evaluation:**
   - Compare the derived SII values with the ground truth SII values.
   - Metrics used: QWK Score
     
     ![image](https://github.com/user-attachments/assets/fa91fcd4-6926-4e14-9072-cf6335dcf76a)


## 2. Direct Prediction of SII + Grid Search Optimization
In this approach, the SII is predicted directly from the input features using a single regression model.

### Improvements:
   - Predicting SII directly
   - Balanced weights
   - Stratified split for train/validation sets
      
### Steps:
 **Data Preparation:**
   - Prepare features and labels (SII).
   - Perform feature engineering (e.g., dimensionality reduction if needed).

 **Model Selection:**
   - Use models such as Random Forest

 **Hyperparameter Tuning:**
   - Apply Grid Search with cross-validation to identify the optimal model parameters.
   - Optimize the model using the Quadratic Weighted Kappa (QWK) score.
     
   - ![image](https://github.com/user-attachments/assets/9b47cc16-799f-4c44-8f62-506298e526c7)

 **Evaluation:**
   - Assess the model's performance using metrics like QWK
     
     ![image](https://github.com/user-attachments/assets/b347300b-9a87-4c50-bdfe-5f33d9c467c1)
   

## 3. XGBoost + Threshold Tuning
This approach uses XGBoost, a powerful gradient boosting algorithm, combined with threshold tuning to enhance prediction accuracy.

### Improvements:
   - Decision threshold tuning
   - Feature engineering
      
**Model Training:**
   - Train an XGBoost regressor using training data.
     
**Threshold Tuning:**
   - Fine-tune the decision thresholds to optimize the model's predictive power.
   - Use the QWK score to evaluate and adjust the thresholds.
     
     ![image](https://github.com/user-attachments/assets/46e7d3e2-9969-427d-982a-2caacb125cd6)

 **Evaluation:**
   - Assess the model's performance using metrics like QWK
     
     ![image](https://github.com/user-attachments/assets/f1bd3580-0b83-4419-bff2-3ecb3d14f98e)

## 4. Vote Regressor + Threshold Tuning
This method combines the predictions of multiple regression models through ensemble learning and tunes thresholds for better accuracy.

### Improvements:
   - Using voting regressor
   - Complementing XGBoost model with Random Forest
      
### Steps:
**Ensemble Creation:**
   - Train multiple regression models :  Random Forest + XGBoost
   - Combine their predictions using a Voting Regressor.
     
     ![image](https://github.com/user-attachments/assets/cd0e81e3-0f4d-4f5c-abb1-6db079cd3ab5)

 **Threshold Tuning:**
   - Adjust thresholds to minimize prediction errors.
   - Optimize the ensemble performance using the QWK score.

 **Evaluation:**
 
   ![image](https://github.com/user-attachments/assets/36bf6390-6566-4f59-8194-d058d7031bcb)


## 5. Final standing

![398444090-0c82e60b-fbd9-4b18-adb1-b675acfc5ed6](https://github.com/user-attachments/assets/bae62d04-4d36-46ce-a01b-a9542f3133d4)


