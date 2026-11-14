================================================================
Medicine Analysis with Power BI - Final Project Submission
Smart Investment Solution (SIS) - Data Analysis Diploma
Student: [Your Name]
Instructor: Eng. Omar Mokhtar
================================================================

PROJECT PHASE: Data Cleaning (Phase 2 of 8)
Dataset: Medicine dataset from Kaggle (248,218 medicines / 10 tables / ~3.4M rows)

----------------------------------------------------------------
FOLDER STRUCTURE
----------------------------------------------------------------

01_Raw_Data/
    The original dataset exactly as downloaded from Kaggle.
    - 10 CSV files (DimMedicine, Dim*, Bridge* tables)
    - README_PowerBI_Setup.txt (original dataset documentation)

02_Cleaned_Data/
    The 10 tables after cleaning with Power Query techniques.
    - DimMedicine.csv         : 248,218 rows x 6 columns (6 redundant text columns removed)
    - DimChemicalClass.csv    : 872 -> 834 rows (38 case-insensitive duplicates merged)
    - DimSubstitute.csv       : 46,684 -> 46,672 rows (12 duplicates merged)
    - DimUse.csv              : 819 -> 813 rows (6 duplicates merged + 2 dirty texts fixed)
    - Bridge tables re-mapped to the new IDs (referential integrity verified: 0 orphans)

03_Cleaning_Documentation/
    - Data_Quality_Report.docx       : Full before/after quality report (Arabic)
    - PowerQuery_Cleaning_Steps.docx : Step-by-step Power Query recipe (Arabic)
    - PowerQuery_M_Code.txt          : The M code of every applied transformation
    - Data_Validation_Log.txt        : Post-cleaning integrity check results

----------------------------------------------------------------
CLEANING SUMMARY (before -> after)
----------------------------------------------------------------
Total rows:              3,418,462 -> 3,418,382 (80 redundant rows removed)
Duplicate values merged: 56 (38 ChemicalClass + 12 Substitute + 6 Use)
Columns removed:         6 redundant text columns from DimMedicine
Dirty texts fixed:       2 (DimUse: UseID=1 "Common cold", UseID=485 "Depression")
Orphan foreign keys:     0
Duplicate full rows:     0
