# Hypertension Prediction Using Machine Learning

A machine learning project that predicts high blood pressure risk using socioeconomic and behavioural risk factors from the Canadian Community Health Survey (CCHS) 2022. This repository demonstrates an end-to-end analytics workflow including data dictionary parsing, feature selection, recoding, exploratory analysis, model development, and prediction interpretation.

## Why This Project Matters

Hypertension is a major risk factor for cardiovascular disease and other chronic conditions. This project explores whether high blood pressure can be predicted from demographic, socioeconomic, and behavioural indicators collected through a national Canadian health survey, making the work relevant for public health screening, risk segmentation, and early intervention analysis.

## Project Overview

Completed for CST2101-010 Business Intelligence Programming by Abdul Rafay Mohammed, Ian Hurda, and Zainularab Zarabi, this project develops a machine learning pipeline for estimating hypertension risk from survey-based features. The workflow uses 63,000+ adult records from the Canadian Community Health Survey, parses 255 variables from a PDF data dictionary, engineers socioeconomic and behavioural predictors, creates analysis-ready datasets, evaluates prediction distributions, and exports a trained model for future use.

## Data Sources

The notebook uses the following files:

- **pumfCCHS.csv** — raw Canadian Community Health Survey 2022 public use microdata file.
- **CCHS2022DataDictionaryFreqs.pdf** — official data dictionary used to extract variable metadata and response labels.
- **cchsesccbsw.csv** — bootstrap survey weights file used for weighted descriptive analysis.

### Data Scope

- Raw survey respondents: **67,079**
- Variables parsed from the data dictionary: **255**
- Variables matched to dataset columns: **255 / 255**
- Staged working dataset: **67,079 rows × 19 variables**
- Final adult recoded modeling dataset: **63,318 rows × 20 columns**

## Technical Workflow

This repository demonstrates the following applied data science workflow:

1. Parsed an unstructured PDF data dictionary into structured variable and response-label reference files.
2. Validated all 255 extracted variables against the raw CCHS dataset columns.
3. Screened candidate predictors for relevance, population coverage, and data leakage risk.
4. Built analysis-ready datasets and merged survey weights for descriptive population analysis.
5. Recoded survey responses into model-friendly features and removed non-adult respondents.
6. Performed exploratory data analysis to assess integrity, class structure, and feature relationships.
7. Prepared and exported a machine learning model artifact for future use in an application or interface.

## Target Variable

The prediction target is the survey variable:

- **CCC80** → recoded as **`hypertension`**
  - `1` = Yes
  - `0` = No

Original target distribution in the notebook:

- Yes: **16,967 respondents**
- No: **49,600 respondents**
- Not stated: **512 respondents**

## Selected Predictors

Main predictors retained for modeling include:

- `agegroup`
- `sex`
- `smokingstatus`
- `alcoholfrequency`
- `bmirisk`
- `income`
- `education`
- `householdsize`
- `stresslevel`
- `region`
- `immigrantstatus`
- `foodsecurity`
- `mooddisorder`

Additional variables assessed with caution included:

- `generalhealth`
- `mentalhealth`
- `smokingduration`

These variables were reviewed carefully because they could introduce redundancy or behave too similarly to downstream health outcomes.

## Feature Engineering

The notebook demonstrates several practical preprocessing decisions:

- Restricted the analysis to adult respondents 18+.
- Recoded survey-coded responses into analysis-ready variables.
- Converted invalid and not-stated values into missing values where appropriate.
- Treated some valid skips as informative values when justified by survey logic.
- Collapsed sparse province categories into broader regional groups.
- Created reusable metadata and recoding dictionaries for transparency and reproducibility.

## Model Evaluation

This project goes beyond training a classifier by showing how predicted probabilities behave across classes.

### Prediction Distribution Analysis

The included visualizations show that respondents with hypertension generally receive higher predicted probabilities than respondents without hypertension. At the same time, the overlap between the two groups highlights that this is a realistic screening model rather than a perfect diagnostic system.

## Suggested Visual Assets for the Repository

- `image-1.jpg` — Predicted Probability by Actual Class.
- `image-2.jpg` — Probability Distribution by Class.
- `image-3.jpg` — Predicted Probability Distribution (All Splits).

These plots help communicate that the model produces meaningful risk separation and supports ranked-risk interpretation instead of only binary output. This is especially useful when demonstrating model understanding to recruiters, instructors, or project reviewers.

## Repository Outputs

Files generated throughout the notebook include:

- `variables.csv`
- `valuelabels.csv`
- `analysisdictionary.json`
- `dataset.csv`
- `wdataset.csv`
- `analysisdictionaryrecode.json`
- `recodeddataset.csv`
- `recodedwithoriginal.csv`
- `BPmodel.joblib`

These outputs show reproducible data preparation, documentation, and model packaging.

## Skills Demonstrated

This project is a strong portfolio example because it shows:

- Python data analysis and preprocessing.
- Machine learning workflow development.
- Public health survey data handling.
- Feature screening and leakage awareness.
- Parsing semi-structured reference documentation.
- Model interpretation through probability distributions.
- Reproducible dataset and artifact generation.

## Repository Structure

```text
.
├── Hypertension-Prediction.ipynb
├── README.md
├── image.jpg
├── image-2.jpg
├── image-3.jpg
├── dataset.csv
├── wdataset.csv
├── recodeddataset.csv
├── recodedwithoriginal.csv
├── analysisdictionary.json
├── analysisdictionaryrecode.json
├── variables.csv
├── valuelabels.csv
└── BPmodel.joblib
```

## How to Run

1. Open `Hypertension-Prediction.ipynb` in Jupyter Notebook or VS Code.
2. Place the required CCHS source files in the project directory.
3. Run the notebook cells in order.
4. Review the generated datasets, dictionaries, visualizations, and model output.

## Future Improvements

Potential next steps include:

- Reporting final evaluation metrics more prominently in the repository.
- Comparing additional classifiers in a summarized results table.
- Adding feature importance or interpretability analysis.
- Building a Streamlit app for interactive hypertension risk prediction.
- Evaluating subgroup performance across age, sex, and region.

## License

This project is intended for educational and portfolio demonstration purposes. Use of the original CCHS data should follow the terms and conditions associated with the dataset source.
