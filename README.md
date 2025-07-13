# FAERS Disproportionality Analysis Pipeline

A **publication-grade Jupyter notebook** to perform pharmacovigilance signal detection using the U.S. FDA Adverse Event Reporting System (FAERS). The pipeline calculates **Reporting Odds Ratio (ROR)** and **Proportional Reporting Ratio (PRR)** for a drug–event combination and exports the results to Excel.

> Includes advanced **VigiMatch-style deduplication** to reduce overcounting of suspect drug entries.

---

## Features

- Load and preprocess FAERS DRUG and REAC files
- VigiMatch-style deduplication (by drug name, route, and dose)
- Drug and adverse event synonym matching
- ROR, PRR, 95% confidence intervals
- Fisher’s exact and Chi-squared tests
- Results exportable to Excel
- Publication-ready, clean structure and outputs

---

## Example Use Case

```python
drug_synonyms = ['LUXTURNA', 'VORETIGENE NEPARVOVEC']
event_synonyms = ['Retinal degeneration', 'Retinal dystrophy', 'Retinal disorder']

