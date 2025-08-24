# Advanced Data Cleaning with Fuzzy String Matching

## BrainyBeam Internship Submission

**Author**: \[Pawan Kumar Barnawal\]\
**Date**: August 24, 2025

## Project Overview
This project implements advanced data cleaning techniques, focusing on fuzzy string matching for deduplication. It processes the Titanic test dataset (`tested.csv`) from Kaggle in a Jupyter Notebook (`main.ipynb`) to handle missing values, standardize text, and identify/remove near-duplicate entries based on the `Name` column.

### Objectives
- Clean the dataset by handling missing values and standardizing text.
- Use fuzzy string matching to detect near-duplicate names (e.g., typos or formatting variations).
- Deduplicate the dataset and save the cleaned version.

### Dataset
- **Source**: [Titanic test dataset](https://www.kaggle.com/datasets/brendan45774/test-file) (`tested.csv`).
- **Description**: Contains 418 passenger records with columns like `PassengerId`, `Name`, `Age`, `Ticket`, etc.
- **Output**: Cleaned dataset saved as `data/cleaned_tested.csv`.

### Repository Structure
```
advanced-data-cleaning-with-fuzzy-string-matching/
├── data/
│   ├── tested.csv              # Input dataset (Passenger test data)
│   └── cleaned_tested.csv      # Cleaned dataset (output, optional)
├── main.ipynb               # Jupyter Notebook with the code
├── README.md                   # Project documentation
├── report/
│   └── Task_5_Report.docx       # Report file 
└── environment.yml             # Conda environment dependencies
```

### Dependencies
The project uses a Conda environment (`data_cleaning_env`) with the following dependencies:
- Python 3.9
- pandas
- numpy
- fuzzywuzzy
- python-levenshtein
- jupyter (for running the notebook)

### Setup Instructions
1. **Install Conda**: Ensure you have [Miniconda](https://docs.conda.io/en/latest/miniconda.html) or Anaconda installed.
2. **Create Environment**:
   ```bash
   conda env create -f environment.yml
   conda activate data_cleaning_env
   ```
3. **Download Dataset**: Place `tested.csv` from Kaggle in the `data/` folder.
4. **Run the Notebook**:
   ```bash
   cd src
   jupyter notebook app.ipynb
   ```
   - Open `main.ipynb` in the Jupyter interface.
   - Run all cells to process `data/tested.csv` and generate `data/cleaned_tested.csv`.
   - Output includes dataset info, missing value checks, and duplicate detection results.

### Methodology
1. **Data Cleaning**:
   - Impute missing `Age` with median, `Embarked` with mode, and `Cabin` with "Unknown".
   - Standardize `Name` column (lowercase, remove extra spaces).
2. **Fuzzy String Matching**:
   - Use `fuzzywuzzy` with `token_sort_ratio` to compare names.
   - Threshold of 90% similarity to flag potential duplicates.
3. **Deduplication**:
   - Remove duplicates (keeping first occurrence) if any are found.
   - Save cleaned dataset to `data/cleaned_tested.csv`.

### Results
- The Titanic dataset typically has no exact duplicates due to unique `PassengerId`.
- Fuzzy matching may identify near-duplicates in `Name` (e.g., "Smith, Mr. John" vs. "Smith, Mr. Jon").
- The cleaned dataset is saved with any duplicates removed.

### Notes
- Ensure `tested.csv` is in the `data/` folder before running the notebook.
- Adjust the fuzzy matching threshold (default: 90) in `app.ipynb` if needed.
- For large datasets, consider using `rapidfuzz` for faster matching.

### Contact
For questions or issues, contact at connecspawan@gmail.com.
