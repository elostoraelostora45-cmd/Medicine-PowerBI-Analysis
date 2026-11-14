==================================================================
Medicine Analysis with Power BI - Final Project
Smart Investment Solution (SIS) - Data Analysis Diploma
Student:Ziad Tarek Mohamed Awadeen Abu El-Enein
Instructor: Eng. Omar Mokhtar
==================================================================

OVERVIEW
End-to-end analysis of a medicines dataset from Kaggle:
data cleaning (Power Query), data modeling, DAX, and an
interactive Power BI dashboard.

DATASET
- Source: Kaggle (medicines dataset)
- 248,218 medicines, restructured from one wide table into 10 tables
  (dimensions + bridge tables)

DATA CLEANING (Power Query)
- Converted ID columns from decimals (2.0) to whole numbers
- Removed 6 duplicated text columns (kept the IDs; names live in the
  dimension tables)
- Trimmed and cleaned text; validated Habit Forming (Yes/No only)
- Repeated columns (uses, side effects, substitutes) restructured
  into bridge tables
- Kept missing values as null (no invented categories):
  Chemical Class missing for 44.5% of medicines, Action Class for
  44.4%, Therapeutic Class for 69 medicines
- Kept repeated medicine names: IDs are unique and the same name can
  be a different product

DATA MODEL
- 10 tables, 9 one-to-many relationships (single direction,
  dimension -> fact/bridge)
- DimMedicine, DimTherapeuticClass, DimChemicalClass, DimActionClass,
  DimUse, DimSideEffect, DimSubstitute, and 3 bridge tables
  (BridgeMedicineUse, BridgeMedicineSideEffect,
  BridgeMedicineSubstitute)

DAX
Measures:
- Total Medicines
- Habit Forming Medicines
- Non Habit Forming Medicines
- Habit Forming %
- Distinct Therapeutic Classes
- Side Effect Links
Calculated columns:
- Therapeutic Class Display (shows "Unknown" for missing classes)
- Has Chemical Class (Yes/No)

DASHBOARD
- KPI cards: Total Medicines, Habit Forming, Non Habit Forming,
  Distinct Therapeutic Classes
- Bar chart: medicines by Therapeutic Class
- Donut chart: Habit Forming split
- Slicer: Therapeutic Class (interactive filtering)

KEY INSIGHTS
- 248,218 medicines across 22 therapeutic classes
- 6,003 habit-forming medicines (2.42%)
- Largest class: Anti Infectives (57,503 medicines), followed by
  Gastro Intestinal (33,630) and Pain Analgesics (32,267)

PROJECT FILES
- 01_Raw_Data
- 02_Cleaned_Data
- 03_Cleaning_Documentation
- Medicine_Analysis.pbix  (the Power BI report)
- dashboard.png           (dashboard screenshot)