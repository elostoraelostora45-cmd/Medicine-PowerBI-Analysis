MEDICINE DATASET - POWER BI STARTER PACKAGE

Uploaded source CSV: medicine_dataset.csv
Actual source shape: 248,218 rows x 58 columns
Unique source IDs: 248,218
Duplicate source IDs: 0
Unique medicine names: 222,825
Repeated name rows (not automatically deleted): 25,393

DATA QUALITY:
Missing Chemical Class: 110,427 (44.5%)
Missing Action Class: 110,182 (44.4%)
Missing Therapeutic Class: 69 (0.0%)
Empty optional repeated slots are omitted from bridge tables.
Text was trimmed; no medical content was inferred or corrected.
Repeated medicine names were retained because IDs are unique and names may describe different formulations/products.

TABLES:
DimMedicine: one row per MedicineID.
DimUse + BridgeMedicineUse.
DimSideEffect + BridgeMedicineSideEffect.
DimSubstitute + BridgeMedicineSubstitute.
DimTherapeuticClass, DimChemicalClass, DimActionClass.

RELATIONSHIPS (1-to-many, single direction from dimension to bridge):
DimMedicine[MedicineID] -> BridgeMedicineUse[MedicineID]
DimUse[UseID] -> BridgeMedicineUse[UseID]
DimMedicine[MedicineID] -> BridgeMedicineSideEffect[MedicineID]
DimSideEffect[SideEffectID] -> BridgeMedicineSideEffect[SideEffectID]
DimMedicine[MedicineID] -> BridgeMedicineSubstitute[MedicineID]
DimSubstitute[SubstituteID] -> BridgeMedicineSubstitute[SubstituteID]
DimTherapeuticClass[TherapeuticClassID] -> DimMedicine[TherapeuticClassID]
DimChemicalClass[ChemicalClassID] -> DimMedicine[ChemicalClassID]
DimActionClass[ActionClassID] -> DimMedicine[ActionClassID]

DAX STARTER MEASURES:
Total Medicines = DISTINCTCOUNT(DimMedicine[MedicineID])
Habit Forming Medicines = CALCULATE([Total Medicines], DimMedicine[Habit Forming] = "Yes")
Non Habit Forming Medicines = CALCULATE([Total Medicines], DimMedicine[Habit Forming] = "No")
Medicines with Chemical Class = CALCULATE([Total Medicines], NOT ISBLANK(DimMedicine[ChemicalClassID]))
Medicines with Action Class = CALCULATE([Total Medicines], NOT ISBLANK(DimMedicine[ActionClassID]))
Listed Use Links = COUNTROWS(BridgeMedicineUse)
Listed Side Effect Links = COUNTROWS(BridgeMedicineSideEffect)
Listed Substitute Links = COUNTROWS(BridgeMedicineSubstitute)
Distinct Therapeutic Classes = DISTINCTCOUNT(DimMedicine[TherapeuticClassID])

DASHBOARD:
KPI cards: Total Medicines, Habit Forming Medicines, Non Habit Forming Medicines,
Distinct Therapeutic Classes, Listed Uses, Listed Side Effects.
Charts: medicines by Therapeutic Class; Habit Forming Yes/No; most frequent listed
side effects; most common listed uses.
Table: medicine name, therapeutic class, chemical class, action class, habit forming.
Slicers: Therapeutic Class, Chemical Class, Action Class, Habit Forming.

POWER QUERY:
Keep original CSV as staging query. Set id to Whole Number; trim/clean text;
convert empty strings to null. Unpivot substitute0..4, sideEffect0..41 and use0..4.
Filter null values after unpivot. Build dimensions and bridge tables from those results.
Do not fill missing chemical/action classes with invented categories.

SIS:
The uploaded CSV satisfies the >100,000-row threshold (248,218 rows).
The SIS brief separately requires Kaggle source and >1,000 Kaggle downloads.
This package checks the uploaded file's row count; verify the Kaggle download count on its page.
