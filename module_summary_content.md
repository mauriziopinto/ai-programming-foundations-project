# Module Summary — APA Report Content

This file contains the exact text to paste into the APA template (.docx).
Copy each section into the corresponding area of the template.

---

## Title Page Fields

- **Title:** A Reproducible Data Workflow for Exploratory Analysis of the Titanic Dataset
- **Name:** Maurizio Pinto
- **Institution:** Woolf University
- **Course:** AI Programming Foundations
- **Instructor:** [fill in from course]
- **Date:** [fill in submission date]

---

## Overview

This project implements a reproducible data workflow in Python for the Titanic - Machine Learning from Disaster dataset (Kaggle, n.d.). The workflow covers data ingestion, cleaning, exploratory analysis, and visualization, producing insights into the factors that influenced passenger survival. The complete analysis is documented in a Jupyter notebook that runs top-to-bottom without errors, supported by version control and a reproducible environment.

---

## Dataset Description

The dataset used is the Titanic training set, which contains records for 891 passengers across 12 columns, including Survived (binary outcome), Pclass (ticket class: 1, 2, or 3), Sex, Age, SibSp (number of siblings or spouses aboard), Parch (number of parents or children aboard), Fare, Cabin, and Embarked (port of embarkation: C = Cherbourg, Q = Queenstown, S = Southampton). Key variables for analysis include Survived as the outcome of interest, Pclass and Sex as the strongest categorical predictors, and Age and Fare as continuous variables. The dataset contains 177 missing Age values (19.9%), 687 missing Cabin values (77.1%), and 2 missing Embarked values (Kaggle, n.d.).

---

## Workflow Description

The workflow follows five sequential steps. First, **ingestion** loads the CSV file using Pandas and displays summary information including shape, data types, and missing value counts. Second, **cleaning** applies two modular functions: one that fills missing Age values using the median age grouped by Pclass and Sex, and another that drops the Cabin column due to excessive missingness, fills the two missing Embarked values with the mode, and removes non-analytical columns (PassengerId, Name, Ticket). Third, **exploratory analysis** runs a dedicated function that computes summary statistics, survival rate breakdowns by class, sex, and embarkation port, a correlation matrix for numeric variables, and age statistics stratified by survival. Fourth, **visualization** produces three plots: survival rate by class and sex, age distribution by survival status, and fare distribution by class. Fifth, a **summary** synthesizes key findings, limitations, and unexpected observations.

---

## Key Decisions and Assumptions

The most consequential cleaning decision was how to handle the 177 missing Age values. Rather than using a global median or mean, I imputed Age using the median grouped by Pclass and Sex. This approach preserves the correlation between these demographic variables and age: first-class passengers tend to be older, and there are age differences between male and female passengers within each class. Simple imputation methods such as mean or median substitution, while straightforward to implement, can underestimate variance and distort distributions (Dong & Peng, 2013). Grouped median imputation mitigates this concern partially by preserving within-group structure, though it still reduces variability compared to more sophisticated approaches like multiple imputation.

The Cabin column was dropped entirely because 77.1% of values were missing, making reliable imputation infeasible. While cabin location is correlated with survival (deck proximity to lifeboats), the sparsity of the data meant that retaining it would have introduced more noise than signal. The two missing Embarked values were filled with the mode (Southampton), which is appropriate given the small number of missing entries.

The three visualizations were chosen to address distinct analytical questions. Figure 1 examines the combined effect of class and sex on survival, the two strongest categorical predictors. Figure 2 investigates whether age influenced survival outcomes, particularly for children. Figure 3 explores the economic stratification reflected in fare distributions across classes.

---

## Results and Interpretation

The analysis revealed that gender was the strongest predictor of survival. Female passengers survived at much higher rates than males across all classes: approximately 97% of first-class females survived compared to roughly 37% of first-class males, and the pattern persisted in second and third class. Figure 1 illustrates this disparity clearly, showing that the interaction between class and sex produced survival rates ranging from approximately 14% (third-class males) to 97% (first-class females).

Passenger class independently influenced survival, with first-class passengers surviving at approximately 63%, second class at 47%, and third class at 24%. Figure 3 shows that fare distributions reflect this class stratification: first-class fares were substantially higher and more variable, with several outliers exceeding 200 pounds and one fare above 500 pounds.

Figure 2 shows that children (ages 0-10) had a distinct survival advantage compared to adults. The kernel density estimates for survivors and non-survivors diverge notably in the childhood range, consistent with the "women and children first" evacuation protocol. For adults aged 20 to 50, the survival and non-survival distributions are similar, suggesting that age beyond childhood had limited additional predictive power.

---

## Responsible Practice (Bias and Data Quality)

Several data quality and bias considerations are relevant to this analysis. First, the grouped median imputation for Age may mask within-group variation, potentially understating the true diversity of ages in each class-sex subgroup. If missing Age values are not missing at random (for example, if younger third-class passengers were less likely to have their age recorded), the imputed values could systematically misrepresent that subgroup (Dong & Peng, 2013).

Second, dropping the Cabin column removes deck-location information that is correlated with survival. Passengers on lower decks had less access to lifeboats, and this structural disadvantage is not captured in the cleaned dataset. Third, the training set contains only 891 of the approximately 2,200 people aboard the Titanic, introducing potential survivorship and selection bias. Results should not be generalized beyond this sample.

To reduce bias risk in future iterations, I would consider multiple imputation for Age rather than single-value imputation, flag imputed values to track their influence on downstream analysis, and retain a binary indicator for Cabin availability even when the specific cabin number is missing.

---

## Reproducibility

Reproducible workflows that document every step from data ingestion to analysis are essential for transparent and verifiable research (Rule et al., 2022). This project is fully reproducible. The Python environment is managed with uv, with all dependencies recorded in pyproject.toml and uv.lock. A requirements.txt file is also provided for compatibility with pip-based workflows. The dataset is included in the repository under the dataset/ folder. The Jupyter notebook data_workflow.ipynb runs top-to-bottom without errors after a fresh kernel restart. Version control is maintained through Git with multiple commits on a dev branch, providing a clear history of incremental progress.

---

## References

Dong, Y., & Peng, C. Y. J. (2013). Principled missing data methods for researchers. *SpringerPlus*, *2*(1), 222. https://doi.org/10.1186/2193-1801-2-222

Kaggle. (n.d.). Titanic - Machine Learning from Disaster. https://www.kaggle.com/c/titanic/data

Rule, A., Sandstrom, N., Viggiano, D., Deniz, E., Doan, A., Kwan, I., & Poldrack, R. A. (2022). Reproducible data science with Python: An open learning resource. *Journal of Open Source Education*, *5*(50), 119. https://doi.org/10.21105/jose.00119

---

# INSTRUCTIONS FOR STUDENT

1. Open `01-APA_resources/templates/apa-7-template-word-doc.docx`
2. Fill in the title page with the fields above
3. Paste each section into the body (starting on page 3) with the section headings as bold headings
4. Copy the References into the pre-formatted References section at the end
5. Review the full document for formatting
6. Export to PDF: File → Save As → PDF (or File → Download → PDF in LibreOffice)
7. Save as `module_summary.pdf` in the project folder
