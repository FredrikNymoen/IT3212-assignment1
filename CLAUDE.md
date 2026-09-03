# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

IT3212 (Data-Driven Software Engineering) Assignment 1: a data preprocessing pipeline built around
`data/graduation_dataset.csv`, the UCI "Predict Students' Dropout and Academic Success" dataset (4,424 rows,
35 columns). The target column is `Target`, with three classes: `Dropout`, `Enrolled`, `Graduate`. All other
columns are numeric (demographic/socioeconomic fields, per-semester curricular unit stats, and macroeconomic
indicators for unemployment rate, inflation rate, and GDP), including several that are categorical codes
encoded as integers (e.g. `Marital status`, `Application mode`, `Course`, qualification/occupation codes).

The assignment (see the grading breakdown below) is delivered as a single Jupyter notebook that takes the raw
CSV through exploration, cleaning, outlier handling, transformation, and train/test splitting.

## Repository structure

- `notebooks/student_graduation.ipynb` — the deliverable notebook. Currently empty; this is where the full
  pipeline should be built. (Earlier commits show the project was previously split into
  `01_data_exploration.ipynb` ... `06_pca_bonus.ipynb`, one per task; these were consolidated into this single
  notebook, so keep the pipeline as one linear notebook rather than reintroducing per-task files.)
- `data/` — holds `graduation_dataset.csv`. This directory is gitignored (only `.gitkeep` is tracked), so the
  dataset must be placed here manually and any cleaned/derived CSVs written here will not be committed.
- `figures/` — intended output location for saved plots (currently only `.gitkeep`), unlike `data/` this
  directory *is* tracked by git.
- `requirements.txt` — present but currently empty; no dependencies are pinned yet.

## Environment

There is no build, lint, or test tooling configured in this repo yet, and `requirements.txt` has no entries.
Working in the notebook will require at minimum pandas, numpy, matplotlib/seaborn, and scikit-learn — add them
to `requirements.txt` as they're introduced rather than installing ad hoc.

## Assignment task breakdown

The notebook is graded against these sections (points in parentheses):

1. **Data Exploration (10)**
   a. Explore the dataset by displaying the first few rows, summary statistics, and data types of each column.
   b. Identify missing values, outliers, and unique values in categorical columns.
2. **Data Cleaning (20)**
   a. Handling Missing Values
   b. Choose appropriate methods to handle missing values (e.g., mean/median imputation for numerical data,
      mode imputation for categorical data, or deletion of rows/columns).
   c. Justify your choices for handling missing data.
3. **Handling Outliers (20)**
   a. Detect outliers using methods such as the IQR method or Z-score.
   b. Decide whether to remove, cap, or transform the outliers. Justify your decisions.
4. **Data Transformation (30)**
   a. Encoding Categorical Data
      i. Apply label encoding or one-hot encoding to transform categorical data into numerical form.
      ii. Justify your choice of encoding method.
   b. Feature Scaling
      i. Apply feature scaling techniques such as normalization (Min-Max scaling) or standardization (Z-score
         normalization) to the dataset.
      ii. Explain why feature scaling is necessary and how it impacts the model.
5. **Data Splitting (10)**
   a. Split the preprocessed dataset into training and testing sets. Typically, an 80-20 or 70-30 split is used.
   b. Explain the importance of splitting the data and how it prevents overfitting.

Each section expects both the implementation and a written justification of the choices made (this is a
grading criterion, not optional narration).
