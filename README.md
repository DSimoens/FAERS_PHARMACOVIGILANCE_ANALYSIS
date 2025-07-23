# FAERS Disproportionality Analysis Pipeline

A **Jupyter notebook** to perform pharmacovigilance signal detection using the U.S. FDA Adverse Event Reporting System (FAERS). The pipeline calculates pharmacovigilance metrics such as ROR, PRR, RRR, and Haldane's Odds Ratio with 95% confidence intervals for a drug–event combination and exports the results to Excel.


---

## Features

Load and clean FAERS DRUG and REAC files across a selected time period.
- Normalize drug names using a provided synonym list.
- Remove duplicates according VigiMatch standards.
- Match adverse events based on a list of synonyms.
- Build contingency table for 2x2 analysis.
- Calculate:
  - **ROR** (Reporting Odds Ratio) + 95% CI
  - **PRR** (Proportional Reporting Ratio) + 95% CI
  - **RRR** (Relative Reporting Ratio) + 95% CI
  - **Haldane's Odds Ratio** + 95% CI
  - **Fisher's Exact Test p-value**
  - **Chi-square and Yates-corrected Chi-square p-values**
- Export detailed results and breakdowns to a multi-sheet Excel file.


---

## Example Use Case

```python
drug_synonyms = ['DRUGNAME', 'GENERIC DRUG NAME']
event_synonyms = ['nausea ', 'vomiting', 'gastrointestinal symptoms']

