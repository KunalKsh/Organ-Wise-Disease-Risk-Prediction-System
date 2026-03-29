# &#x20;                       CAPSTONE PROJECT-XA24007



**PROBABILISTIC RISK SCORING ENGINE**



1. **SYSTEM OVERIEW**



Raw Blood Report  + Lifestyle Data 

&#x20;             |

Data Cleaning \& Structuring

&#x20;             |

Feature Engineering (Organ Mapping)

&#x09;      |

Statistical Normalization

&#x09;      |

Context Adjustment(Age, Smoking, Drinking)

&#x20;	      |

Risk Label Generation(Synthetic)

&#x09;      |

Machine Learning Models

&#x09;      |

Probability-Based Risk Output



**2. DATA ARCHITECTURE**



1. Patient Metadata - patient\_id, age, gender, city/state, lifestyle(activity, sleep, smoking, alcohol)
2. Biomarkers - medical test, organ/system
* Hemoglobin - Blood/Bone Marrow
* Creatinine - Kidney
* SGPT - Liver
* Cholesterol - Heart



**3. DATA PREPROCESSING**

1. Cleaning- Remover header noise, Convert Categorical to Numeric
2. Handling Missing Values - SimpleImputer(strategy="mean")

Missing values break ML models.

Imputation replaces them with statistical estimates



**4. FEATURE ENGINEERING**

* Organ Grouping - \[Cardiovascular, Hepatic, Renal, Hematology, Metabolic]
* Category Score Calculation - Z-score normalization : (value-mean)/std
* Z-score : Measures how far a value deviates from normal : 0-Normal, +2 -High abnormal, -2 - Low Abnormal

Mean Absolute Deviation across Biomarkers - High Score = More Abnormal = Higher risk



**5. CONTEXT ADJUSTMENT**

Score using - Age, Smoking

Older age - Higher Risk Multiplier

Smoking - Increases Cardiovascular Risk



**6. LABEL GENERATION** 

Score > Threshold - High Risk(1)

Score <= Threshold - Low Risk(0)

Perfect labels - Perfect model - Fake performance



**7. MODELS**

1. Logistic Regression - Linear Model : Output = Probability using sigmoid function, Relationship are linear, Clean Data
2. Random Forest - Ensemble of decision tree, Uses bagging, Non-linear Data, Complex Patterns
3. Gradient Boosting - Sequential Learning, Each model corrects previous erros, Fine Optimization, Subtle Patterns



**8. PIPELINE ARCHITECTURE**

* Imputer - Scaler - Model
* Consistent Preprocessing
* Avoids Data leakage
* Reproducible results



**9. TRAIN-TEST SPLIT**

train\_test\_split()

Train - Learn Patterns

Test - Evaluate Performance



**10. EVALUATION METRICS**

* ACCURACY - Correct/Total
* F1 SCORE = Balance of Precision \& Recall
* F1 - Imbalanced data, reliability



**11. MODEL COMPARISON**

MODEL \* ORGAN \* METRICS - comparison\_df



**12. OUTPUT INTERPRETATION**

CARDIOVASCULAR - F1 \~ O.86 - Strong, Predictable system

HEPATIC - F1 \~ 0.77 - Moderate variability

RENAL - F1 \~ 0.85 - RF best - Complex Patterns

HEMATOLOGY - F1 \~ -0.57 - Noisy, difficult system

METABOLIC - F1 \~ 0.85 - Strong signal



**13. KEY INSIGHTS**

* Different organs require different models
* Biological complexity affects prediction
* Not all systems are equally predictable



**14. PATIENT-LEVEL PIPELINE**

Input - patient ID

System - Fetch Row - Compute organ scores - Apply trained model - Output probabilities



**15. FINAL OUTPUT**

* Cardiovascular - 97% - High
* Renal - 99% - High
* Hepatic - 2% - Low



**16. LIMITATIONS** 

* Synthetic Label Dependency - Score - Threshold - High/Low Risk

Model is learning patterns that were derived from same input features

Input - Score - Label - Model Learns - Predicts same logic

* Data Leakage : Labels still depends on feature, Training uses subset of features
* Over-Simplified Risk Modeling - All biomarkers-Equal Weight-Average Deviation
* Lack of Clinical Ground Truth 
* Assumption of Normal Distribution(Z-score Limitation)- Data\~Normal Distribution-Skewed, Heavy-tailed, Non-linear
* Static Thresholding - Same threshold for all patients - Misclassification Risk



**17. SCOPE OF IMPROVEMENT**

1. Replace Synthetic data with Real data with correct Labels
2. Advanced Feature Engineering - Weighted Biomarkers, Domain-based importance
3. Non-Linear Scoring Instead of Z-score - Percentile Scoring, Robust Scaling, Quantile Transformation
4. Personalized Threshold - Global Median - Age-specific, Gender-specific
5. Time-Series Modeling - Multiple reports over time - LSTM, Trend Analysis
6. Ensemble Optimization - Instead of equal voting - Weighted Ensemble, Stacking Models
7. Explainability - SHAP Values, Feature Importance



\-------------------------------------------------------------------------------------------------------------------------

### **DEFINITON \& CONCEPTS**



1. **DATA ENGINEERING LOGICS-**
* Organ Grouping - Categorizing specific biomarkers into biological systems
* Imputation Logic - Method to fill in missing data using statistical averages
* Categorical Encoding - Converting Text into numbers



**2. STATISTICAL \& MATHEMATICAL LOGICS-**

* Z-Score Normalization - Calculation of how many standard deviations an element is from the mean
* Mean Absolute Deviation (MAD) - Average distance between each data point \& the mean
* Contextual Multipliers - Adjusting a score based on external lifestyle factors



**3. MACHINE LEARNING LOGICS-**

* Logistic Regression (Sigmoid Logic) : Model that calculates the probability of a binary event(Risk VS No-Risk)
* Random Forest (Bagging Logic) : An ensemble of many Decision Trees working together
* Gradient Boosting(Sequential Logic) : An ensemble method where models are added one at a time

&#x20;

**4. EVALUATION \& PIPELINE LOGIC-**

* Train-Test Split - Spliting the data(70-30)
* F1-Score Logic - Balance between Precision \& Recall
* Pipeline Logic - Raw Data - Imputer - Scaler - Model; Prevents Data Leakage 

















