# Predicting_Prolonged_Hospital_Stay_Risk
## Predicting Prolonged Hospital Stay Using Clinical Risk Stratification

## Overview
Prolonged hospital stays increase operational costs, strain bed capacity, and often reflect underlying clinical complexity.  
This project builds a clinically interpretable machine learning model to identify patients at risk of long hospital stays and translate predictions into actionable risk tiers.

The focus is not just model accuracy, but **decision usefulness** in a healthcare setting.

## Problem Statement
Hospitals need early signals to:
- Identify patients likely to experience prolonged admission
- Prioritize care coordination and discharge planning
- Allocate limited resources effectively

This project frames prolonged stay as a **binary risk problem** and evaluates trade-offs between sensitivity and false negatives.

## Data
- Patient-level clinical and administrative data
- Includes diagnoses, medications, procedures, and admission metadata
- Target variable derived from **time in hospital**

To improve decision relevance, the target was converted into a binary classification problem:
- **1**: Prolonged stay  
- **0**: Short stay

## Approach

### 1. Feature Engineering
- One-hot encoding for categorical variables
- Diagnosis grouping to reduce sparsity
- Removal of leakage-prone and non-actionable features

### 2. Baseline Model
- Logistic Regression with class weighting
- Selected for stability, transparency, and clinical interpretability

### 3. Feature Evaluation
- Coefficient-based importance analysis
- Weak and zero-impact features identified and removed
- Demographic features (race, gender) showed limited standalone impact

### 4. Interpretability Check
- A shallow decision tree was trained to validate dominant signals
- Used strictly for interpretability, not deployment

### 5. Threshold Optimization
- Multiple probability thresholds evaluated
- Focus placed on minimizing **false negatives**, given operational risk

## Risk Stratification
Instead of a single binary decision, predicted probabilities were converted into **three risk tiers**:

| Risk Tier | Interpretation |
|----------|---------------|
| Low | Low likelihood of prolonged stay |
| Medium | Moderate risk, monitor closely |
| High | High risk, early intervention recommended |

This framing aligns better with real hospital workflows than a hard classification cutoff.

## Results (High-Level)
- Logistic regression provided stable, interpretable predictions
- Risk tiers clearly separated patient groups by observed prolonged stay rates
- Trade-offs between sensitivity and false positives were explicitly documented

## Key Takeaways
- Clinical risk is driven more by **care complexity** than demographics
- Threshold choice is a business decision, not a modeling one
- Risk tiering improves actionability over raw predictions

## Tools & Technologies
- Python
- Pandas, NumPy
- Scikit-learn
- Matplotlib / Seaborn

## How This Would Be Used in Practice
- Flag high-risk patients early during admission
- Support discharge planning and care coordination teams
- Inform capacity and staffing decisions

## Next Steps
- External validation on hospital-specific data
- Cost-sensitive optimization using real operational constraints
- Integration into clinical decision support workflows
