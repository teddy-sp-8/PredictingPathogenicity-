# Predicting Pathogenicity of Missense Variants

This project aims to predict whether missense genetic variants are benign or pathogenic using machine learning. The main focus is on single nucleotide variants (SNVs) that result in amino acid changes and how biochemical properties of these amino acids can improve prediction performance.

## Overview

Missense variants can significantly affect protein structure and function, potentially leading to disease. Using data from ClinVar, this project builds and compares several machine learning models to classify variants as benign or pathogenic.

### Key Objectives
- Clean and preprocess ClinVar data for missense SNVs
- Engineer biochemical features (charge, hydrophobicity, polarity) of amino acids
- Train and evaluate multiple machine learning models
- Analyze the impact of biochemical features on model performance

## Approach

1. **Data Processing**
   - Filtered ClinVar data to keep only missense SNVs
   - Extracted reference and alternate amino acids using regex
   - Removed duplicates and variants with unclear clinical significance

2. **Feature Engineering**
   - Added biochemical properties of amino acids (charge, hydrophobicity, polarity)
   - Calculated delta features representing the change between reference and alternate amino acids

3. **Modeling**
   - Split data into training and test sets (stratified)
   - Used `ColumnTransformer` and `OneHotEncoder` for preprocessing
   - Trained three models:
     - Logistic Regression (baseline)
     - Random Forest
     - XGBoost

4. **Evaluation**
   - Compared models using Accuracy, F1 Score, and class-specific F1 scores
   - Analyzed the contribution of biochemical features

## Results

| Model                | Accuracy | F1 Score | Pathogenic F1 |
|----------------------|----------|----------|---------------|
| Logistic Regression  | 0.57     | 0.56     | 0.47          |
| Random Forest        | 0.77     | 0.73     | 0.63          |
| **XGBoost**          | **0.80** | **0.74** | 0.61          |

**Key Finding:** Adding biochemical features of amino acids consistently improved model performance across all algorithms. XGBoost achieved the best overall results.

## Conclusion

This project demonstrates that combining traditional genomic features with biochemical properties of amino acids can improve the prediction of missense variant pathogenicity. Gradient boosting methods (especially XGBoost) performed best on this task.

## Technologies Used
- Python
- pandas, scikit-learn, XGBoost
- Jupyter Notebook

## Repository Structure
