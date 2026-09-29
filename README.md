# Pattern Recognition for Payment Integrity

**Cotiviti Intern Assessment: Technology Solutions Analyst**
**Author:** Rhutika Patil
**Topic:** Clinical Decision Making and Pattern Recognition in Health Care (focus: anomaly detection for Payment)

## Summary

Health plans lose billions of dollars a year to improper payments. This project tests how well three detection methods can rank Medicare providers so auditors review the most suspicious ones first.

* **Data:** 558,211 Medicare style claims from 5,410 providers (Kaggle, Gupta 2019)
* **Approach:** SQL rollup of claims into provider profiles, then statistical rules, Isolation Forest (unsupervised), and Logistic Regression (supervised)
* **Result:** reviewing only the top 10% of providers, Logistic Regression caught **71%** of providers labeled potential fraud (PR AUC 0.74 vs 0.09 for random ranking)
* **Output:** a ranked review list with a plain English reason for every flagged provider

## Deliverables

| Deliverable | File |
|---|---|
| Written report (2 pages + references) | `Cotiviti_Report_Rhutika_Patil.docx` |
| Proof of concept (Jupyter notebook) | `medicare_fraud_detection.ipynb` |
| Proof of concept (view in a browser, no setup) | `medicare_fraud_detection.html` |
| Slide presentation | `Cotiviti_Presentation_Rhutika_Patil.pptx` |
| Video presentation | `Cotiviti_Video_Rhutika_Patil.mp4` |
| Resume | `Rhutika_Patil_Resume.pdf` |

## Results (held out test set, 1,082 providers, top 10% reviewed)

| Method | Labels needed | Precision | Recall | PR AUC |
|---|---|---|---|---|
| Statistical rules (z score) | No | 46% | 57% | 0.58 |
| Isolation Forest | No | 36% | 43% | 0.30 |
| **Logistic Regression** | Yes | **64%** | **71%** | **0.74** |

## Notebook structure

The notebook follows the data science lifecycle:

1. Problem definition
2. Setup and data loading
3. Data quality checks
4. Data preparation with SQL (provider profiles)
5. Exploratory data analysis
6. Statistical analysis (Mann Whitney U, z scores)
7. Feature engineering and train/test split
8. Baseline: statistical rules
9. Unsupervised model: Isolation Forest
10. Supervised model: Logistic Regression
11. Evaluation and comparison
12. Explainability
13. Results summary
14. Conclusion, limitations, and next steps

## How to run

```bash
pip install -r requirements.txt
# download the 4 Train files from Kaggle into data/ (see data/README.md)
jupyter notebook medicare_fraud_detection.ipynb
```

Then run all cells (Kernel > Restart & Run All). Runtime is about one minute on a laptop.

## Tools

Python, pandas, SQLite, scipy, scikit-learn, matplotlib, seaborn.

## Data source

Gupta, R. A. (2019). *Healthcare provider fraud detection analysis* [Data set]. Kaggle. https://www.kaggle.com/datasets/rohitrox/healthcare-provider-fraud-detection-analysis
