# Pulsar Classification for Class Prediction

## 🚀 Project Objective
The goal of this project is to build a robust classification model capable of predicting whether a space observation instance is a Pulsar (1) or not a Pulsar (0).

Pulsars are rare astronomical objects, and identifying them requires high-precision modeling to handle the significant class imbalance in the dataset.

---

## 🧩 Challenge:
High imbalance due to rare nature of Pulsar stars 

---
 
## 📊 Dataset Overview
The dataset contains 17,898 entries with features derived from the Integrated Profile and the DM-SNR Curve of the observations.

### Features:
- <b>Mean_Integrated:</b> Mean of the integrated profile.
- <b>SD:</b> Standard deviation of the integrated profile.
- <b>EK:</b> Excess kurtosis of the integrated profile.
- <b>Skewness:</b> Asymmetry of the probability distribution.
- <b>Mean_DMSNR_Curve:</b> Mean of the DM-SNR curve.
- <b>SD_DMSNR_Curve:</b> Standard deviation of the DM-SNR curve.
- <b>EK_DMSNR_Curve:</b> Excess kurtosis of the DM-SNR curve.
- <b>Skewness_DMSNR_Curve:</b> Skewness of the DM-SNR curve.
- <b>Class:</b> Target variable (0: Not Pulsar, 1: Pulsar).

<b>Note on DM-SNR Curve:</b>
Radio waves emitted from pulsars reach Earth through space filled with free electrons. Higher frequencies slow down less than lower frequencies (dispersion), creating a curve used for identification.

---

## 🛠️ Data Analysis & Preprocessing
### 1. Data Understanding
- Imbalance Handling: Class 0 has 16,259 entries while Class 1 only has 1,640.
- Correlation Insights: Features like EK and Skewness show high positive correlation with the Target Class, while Mean_Integrated shows high negative correlation.
### 2. Data Cleaning
- Missing Values: Handled using Median Imputation for features like SD, Skewness, and SD_DMSNR_Curve.
- Duplicates: Identified and removed to ensure data integrity.
### 3. Feature Engineering & Scaling
- Feature Selection: Dropped highly redundant features (Mean_Integrated, Skewness, Mean_DMSNR_Curve, EK_DMSNR_Curve) to reduce multicollinearity.
- Standardization: Applied StandardScaler to normalize feature distributions.

---

## 🤖 Model Building
I utilized a Random Forest Classifier for this task.

### Why Random Forest?
- Ensemble Power: It operates by constructing multiple decision trees and outputting the average prediction, which helps mitigate overfitting.
- Imbalance Resilience: It is highly effective at handling imbalanced datasets where one class (non-pulsars) significantly outweighs the other.

### Model Parameters:
- n_estimators: 500
- random_state: 42
- test_size: 20%

---

## 📈 Evaluation Results
The model achieved high performance across all key metrics, proving that it can identify rare Pulsars without sacrificing overall accuracy.

- MetricScoreAccuracy --> 98.35%
- Precision (Class 1) --> 92%
- Recall (Class 1) --> 90%
- F1-Score (Class 1) --> 91%

### Confusion Matrix:
- True Negatives (Non-Pulsar): 3223
- True Positives (Pulsar): 298
- False Positives: 25
- False Negatives: 34

---
  
## 💻 Tech StackLanguage: 
PythonLibraries: Pandas, NumPy, Scikit-learn, Seaborn, Matplotlib
