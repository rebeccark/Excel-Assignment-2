<img width="1872" height="837" alt="image" src="https://github.com/user-attachments/assets/baf8adab-8a39-43ac-afc5-3d7816e73b62" />
[Excel_Assignment_2_Answers.xlsx](https://github.com/user-attachments/files/32621440/Excel_Assignment_2_Answers.xlsx)
# Excel-Assignment-2
Q1 for categorical values, either replace with mode or 'unknown/NA'
For numerical values, null values upto 40% permissible
but here i used following formulas:
Price (numerical): =COUNTBLANK(...)/COUNTA(...) → 8.8% missing, checked against a 5% threshold cell → since it exceeds it, the sheet decides "impute" (using category averages, same as before)
Category (categorical): 11.8% missing → built a small COUNTIF frequency table per category, then INDEX/MATCH gives the mode ("Electronics", 13 occurrences)

Q2 Correcting Inconsistent Data
Found inconsistent casing ("laptop", "smartphone") and a typo ("Electroni" → "Electronics") in the raw data. Fixed with =PROPER(name) for casing and =IF(category="Electroni","Electronics",category) for the typo.

3) Removing Duplicates
Flagged duplicates by checking if the same 6-column combination had appeared earlier, using =COUNTIFS(range,value,...)>1 across all columns. Found 3 exact duplicates (rows 25, 29, 34) and removed them from the cleaned table.

4) Splitting and Merging Data
Split Product ID into Manufacturing Date and Country Code using =DATE(year, MATCH(month_text,{"JAN",...,"DEC"},0), VALUE(LEFT(id,2))) and =RIGHT(id,2). Merged Brand + Product Name into "Product Brand" with =Brand&" "&PROPER(Name).

5) Number Formatting
Applied the Currency format to the Price column and a custom DD-MM-YYYY format to the Manufacturing Date column using Home → Number Format 

6) Conditional Formatting
Applied a Data Bar to the Price column (Home → Conditional Formatting → Data Bars) and a custom rule highlighting cells equal to "Electronics" in the Category column (Conditional Formatting → New Rule → "Cell value = Electronics").
