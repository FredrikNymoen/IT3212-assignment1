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

1. **Data Exploration (10)** — first-rows preview, summary statistics, dtypes; identify missing values,
   outliers, and unique values in categorical columns.
2. **Data Cleaning (20)** — handle missing values (mean/median/mode imputation or row/column deletion), with
   justification for the chosen method.
3. **Handling Outliers (20)** — detect via IQR or Z-score; decide to remove/cap/transform, with justification.
4. **Data Transformation (30)**
   - Encode categorical columns (label vs. one-hot), with justification for the choice per column.
   - Apply feature scaling (Min-Max or Z-score standardization); explain why scaling matters and its effect on
     downstream models.
5. **Data Splitting (10)** — 80/20 or 70/30 train/test split; explain why splitting guards against overfitting.
6. **Bonus (10)** — PCA for dimensionality reduction; discuss its effect on the dataset.

Each section expects both the implementation and a written justification of the choices made (this is a
grading criterion, not optional narration).
