# ClinVar-Genetic-Variants-EDA
# ClinVar Genetic Variants – Exploratory Data Analysis

## Project Overview

This project presents an exploratory data analysis (EDA) of genetic variants from the ClinVar Conflicting Classifications dataset.

The main objective is to investigate population allele frequencies, predicted variant harmfulness, and differences between variants with and without conflicting clinical classifications.

**Research questions:**
- What are the main distributions and data quality characteristics of the dataset?
- Is there a relationship between population allele frequency and predicted harmfulness?
- Does this relationship differ between variants with and without conflicting clinical classifications?

## Dataset Description

The dataset contains **65,188 observations and 46 variables**.

**Source:** **Source:** [ClinVar Conflicting Classifications – Kaggle](https://www.kaggle.com/datasets/kevinarvai/clinvar-conflicting)

**Key variables:**
- `CLASS`: Indicates whether clinical classifications are conflicting (1) or not (0).
- `AF_EXAC`: Population allele frequency from ExAC.
- `AF_TGP`: Population allele frequency from the 1000 Genomes Project.
- `CADD_PHRED`: Predicted variant harmfulness score.
- `CLNVC`: Genetic variant type.
- `IMPACT`: Predicted impact category.
- `PolyPhen`: Predicted functional effect.

## Tools and Libraries

- Python
- Google Colab / Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Other statistical libraries used in the notebook, where applicable

## Analysis

The analysis includes:

1. Data quality assessment, including missing values, duplicates, and suspicious values.
2. Data cleaning and evaluation of its effect.
3. Descriptive statistics and visualizations of numerical and categorical variables.
4. Outlier detection using IQR, Z-score, and MAD.
5. Pearson and Spearman correlation analysis.
6. Comparison of numerical distributions and correlations between classification groups.
7. Robustness checks using outlier removal and subgroup analysis.
8. Independent calculation of mean, population variance, and standard deviation using Python loops.

## Key Findings

**1. Classification distribution**

Approximately 74.79% of variants have no conflicting clinical classifications (`CLASS = 0`), while 25.21% have conflicting classifications (`CLASS = 1`).

**2. Population frequency and predicted harmfulness**

A weak negative association was found between `AF_EXAC` and `CADD_PHRED`.

- Pearson correlation: **-0.1549**
- Spearman correlation: **-0.2322**

This suggests that rarer variants tend to have higher predicted harmfulness scores, although the association is weak.

**3. Differences between classification groups**

The relationship differs between groups:

| Group | Pearson | Spearman |
|---|---:|---:|
| CLASS = 0 | -0.1825 | -0.2652 |
| CLASS = 1 | -0.0222 | -0.0634 |

The association is more noticeable in `CLASS = 0` and almost absent in `CLASS = 1`.

**4. Robustness**

Removing 131 outliers from `CADD_PHRED` changed the Pearson correlation only from -0.1549 to -0.1555, indicating that the overall association is not primarily driven by those outliers.

## Visualizations

**AF_EXAC and CADD_PHRED correlation**

![Correlation Figure 1](figures/correlation.png%201.png)

**AF_TGP and CADD_PHRED correlation**

![Correlation Figure 2](figures/correlation.png%202.png)

## How to Run

1. Download the ClinVar Conflicting Classifications dataset from Kaggle as `archive.zip`.
2. Open `EDA_1.ipynb` in Google Colab.
3. Run the data-loading cell and select the downloaded `archive.zip` file when prompted.
4. The notebook extracts `clinvar_conflicting.csv` and loads it using Pandas.
5. Run the remaining cells in order to reproduce the analysis and visualizations.

The notebook uses standard Python data analysis libraries available in Google Colab. If any required package is missing, install it before running the analysis.

## Limitations

- Some variables, including `SIFT` and `PolyPhen`, have substantial missing data.
- The observed correlations are weak and do not imply causation.
- Predicted harmfulness scores do not replace clinical evidence.
- The dataset may not represent all genetic variants or populations equally.
- Subgroup differences require further investigation before making clinical decisions.

## Conclusion

This project demonstrates how exploratory data analysis can reveal important patterns and limitations in genetic variant data. The results highlight the importance of data quality assessment, subgroup comparisons, and robustness testing when interpreting statistical relationships.
