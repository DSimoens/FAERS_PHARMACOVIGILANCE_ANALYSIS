# FAERS Pharmacovigilance Analysis Pipeline

A **Jupyter notebook** to perform pharmacovigilance signal detection using the U.S. FDA Adverse Event Reporting System (FAERS). The pipeline calculates pharmacovigilance metrics such as ROR, PRR, RRR, and Haldane's Odds Ratio with 95% confidence intervals for a drug–event combination and exports the results to Excel.

This might contain errors, use at own risk. 

## Downloading the data files

Please download the ASCII file using this link:

[https://fis.fda.gov/extensions/FPD-QDE-FAERS/FPD-QDE-FAERS.html](https://fis.fda.gov/extensions/FPD-QDE-FAERS/FPD-QDE-FAERS.html)

These are the steps you should follow.

1. Download the ASCII ZIP archive
2. Unzip. Find the files `DRUG25Q1.txt` and `REAC25Q1.txt`
3. Create a folder called `data-source` in this repo
4. Put the aforementioned files in this folder

## Setup your runtime environment

Open a terminal pointed to the root folder of this repository.

If you have not done so make a venv using:

```bash
python -m venv ./.venv
```

Activate the vevenv and install the libraries using:

```bash
source ./.venv/bin/activate
pip install -r requirements.txt
```

Now you can either run Jupyter notebook or use vcode with the Jupyter extention.

## Features

Load and clean FAERS DRUG and REAC files across a selected time period.
- Normalize drug names using a provided synonym list.
- Normalize synonym event wher it converts all adverse event terms to uppercase and match against a user-defined synonym list (case-insensitive).
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
- Bayesian pharmacovigilance methods:
  - **Information Component (IC) with 95% credibility interval**
  - **Empirical Bayes Geometric Mean (EBGM) with 95% credibility interval**
- Export detailed results and breakdowns to a multi-sheet Excel file:
  - Summary sheet with overall metrics
  - Event Synonym Breakdown sheet with detailed counts
- Optional log of skipped or malformed input files


Optional python file: Eudravigilance_deduplication...

A basic analysis to perform on the EudraVigilance line listing file. The dataset is first deduplicated based on unique case identifiers. To ensure consistency, the line listing excel sheet needs to be cleaned before running the code by renaming coloms, removing punctuation and removing extra details from the reactions. After preprocessing, the frequency of each reported event is calculated. Minor adjustments to sheet or column names in the Excel file may be required before executing the code.


## Example of user input

In the first code cell of the nodebook you can change the parameters of the script.

For example:

```python
drug_synonyms = ['DRUGNAME', 'GENERIC DRUG NAME']
event_synonyms = ['nausea ', 'vomiting', 'gastrointestinal symptoms']
```

Run all the cells in order and you should see an Excel file appear in the repository.

# Contact

Please create an issue if you have any questions.  
Thank you.
