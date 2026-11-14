==================================================================
Medicine Analysis with Power BI - Final Project
Smart Investment Solution (SIS) - Data Analysis Diploma
Student:    Ziad Tarek Mohamed Awadeen Abu El-Enein
Instructor: Eng. Omar Mokhtar
==================================================================

OVERVIEW
End-to-end analysis of a medicines dataset from Kaggle:
data cleaning (Power Query), data modeling, DAX, and an
interactive Power BI dashboard.

DATASET
- Source: Kaggle (medicines dataset)
- 248,218 medicines, organized into 10 tables
  (dimensions + bridge tables)

FOLDER STRUCTURE
- 01_Raw_Data/               original dataset as downloaded
- 02_Cleaned_Data/           the 10 tables after cleaning
- 03_Cleaning_Documentation/ data quality report, Power Query
                             steps and M code, validation log
- Medicine_Analysis.pbix     the Power BI report
- dashboard.png              dashboard screenshot

DATA CLEANING (Power Query)
- Converted ID columns from decimals (2.0) to whole numbers
- Removed 6 duplicated text columns from DimMedicine (names live in
  the dimension tables)
- Trimmed and cleaned text; validated Habit Forming (Yes/No only)
- Merged hidden case/space-insensitive duplicates in dimension tables:
  DimChemicalClass 872 -> 834, DimSubstitute 46,684 -> 46,672,
  DimUse 819 -> 813, and remapped foreign keys in the bridge tables
- Validation: 39/39 checks passed (see Data_Validation_Log.txt)
- Kept missing values as null (no invented categories):
  Chemical Class missing for 44.5% of medicines, Action Class for
  44.4%, Therapeutic Class for 69 medicines
- Kept repeated medicine names: IDs are unique and the same name can
  be a different product

DATA MODEL
- 10 tables, 9 one-to-many relationships (single direction,
  dimension -> fact/bridge)
- DimMedicine, DimTherapeuticClass, DimChemicalClass, DimActionClass,
  DimUse, DimSideEffect,